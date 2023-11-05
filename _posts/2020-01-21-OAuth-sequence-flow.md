---
title: "What is OAuth and why do we need it?"
excerpt_separator: "<!--more-->"
categories:
  - OAuth
tags:
  - OAuth
---

```plantuml
@startuml
participant User
participant "Client\nApplication" as Client
participant "Authorization\nServer" as AuthServer
participant "Resource\nServer" as ResourceServer

User -> Client: Initiate Login
Client -> AuthServer: Redirect to Authorization Server
AuthServer -> User: Login & Grant Permissions
User -> AuthServer: Provide Credentials & Grant Permissions
AuthServer -> Client: Authorization Code
Client -> AuthServer: Request Access Token with Code
AuthServer -> Client: Issue Access Token
Client -> ResourceServer: Request Protected Resource with Token
ResourceServer -> AuthServer: Validate Token
AuthServer -> ResourceServer: Token is Valid
ResourceServer -> Client: Serve Resource
@enduml
