---
title: "Integrating Spring Boot with Okta via SAML"
excerpt_separator: "<!--more-->"
categories:
  - SAML
tags:
  - SAML
  - Spring
  - Okta
  - Java
---

### Integrating Spring Boot with Okta via SAML

---

**1. Setting up Okta for SAML Integration**

Before diving into the Spring Boot configuration, it's essential to prepare Okta for the integration:

1. **Create a New Application**: Log in to your Okta developer console, go to "Applications" and click "Add Application". Choose "Web" and set the sign-on method to "SAML 2.0".
2. **General Settings**: Name your app and optionally provide a logo.
3. **SAML Settings**:
   - **Single Sign On URL**: `https://your-springboot-app/saml/SSO`
   - **Audience URI (SP Entity ID)**: `https://your-springboot-app/saml/metadata`
   - Make sure to download the Okta certificate, you'll need it later.

---

**2. Setting up Spring Boot for SAML Integration**

Start by adding the necessary dependencies. You'll need the Spring Security SAML extension.

**Maven Dependencies**:

```xml
<dependency>
    <groupId>org.springframework.security.extensions</groupId>
    <artifactId>spring-security-saml2-core</artifactId>
    <version>1.0.10.RELEASE</version>
</dependency>
```

---

**3. Configuring Spring Security**

In your Spring Boot application, create a security configuration class.

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Autowired
    private SAMLUserDetailsService userDetailsService;

    @Autowired
    private SAMLAuthenticationProvider samlAuthenticationProvider;

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .apply(sso())
            .userDetailsService(userDetailsService)
            .authenticationProvider(samlAuthenticationProvider)
            .defaultSuccessURL("/home")
            .and()
            .authorizeRequests()
            .antMatchers("/saml/**").permitAll()
            .anyRequest().authenticated();
    }

    @Bean
    public SSOConfigurer sso() {
        return new SSOConfigurer();
    }
}
```

---

**4. SAML User Details Service**

Implement the `SAMLUserDetailsService` to load user details from the SAML assertion.

```java
@Service
public class SAMLUserDetailsServiceImpl implements SAMLUserDetailsService {

    @Override
    public Object loadUserBySAML(SAMLCredential credential) throws UsernameNotFoundException {
        // Extract attributes from the SAML assertion and create a user object.
        // Return your user object.
    }
}
```

---

**5. SAML Authentication Provider**

This provider will validate the authentication against Okta's SAML response.

```java
@Bean
public SAMLAuthenticationProvider samlAuthenticationProvider() {
    SAMLAuthenticationProvider provider = new SAMLAuthenticationProvider();
    provider.setUserDetails(new SAMLUserDetailsServiceImpl());
    provider.setForcePrincipalAsString(false);
    return provider;
}
```

---

**6. Loading Okta's Metadata**

To validate incoming assertions, your app needs to trust Okta. This is achieved by loading Okta's metadata containing its public key and other details.

```java
@Bean
@Qualifier("metadata")
public MetadataDisplayFilter metadataDisplayFilter() {
    return new MetadataDisplayFilter();
}

@Bean
public ExtendedMetadataDelegate oktaExtendedMetadataProvider() throws MetadataProviderException {
    HTTPMetadataProvider httpMetadata = new HTTPMetadataProvider("https://<your-okta-url>/app/<your-app-id>/sso/saml/metadata", 5000);
    httpMetadata.setParserPool(parserPool());
    ExtendedMetadataDelegate extendedMetadataDelegate = new ExtendedMetadataDelegate(httpMetadata, extendedMetadata());
    extendedMetadataDelegate.setMetadataTrustCheck(true);
    extendedMetadataDelegate.setMetadataRequireSignature(false);
    return extendedMetadataDelegate;
}
```

---

**7. Implementing SSO Endpoint**

The last piece is the Single Sign-On endpoint that will process the SAML assertion from Okta.

```java
@RestController
@RequestMapping("/saml")
public class SAMLController {

    @Autowired
    private SSOConfigurer ssoConfigurer;

    @PostMapping("/SSO")
    public ResponseEntity<?> processSSO(HttpServletRequest request, HttpServletResponse response) {
        // Handle the SSO response from Okta and authenticate the user.
    }
}
```

---

**8. Running and Testing**

Once everything is set up, run your Spring Boot application. To initiate the SSO process, direct your browser to the `/saml/login` endpoint. This will redirect you to Okta's login page. After authentication, you'll be redirected back to your application.

---

**Conclusion**

Integrating Spring Boot with Okta using SAML might seem daunting at first, but with a structured approach, it's straightforward. This guide has provided you with a step-by-step breakdown, making it easier to secure your application with this robust combination. Happy coding!
