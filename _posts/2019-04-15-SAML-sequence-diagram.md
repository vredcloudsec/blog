The SAML sequence flow

1. User initiates login: 
   User -> [Click Login] -> Service Provider

2. SP redirects to IdP:
   Service Provider -> [Redirect to IdP with SAML Request] -> User

3. User reaches IdP login:
   User -> [Navigate to IdP Login Page] -> Identity Provider

4. IdP requests credentials:
   Identity Provider -> [Prompt for Credentials] -> User

5. User supplies credentials:
   User -> [Enter Credentials] -> Identity Provider

6. IdP generates SAML Assertion:
   Identity Provider -> [Generate SAML Assertion] -> User

7. User redirected back to SP:
   User -> [Navigate back with SAML Assertion] -> Service Provider

8. Optional Validation (sometimes skipped):
   Service Provider -> [Validate SAML Assertion (optional)] -> Identity Provider

9. User gains access:
   Service Provider -> [Grant Access] -> User


![SAML Sequence Flow](/assets/images/url-encode_reduced.png)
