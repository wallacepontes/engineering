# API Security

## Videos 

### 1) Spring Security JWT: How to secure your Spring Boot REST APIs with JSON Web Tokens

Here is a summary of the video: 
[Spring Security JWT: How to secure your Spring Boot REST APIs with JSON Web Tokens](https://www.youtube.com/watch?v=KYNR5js2cXE&t=5s)

The video is about how to secure Spring Boot REST APIs with JSON Web Tokens (JWTs).

The speaker, Dan Vega, begins by creating a new Spring Boot project using Spring Initializr. He then adds the following dependencies to the project:

* Spring Web
* OAuth 2 Resource Server
* Configuration Processor

The speaker then creates a simple REST API with a single endpoint, `/home`, that returns a string. He then configures Spring Security to secure the API using JWTs.

To do this, the speaker creates a new class called `SecurityConfig`. This class extends the `WebSecurityConfigurerAdapter` class and overrides the `configure(HttpSecurity http)` method. In this method, the speaker configures Spring Security to use JWTs by adding the following filters to the HTTP security chain:

* `JwtAuthenticationTokenFilter`
* `ExceptionHandlingFilter`

The `JwtAuthenticationTokenFilter` filter is responsible for extracting the JWT token from the request and validating it. The `ExceptionHandlingFilter` filter is responsible for handling any exceptions that occur during the authentication process.

The speaker then creates a new class called `TokenService`. This class is responsible for generating JWT tokens. To do this, the class uses the `Nimbus JOSE JWT` library.

The speaker then demonstrates how to use the `TokenService` class to generate a JWT token. He then shows how to use the token to authenticate a request to the `/home` endpoint.

Finally, the speaker discusses how to test the security configuration. He does this by creating a test class that uses the `@MockUser` annotation to mock the authentication process.

The video is a great resource for anyone who wants to learn how to secure Spring Boot REST APIs with JWTs.

### 2) Securing Spring Boot Microservices with Keycloak using OpenID | OAuth2.0 | JavaTechie

Here is a summary of the video: 
[Securing Spring Boot Microservices with Keycloak using OpenID | OAuth2.0 | JavaTechie](https://www.youtube.com/watch?v=La082JsJoH4)

> 1. A simple project with two endpoints with differents roles...
[Github Spring-boot-keycloak](https://github.com/Java-Techie-jt/spring-boot-keycloak)
> 2. 2.3.6. Spring Security adapter [Securing Applications and Services Guide](https://www.keycloak.org/docs/latest/securing_apps/)
> 3. [JWT.IO](https://jwt.io/) allows you to decode, verify and generate JWT.
> 4. Download 23.0.1 Keycloack by Quarkus [here](https://www.keycloak.org/downloads)
> 4.1. or [Container image](https://www.keycloak.org/server/containers)
> 5. Extracting the the keycloak in a folder and open the command prompt and go to the bin folder to run the command:  `kc.bat start-dev` 
> 6. Go to a browser and type `localhost:8080`
> 7. Create an initial admin user like `admin`/`password` and login with that user created.
> 8. You logged in a Master Realm, choose to create a new realm, like `sprintBootKeycloak` 
> 9. Create a new Client like client Id : my_client, client name : My Client and check box (Client authentication, Authorization, Authentication flow: Standard flow, Direct acess grants, implicit flow) and SAVE
> 10. Create Realm roles like `admin` and `super_admin`
> 11. Create Users like wallace and bia, set a simple password like 123 and define a role for each one.
> 12. 



## Compare Projects

> * [Keycloak vs Gluu vs FreeIPA ](https://openhub.net/p/_compare?project_0=keycloak&project_1=Gluu&project_2=FreeIPA)

If you're looking for open-source Identity and Access Management (IAM) solutions similar to Keycloak, here are a few options:

As of my last knowledge update in January 2022, Keycloak is an open-source Identity and Access Management (IAM) solution developed by Red Hat. Keycloak is designed to provide authentication, authorization, and single sign-on (SSO) capabilities for applications and services. It's worth noting that developments may have occurred since my last update, so always check for the latest information.

0. **Keycloak:**
- **Description:** Keycloak is an open-source IAM solution that can be used for securing web applications and services. It provides features such as user authentication, authorization, social login, and centralized identity management.
- **Key Features:**
  - Single Sign-On (SSO) and identity federation.
  - Multi-factor authentication (MFA).
  - User registration and self-service.
  - OAuth 2.0 and OpenID Connect support.
  - Integration with LDAP and other user stores.
  - Role-based access control (RBAC).

**Advantages:**
- **Open Source:** Keycloak is open-source and freely available, allowing for customization and community contributions.
- **Ease of Integration:** It can be integrated with various platforms and technologies.
- **Standards-Based:** Keycloak supports widely adopted standards such as OAuth 2.0 and OpenID Connect.

**Considerations:**
- **Complexity:** Depending on your use case, the configuration and setup of Keycloak may involve a learning curve.
- **Community Support:** While Keycloak has an active community, the level of support may not be as extensive as with some commercial solutions.

Keycloak is often chosen by organizations looking for an open-source IAM solution with a focus on flexibility and standards compliance. It's commonly used in conjunction with microservices architectures, containerized applications, and cloud environments.

As always, when considering an IAM solution, evaluate it based on your specific requirements, scalability needs, and the level of support your organization may require. Additionally, check for any updates or changes that may have occurred since my last knowledge update.

### Alternatives

1. **Gluu Server:**
   - **Description:** Gluu Server is an open-source IAM platform that provides authentication, authorization, and federation capabilities. It supports standards like OAuth 2.0, OpenID Connect, and SAML.
   - **Key Features:**
     - Single Sign-On (SSO).
     - Multi-factor authentication (MFA).
     - User authentication and authorization.
     - LDAP integration.

2. **FreeIPA:**
   - **Description:** FreeIPA is an open-source identity management system designed to manage the identity, policy, and audit for Linux and Unix-based systems. It includes features such as LDAP, Kerberos, and DNS services.
   - **Key Features:**
     - Centralized identity management.
     - Kerberos-based authentication.
     - Role-based access control (RBAC).
     - Web-based administration.

3. **Shibboleth: (Inactive)**
   - **Description:** Shibboleth is an open-source IAM solution that focuses on federated identity management. It is widely used in academic and research institutions for secure single sign-on.
   - **Key Features:**
     - Federated identity and single sign-on.
     - SAML-based authentication.
     - Attribute-based access control.
     - Integration with web applications.

4. **KeyStone: (Inactive)**
   - **Description:** KeyStone is the identity service used in the OpenStack cloud computing platform. It provides a RESTful API for authentication and authorization.
   - **Key Features:**
     - Token-based authentication.
     - Role-based access control.
     - Multi-tenancy support.
     - Integration with OpenStack services.

Before selecting an open-source IAM solution, carefully assess your organization's requirements, the specific features you need, and how well each solution aligns with your technology stack. Also, consider factors such as community support, documentation, and ease of integration with your existing systems. Always check for the latest information and updates from the respective projects.

## A Spring Boot application uses Spring Security for access control. If we want to build a new microservice with fine-grained authorization requirements based on user roles and resource types. How would you design and implement a secure authorization strategy within Spring Security for this microservice? 

To design and implement a secure authorization strategy within Spring Security for a new microservice with fine-grained authorization requirements based on user roles and resource types, follow these steps:

### 1. Define Authorization Requirements

#### Identify Roles and Permissions
- **Roles:** Define the roles required for the application (e.g., ADMIN, USER, MANAGER).
- **Permissions:** Define specific permissions/actions that each role can perform (e.g., READ, WRITE, DELETE).

#### Resource Types
- Identify the types of resources that need to be secured (e.g., documents, orders, user profiles).

### 2. Set Up Spring Security

#### Add Dependencies
Ensure you have the necessary dependencies in your `pom.xml` or `build.gradle`.

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.security</groupId>
    <artifactId>spring-security-oauth2-resource-server</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.security</groupId>
    <artifactId>spring-security-oauth2-jose</artifactId>
</dependency>
```

#### Configure Security
Set up Spring Security configuration to handle authentication and authorization.

```java
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests()
                .antMatchers("/public/**").permitAll() // Public endpoints
                .antMatchers("/admin/**").hasRole("ADMIN") // Admin endpoints
                .anyRequest().authenticated()
            .and()
            .oauth2ResourceServer()
                .jwt();
    }
}
```

### 3. Use JWT for Authentication

#### JWT Configuration
Configure your application to use JWT for authentication.

```java
@Bean
public JwtDecoder jwtDecoder() {
    return JwtDecoders.fromIssuerLocation("https://your-auth-server/.well-known/jwks.json");
}

@Bean
public JwtAuthenticationConverter jwtAuthenticationConverter() {
    JwtGrantedAuthoritiesConverter grantedAuthoritiesConverter = new JwtGrantedAuthoritiesConverter();
    grantedAuthoritiesConverter.setAuthorityPrefix("ROLE_");
    grantedAuthoritiesConverter.setAuthoritiesClaimName("roles");

    JwtAuthenticationConverter jwtAuthenticationConverter = new JwtAuthenticationConverter();
    jwtAuthenticationConverter.setJwtGrantedAuthoritiesConverter(grantedAuthoritiesConverter);
    return jwtAuthenticationConverter;
}

@Override
protected void configure(HttpSecurity http) throws Exception {
    http
        .authorizeRequests()
            .anyRequest().authenticated()
        .and()
        .oauth2ResourceServer()
            .jwt()
            .jwtAuthenticationConverter(jwtAuthenticationConverter());
}
```

### 4. Implement Role-Based Access Control (RBAC)

#### Define Roles and Permissions
Map roles to specific permissions.

```java
public enum Role {
    ADMIN(Set.of(Permission.READ, Permission.WRITE, Permission.DELETE)),
    USER(Set.of(Permission.READ, Permission.WRITE));

    private final Set<Permission> permissions;

    Role(Set<Permission> permissions) {
        this.permissions = permissions;
    }

    public Set<Permission> getPermissions() {
        return permissions;
    }
}

public enum Permission {
    READ, WRITE, DELETE;
}
```

### 5. Implement Fine-Grained Authorization

#### Custom Permission Evaluator
Implement a custom permission evaluator for resource-specific permissions.

```java
@Component
public class CustomPermissionEvaluator implements PermissionEvaluator {

    @Override
    public boolean hasPermission(Authentication authentication, Object targetDomainObject, Object permission) {
        if (authentication == null || !(permission instanceof String)) {
            return false;
        }

        String targetType = targetDomainObject.getClass().getSimpleName().toUpperCase();
        String permissionString = (String) permission;

        for (GrantedAuthority authority : authentication.getAuthorities()) {
            if (authority.getAuthority().startsWith("ROLE_")) {
                String role = authority.getAuthority().substring(5);
                Set<Permission> permissions = Role.valueOf(role).getPermissions();
                if (permissions.contains(Permission.valueOf(permissionString))) {
                    return true;
                }
            }
        }
        return false;
    }

    @Override
    public boolean hasPermission(Authentication authentication, Serializable targetId, String targetType, Object permission) {
        // Optional: Implement if needed for target ID checks
        return false;
    }
}
```

#### Configure Method Security
Enable method security and configure the custom permission evaluator.

```java
@Configuration
@EnableGlobalMethodSecurity(prePostEnabled = true)
public class MethodSecurityConfig extends GlobalMethodSecurityConfiguration {

    @Override
    protected MethodSecurityExpressionHandler createExpressionHandler() {
        DefaultMethodSecurityExpressionHandler expressionHandler = new DefaultMethodSecurityExpressionHandler();
        expressionHandler.setPermissionEvaluator(new CustomPermissionEvaluator());
        return expressionHandler;
    }
}
```

#### Secure Methods with @PreAuthorize
Use `@PreAuthorize` to secure methods based on roles and permissions.

```java
@Service
public class DocumentService {

    @PreAuthorize("hasPermission(#document, 'READ')")
    public Document getDocument(Document document) {
        // Logic to get document
    }

    @PreAuthorize("hasRole('ADMIN') or hasPermission(#document, 'WRITE')")
    public void updateDocument(Document document) {
        // Logic to update document
    }

    @PreAuthorize("hasRole('ADMIN')")
    public void deleteDocument(Document document) {
        // Logic to delete document
    }
}
```

### 6. Externalize Configuration and Centralize Security

#### Externalize Configuration
Use Spring Cloud Config or a similar tool to externalize configuration properties.

```yaml
spring:
  security:
    oauth2:
      resourceserver:
        jwt:
          issuer-uri: https://your-auth-server
          jwk-set-uri: https://your-auth-server/.well-known/jwks.json
```

### 7. Monitor and Audit

#### Logging and Auditing
Implement logging and auditing to track access and changes.

```java
@Aspect
@Component
public class LoggingAspect {

    @Around("@annotation(org.springframework.security.access.prepost.PreAuthorize)")
    public Object logAccess(ProceedingJoinPoint joinPoint) throws Throwable {
        Authentication authentication = SecurityContextHolder.getContext().getAuthentication();
        String username = authentication.getName();
        String methodName = joinPoint.getSignature().getName();
        Object[] args = joinPoint.getArgs();
        // Log the access details
        return joinPoint.proceed();
    }
}
```

### Conclusion

This approach ensures a secure authorization strategy within Spring Security for your microservice. By leveraging JWT for authentication, implementing fine-grained authorization with custom permission evaluators, and using method security annotations, you can achieve a robust and flexible security model tailored to your application's needs. Externalizing configurations and implementing monitoring and auditing further enhance security and maintainability.