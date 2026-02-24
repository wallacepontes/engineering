---
bookToC: false
title: Protegendo microsserviços com OAuth2, OpenID e Spring Security
---

{{< hint warning >}}
Este documento está em construção e será evoluído com novas definições.
{{< /hint >}}

## O que é Spring Security

O Spring Security é um framework de segurança poderosa e altamente personalizável fornecida pelo ecossistema Spring para aplicativos Java. Ele foi projetado para lidar com autenticação, autorização e outras questões de segurança em aplicativos da Web e corporativos. O Spring Security permite que os desenvolvedores protejam seus aplicativos, fornecendo um conjunto de recursos de segurança abrangentes, facilitando a construção de sistemas seguros e robustos.

Os principais recursos do Spring Security incluem:

> 1. **Autenticação**: O Spring Security facilita vários mecanismos de autenticação, como nome de usuário/senha, certificados X.509, LDAP e muito mais. Ele se integra com bancos de dados de usuários existentes ou provedores de autenticação personalizados para verificar a identidade dos usuários.
> 2. **Autorização**: Depois que um usuário é autenticado, o Spring Security ajuda a definir e impor regras de controle de acesso com base nas funções e permissões do usuário. Esse controle de acesso baseado em função (RBAC) garante que os usuários possam acessar apenas recursos autorizados.
> 3. **Proteção contra vulnerabilidades comuns**: O Spring Security protege contra vulnerabilidades de segurança comuns, como cross-site scripting (XSS), cross-site request forgery (CSRF) e injeção de SQL, entre outros. Ele fornece recursos para limpar a entrada e proteger contra essas ameaças potenciais.
> 4. **Personalização**: A estrutura é altamente configurável e permite que os desenvolvedores personalizem os mecanismos de autenticação e autorização para atender aos requisitos específicos de seus aplicativos.
> 5. **Integração**: O Spring Security integra-se perfeitamente com outros projetos Spring, como Spring Framework, Spring Boot e Spring Web MVC, facilitando a inclusão de recursos de segurança em aplicativos Spring existentes.
> 6. **Suporte para aplicativos da web**: embora o Spring Security seja comumente usado para proteger aplicativos da web, ele também pode ser adaptado para proteger aplicativos não-web, como APIs e microsserviços.
> 7. **Autenticação baseada em token**: Spring Security suporta autenticação baseada em token, como JSON Web Tokens (JWT), permitindo autenticação sem estado para sistemas distribuídos.

No geral, o Spring Security é uma estrutura de segurança madura e amplamente adotada que fornece aos desenvolvedores as ferramentas e os recursos necessários para criar aplicativos seguros e confiáveis. Sua flexibilidade e facilidade de integração com outros projetos Spring o tornaram uma escolha popular para proteger aplicativos baseados em Java em vários setores.

### Principais vulnerabilidades:

O Spring Security é uma estrutura de segurança abrangente para aplicativos Java, incluindo aplicativos da Web, que aborda vários dos 10 principais riscos de segurança da OWASP. Embora possa não resolver diretamente todos esses problemas imediatamente, ele fornece ferramentas, recursos e práticas recomendadas essenciais que os desenvolvedores podem aproveitar para mitigar muitos desses riscos com eficiência.

Vamos dar uma olhada em como o Spring Security ajuda a lidar com alguns dos 10 principais riscos de segurança comuns do OWASP:

> 1. **Injeção (por exemplo, SQL Injection)**: O próprio Spring Security não impede diretamente os ataques de injeção de SQL. No entanto, ao fornecer mecanismos de autenticação e autorização, ajuda a garantir que apenas usuários autenticados e autorizados possam interagir com dados e operações confidenciais. Para evitar a injeção de SQL, os desenvolvedores precisam usar consultas parametrizadas, que o Spring Security não manipula diretamente. No entanto, o Spring Data JPA (um módulo popular do Spring para trabalhar com bancos de dados) oferece suporte a consultas parametrizadas e a combinação do Spring Security com o Spring Data JPA pode ajudar a reduzir os riscos de injeção de SQL.

> 2. **Autenticação quebrada**: O Spring Security oferece autenticação robusta e recursos de gerenciamento de sessão, ajudando os desenvolvedores a evitar vulnerabilidades de autenticação comuns. Ele oferece suporte a vários mecanismos de autenticação e incentiva as práticas recomendadas para hash de senha, gerenciamento de sessão e manipulação de dados confidenciais do usuário.

> 3. **Exposição de dados confidenciais**: Os desenvolvedores podem utilizar o Spring Security para impor HTTPS para comunicação segura entre clientes e o aplicativo. Ao garantir a transmissão de dados criptografados, os riscos de exposição de dados confidenciais são significativamente reduzidos.

> 4. **Entidades Externas XML (XXE)**: O Spring Security não lida diretamente com vulnerabilidades XXE, mas incentiva o uso de práticas de codificação seguras para evitar possíveis problemas relacionados a XML. Os desenvolvedores devem ser cautelosos ao processar a entrada XML e considerar o uso de alternativas mais seguras, como JSON, quando possível.

> 5. **Controle de acesso quebrado**: O Spring Security foi projetado para lidar com o controle de acesso de forma eficaz. Ele permite que os desenvolvedores definam regras de acesso refinadas com base nas funções e permissões do usuário, garantindo que apenas usuários autorizados possam acessar recursos específicos.

> 6. **Configuração incorreta de segurança**: O Spring Security fornece configurações padrão sensatas, tornando mais fácil para os desenvolvedores evitar configurações incorretas de segurança. No entanto, é essencial que os desenvolvedores revisem e ajustem essas configurações com base nos requisitos específicos de seus aplicativos.

> 7. **Cross-Site Scripting (XSS)**: O Spring Security não aborda diretamente as vulnerabilidades XSS. Os desenvolvedores devem validar e higienizar cuidadosamente a entrada do usuário e usar a codificação de saída apropriada para evitar ataques XSS. Embora não faça parte do próprio Spring Security, outros projetos Spring, como o Spring Web MVC, podem ajudar a lidar com a validação de entrada e a codificação de saída.

> 8. **Desserialização insegura**: O Spring Security não é responsável por lidar diretamente com a desserialização. No entanto, os aplicativos Spring devem seguir práticas de codificação segura ao lidar com a desserialização para minimizar o risco de vulnerabilidades de desserialização insegura.

> 9. **Usando componentes com vulnerabilidades conhecidas**: O Spring Security é mantido ativamente e o uso da versão mais recente ajuda a minimizar o risco de usar componentes com vulnerabilidades conhecidas. No entanto, os desenvolvedores precisam se manter informados sobre as atualizações de segurança e aplicar os patches imediatamente.

> 10. **Registro e monitoramento insuficientes**: O Spring Security não manipula diretamente o log e o monitoramento. No entanto, os desenvolvedores podem integrar o Spring Security com outras soluções de monitoramento e registro para rastrear e identificar eventos relacionados à segurança de forma eficaz.

Em resumo, embora o Spring Security não aborde todos os 10 principais riscos do OWASP por conta própria, ele fornece aos desenvolvedores ferramentas poderosas e práticas recomendadas para criar aplicativos seguros com eficiência. Os desenvolvedores devem usar o Spring Security em conjunto com práticas de codificação seguras, configuração adequada e monitoramento contínuo para criar aplicativos da Web robustos e seguros.

## OAuth 2.0 e OpenID Connect 1.0

A implementação atual do Spring Security incorpora o uso de tokens da web de acordo com as especificações OAuth 2.0 e OpenID Connect 1.0. Essa implementação aprimora significativamente os recursos de segurança do Spring Security, especialmente para proteger aplicativos da Web e APIs. Veja como o Spring Security ajuda com tokens da web:

> 1. **Suporte OAuth 2.0**: O Spring Security fornece suporte integrado para OAuth 2.0, uma estrutura de autorização amplamente adotada. Com o OAuth 2.0, os desenvolvedores podem proteger suas APIs e delegar a autenticação do usuário a provedores de identidade terceirizados (como Google, Facebook ou provedores de identidade personalizados). O Spring Security facilita a configuração de clientes OAuth 2.0 e servidores de recursos, permitindo integração perfeita com sistemas de autenticação externos.

> 2. **Suporte OpenID Connect**: OpenID Connect 1.0 é uma camada de autenticação construída sobre OAuth 2.0, fornecendo informações de identidade sobre usuários autenticados. O Spring Security integra o OpenID Connect, permitindo que os desenvolvedores obtenham informações de identidade do usuário de provedores de identidade, tornando mais fácil criar soluções de Single Sign-On (SSO) e obter atributos do usuário com segurança.

> 3. **JSON Web Tokens (JWT)**: Spring Security suporta JWT, um formato compacto e independente para transmissão de informações entre as partes. JWT é comumente usado como um token de acesso em OAuth 2.0 e OpenID Connect. O Spring Security pode lidar com autenticação, validação e gerenciamento de token baseados em JWT, fornecendo uma maneira segura e eficiente de gerenciar as sessões do usuário.

> 4. **Autenticação sem estado**: Ao usar tokens da Web como JWT, o Spring Security pode implementar autenticação sem estado. Isso significa que o servidor não precisa manter nenhum estado de sessão para usuários autenticados, pois as informações necessárias estão contidas no token. A autenticação sem estado é adequada para sistemas distribuídos e arquiteturas de microsserviços.

> 5. **Segurança baseada em token**: Com tokens da web, o Spring Security permite segurança baseada em token para aplicativos da web e APIs. Os tokens podem ser enviados em cabeçalhos HTTP, cookies ou como parâmetros de URL, oferecendo flexibilidade e personalização na forma como a autenticação é implementada.

> 6. **Controle de acesso refinado**: O Spring Security permite que os desenvolvedores imponham um controle de acesso refinado com base nas informações contidas nos tokens da web. As funções e permissões especificadas no token podem ser usadas para determinar quais recursos e terminais um usuário pode acessar.

> 7. **Personalização**: Embora o Spring Security forneça suporte robusto para tokens da Web e seu gerenciamento, os desenvolvedores ainda podem personalizar e estender a implementação para atender a casos de uso e requisitos específicos.

No geral, ao incorporar tokens da web baseados em OAuth 2.0 e OpenID Connect 1.0, o Spring Security agiliza a implementação de autenticação e autorização seguras em aplicativos da web e APIs Java. Ele permite integração perfeita com provedores de identidade externos, promove autenticação sem estado e segura e permite controle de acesso refinado, tornando-o uma excelente opção para aplicativos modernos, seguros e escaláveis.

## HTTP 401 (não autenticado) e 403 (não autorizado)

No contexto do Spring Security, a estrutura normalmente retorna os códigos de status HTTP 401 (não autenticado) e 403 (não autorizado) para indicar problemas relacionados à autenticação e autorização, respectivamente. Esses códigos de status são usados para comunicar o resultado de uma solicitação que falhou devido a direitos de acesso insuficientes ou inválidos.

> 1. **HTTP 401 não autenticado**: O código de status 401 indica que a solicitação requer autenticação e o usuário precisa fornecer credenciais válidas (por exemplo, nome de usuário e senha, chave de API etc.) Em outras palavras, o cliente deve se autenticar para obter a resposta solicitada.

> 2. **HTTP 403 não autorizado**: O código de status 403 significa que o servidor entendeu a solicitação, mas se recusa a autorizá-la. Esse status é retornado quando o servidor reconhece o usuário autenticado, mas o usuário não possui permissões suficientes para acessar o recurso solicitado.

Esses códigos de status fazem parte dos códigos de resposta HTTP padrão e são amplamente reconhecidos por clientes e desenvolvedores. Ao usar o Spring Security, você pode configurar a estrutura para lidar com falhas de autenticação e autorização e retornar automaticamente o código de status apropriado em resposta a solicitações não autorizadas ou proibidas.

Vale a pena notar que o Spring Security fornece vários mecanismos para personalizar as respostas de erro, incluindo tratamento de exceções e criação de manipuladores personalizados de acesso negado. Isso permite que os desenvolvedores definam sua lógica de tratamento de erros e retornem respostas apropriadas com base nos requisitos do aplicativo. No entanto, o uso de códigos de status HTTP padrão, como 401 e 403, fornece consistência e segue as práticas recomendadas para design de API RESTful e segurança de aplicativos da web.

Aqui está um exemplo de como você pode configurar o Spring Security para retornar códigos de status HTTP 401 e 403 para falhas de autenticação e autorização:

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests()
                .antMatchers("/public/**").permitAll() // Example: Allow public access to certain URLs
                .anyRequest().authenticated()
                .and()
            .httpBasic()
                .authenticationEntryPoint(authenticationEntryPoint())
                .and()
            .exceptionHandling()
                .accessDeniedHandler(accessDeniedHandler());
    }

    @Bean
    public AuthenticationEntryPoint authenticationEntryPoint() {
        return new HttpStatusEntryPoint(HttpStatus.UNAUTHORIZED);
    }

    @Bean
    public AccessDeniedHandler accessDeniedHandler() {
        return new HttpStatusAccessDeniedHandler(HttpStatus.FORBIDDEN);
    }

    // Other security configuration methods...

}
``` 

No trecho de código acima:

- O método `configure(HttpSecurity http)` configura as regras de segurança para diferentes URLs. Neste exemplo, as URLs `/public/**` são permitidas para acesso público, enquanto qualquer outra solicitação requer autenticação.
- O método `httpBasic()` configura a autenticação básica HTTP como o mecanismo de autenticação.
- O bean `authenticationEntryPoint()` configura o `AuthenticationEntryPoint`, que lida com falhas de autenticação. Nesse caso, ele retorna um código de status HTTP 401 (`HttpStatus.UNAUTHORIZED`).
- O bean `accessDeniedHandler()` configura o `AccessDeniedHandler`, responsável por tratar falhas de autorização. Ele retorna um código de status HTTP 403 (`HttpStatus.FORBIDDEN`).

Observe que este é um exemplo simplificado e você pode personalizar ainda mais a configuração de segurança com base em seus requisitos específicos.

Ao configurar o `AuthenticationEntryPoint` e `AccessDeniedHandler` como mostrado acima, o Spring Security retornará automaticamente os códigos de status HTTP apropriados (401 ou 403) quando a autenticação ou autorização falhar, respectivamente.

Com as versões mais recentes do Spring Security e Spring Boot, há uma nova maneira de configurar a segurança usando componentes, o que fornece uma abordagem mais modular e concisa.

Este novo estilo de configuração, conhecido como "Security DSL" (Domain-Specific Language), permite definir regras de segurança e comportamento usando métodos simples e expressões lambda. É mais direto e fácil de ler e manter do que a configuração tradicional baseada em XML ou Java.

Aqui está um exemplo de como você pode usar o Security DSL para configurar o Spring Security para retornar os códigos de status HTTP 401 e 403:

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests(authorize -> authorize
                .antMatchers("/public/**").permitAll()
                .anyRequest().authenticated()
            )
            .httpBasic(httpBasic -> httpBasic
                .authenticationEntryPoint(authenticationEntryPoint())
            )
            .exceptionHandling(exceptionHandling -> exceptionHandling
                .accessDeniedHandler(accessDeniedHandler())
            );
    }

    @Bean
    public AuthenticationEntryPoint authenticationEntryPoint() {
        return new HttpStatusEntryPoint(HttpStatus.UNAUTHORIZED);
    }

    @Bean
    public AccessDeniedHandler accessDeniedHandler() {
        return new HttpStatusAccessDeniedHandler(HttpStatus.FORBIDDEN);
    }

    // Other security configuration methods...

}
```
No código acima:

- Usamos expressões lambda para definir as regras de autorização com `authorizeRequests`. A linha `.antMatchers("/public/**").permitAll()` permite acesso a URLs que correspondem a "/public/**" sem autenticação, e a linha `.anyRequest().authenticated()` requer autenticação para qualquer outro pedido.
- Da mesma forma, usamos expressões lambda para configurar a autenticação básica HTTP e personalizar o `AuthenticationEntryPoint` e `AccessDeniedHandler`.

Ao usar o Security DSL, a configuração é mais concisa e fácil de ler, além de ajudar a evitar a necessidade de configurações detalhadas em XML ou baseadas em Java.

Lembre-se de que o Security DSL está disponível em versões específicas do Spring Security e do Spring Boot. Certifique-se de estar usando uma versão compatível com esse novo estilo de configuração. Desde minha última atualização em setembro de 2021, a configuração DSL é bem suportada em versões recentes. Sempre consulte a documentação oficial da versão que você está usando para garantir a compatibilidade e manter-se atualizado com os recursos e alterações mais recentes.

## Anotação @EnableWebSecurity do Spring Security

`@EnableWebSecurity` é uma anotação do Spring Security usada para ativar a segurança da Web para seu aplicativo. Quando você inclui esta anotação em sua classe de configuração Spring Boot ou Spring MVC, isso indica que você deseja configurar e habilitar os recursos de segurança da Web fornecidos pelo Spring Security.

Ao usar `@EnableWebSecurity`, você está essencialmente dizendo ao Spring para criar um bean `WebSecurityConfigurer` no contexto do aplicativo, que permite customizar a configuração de segurança usando configuração baseada em Java ou o Security DSL (Domain-Specific Language).

Aqui está uma visão geral do que `@EnableWebSecurity` faz:

> 1. **Ativador de configuração**: A anotação é o ponto de partida para configurar o Spring Security em seu aplicativo da web. Ele registra automaticamente os filtros e componentes Spring Security necessários para proteger seu aplicativo.

> 2. **Configuração Padrão**: Se você não fornecer nenhuma configuração específica após habilitar a segurança da web, o Spring Security aplicará algumas configurações de segurança padrão sensatas. Por exemplo, exigirá autenticação básica para todas as solicitações e fornecerá um formulário de login para autenticação.

> 3. **Personalização**: Depois de ativar a segurança da Web, você pode estender `WebSecurityConfigurerAdapter` ou usar o Security DSL para personalizar vários aspectos de segurança, como definir mecanismos de autenticação, regras de autorização, controle de acesso, lidar com cenários de exceção e muito mais.

> 4. **Várias configurações**: Em aplicativos mais complexos, você pode ter vários beans `WebSecurityConfigurer` para definir diferentes configurações de segurança para diferentes partes de seu aplicativo. Isso é obtido criando várias classes de configuração com a anotação `@Configuration`.

Aqui está um exemplo de como usar `@EnableWebSecurity` em uma classe de configuração do Spring Boot:

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        // Your security configuration goes here
    }

    // Other security-related methods or beans can be defined here
}
```
No exemplo acima, criamos uma classe `SecurityConfig` e a anotamos com `@EnableWebSecurity`, indicando que queremos habilitar o Spring Security para nosso aplicativo. O método `configure(HttpSecurity http)` pode ser substituído para personalizar as configurações de segurança usando a configuração baseada em Java ou DSL de segurança.

Lembre-se que quando você usar `@EnableWebSecurity`, o Spring Security será ativado automaticamente e começará a proteger seu aplicativo de acordo com a configuração que você fornecer. É uma etapa crucial na configuração da segurança da Web para seu aplicativo Spring.

## CSRF (Cross-Site Request Forgery)

CSRF (Cross-Site Request Forgery) é uma vulnerabilidade de segurança da Web que permite que um invasor execute ações indesejadas em nome de um usuário autenticado. Em um ataque CSRF, o invasor engana o navegador do usuário para fazer uma solicitação não intencional a um aplicativo de destino, explorando a sessão autenticada do usuário para executar ações sem seu consentimento.

Para mitigar ataques CSRF, o Spring Security inclui proteção integrada que gera e valida automaticamente tokens CSRF para aplicativos da web. Essa proteção é habilitada por padrão nas versões recentes do Spring Security.

Aqui está uma visão geral de como a proteção CSRF funciona no Spring Security:

> 1. **Geração de token CSRF**: Quando um usuário efetua login ou acessa uma página segura, o Spring Security gera um token CSRF e o armazena na sessão do usuário. Esse token é exclusivo para cada sessão e usuário.

> 2. **Inclusão de token em solicitações**: Para quaisquer solicitações de mudança de estado (por exemplo, POST, PUT, DELETE) enviadas ao servidor, o Spring Security inclui o token CSRF como um parâmetro de solicitação ou em um cabeçalho HTTP personalizado. O token é adicionado automaticamente ao formulário ou solicitações AJAX feitas pelo aplicativo.

> 3. **Validação de token**: No lado do servidor, o Spring Security intercepta as solicitações recebidas e valida o token CSRF. Se o token estiver ausente ou não corresponder ao valor esperado na sessão do usuário, a solicitação é considerada inválida e o Spring Security pode tomar as ações apropriadas, como bloquear a solicitação ou redirecionar o usuário para uma página de erro.

Para habilitar a proteção CSRF no Spring Security, você não precisa fazer nada explicitamente. A proteção CSRF é habilitada por padrão nas versões recentes do Spring Security. Enquanto você estiver usando o Spring Security em seu aplicativo da web, a proteção CSRF estará ativa e irá gerar e validar automaticamente os tokens CSRF para você.

Aqui está um exemplo de como desabilitar a proteção CSRF explicitamente na classe de configuração se você estiver usando o Security DSL:

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            // Other security configurations...
            .csrf().disable(); // Explicitly disable CSRF protection
    }

    // Other security-related methods or beans can be defined here
}
```
No exemplo acima, `http.csrf().disable()` desativa explicitamente a proteção CSRF, o que geralmente não é recomendado, a menos que você tenha um motivo específico para fazê-lo. É importante manter a proteção CSRF habilitada por padrão na maioria dos casos para garantir a segurança de seu aplicativo da web.

## Autenticação na memória para o ambiente de desenvolvimento

Autenticação in-memory é particularmente útil durante os estágios de desenvolvimento e teste.

Para configurar a autenticação na memória no Spring Security, você pode usar o método `inMemoryAuthentication()` fornecido pelo `WebSecurityConfigurerAdapter`. Isso permite que você defina as credenciais do usuário diretamente na configuração do seu aplicativo sem a necessidade de um banco de dados externo do usuário. A autenticação na memória é útil para testes, desenvolvimento ou cenários em que um banco de dados de usuário completo não é necessário.

Aqui está um exemplo de como configurar a autenticação na memória em uma classe de configuração do Spring Security:

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception {
        auth
            .inMemoryAuthentication()
                .withUser("user1").password("{noop}password1").roles("USER")
                .and()
                .withUser("user2").password("{noop}password2").roles("USER")
                .and()
                .withUser("admin").password("{noop}adminpassword").roles("ADMIN");
    }

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            // Your other security configurations go here
            .httpBasic();
    }
}
```

No exemplo acima:

> 1. Substituímos o método `configure(AuthenticationManagerBuilder auth)` para configurar o gerenciador de autenticação. Usamos `auth.inMemoryAuthentication()` para especificar que queremos usar a autenticação na memória.

> 2. Usamos o método `withUser` para definir vários usuários. Cada usuário é definido com um nome de usuário, senha e funções às quais pertencem.

> 3. `{noop}` é usado como o codificador de senha para indicar que as senhas são armazenadas em texto simples. Em aplicativos de produção, é essencial usar codificação de senha adequada, como BCrypt, para armazenar senhas com segurança. Para uso em produção, considere usar `BCryptPasswordEncoder` ou outros codificadores de senha fortes em vez de `{noop}`.

> 4. No método `configure(HttpSecurity http)`, definimos outras configurações de segurança. Neste exemplo, ativamos a autenticação HTTP Basic, que solicita aos usuários que forneçam credenciais em uma caixa de diálogo de autenticação básica ao acessar recursos protegidos.

Observe que a autenticação na memória não é adequada para uso em produção, pois as credenciais do usuário são armazenadas na configuração do aplicativo e não são persistentes. Para aplicativos de produção, é recomendável usar um banco de dados de usuário adequado e mecanismos seguros de armazenamento de senhas, como a codificação BCrypt. Além disso, considere o uso de outros provedores de autenticação, como LDAP, OAuth ou autenticação baseada em banco de dados, dependendo das necessidades de seu aplicativo.

### Não é necessário criar um bean para BCryptPasswordEncoder

Nas versões recentes do Spring Security, o `BCryptPasswordEncoder` é fornecido automaticamente como um bean pelo Spring Boot, e você não precisa criar um bean separado para ele. Quando você inclui o Spring Security como uma dependência em seu projeto Spring Boot, o `BCryptPasswordEncoder` é automaticamente registrado e disponível para uso.

Para usar o `BCryptPasswordEncoder` para codificação de senha, simplesmente inclua-o em seu método `configure(AuthenticationManagerBuilder auth)`, e o Spring Boot cuidará do resto:

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception {
        auth
            .inMemoryAuthentication()
                .withUser("user1").password(passwordEncoder().encode("password1")).roles("USER")
                .and()
                .withUser("user2").password(passwordEncoder().encode("password2")).roles("USER")
                .and()
                .withUser("admin").password(passwordEncoder().encode("adminpassword")).roles("ADMIN");
    }

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            // Your other security configurations go here
            .httpBasic();
    }

    @Bean
    public PasswordEncoder passwordEncoder() {
        return new BCryptPasswordEncoder();
    }
}
```

Neste exemplo, removemos o prefixo `{noop}` e, em vez disso, usamos o método `passwordEncoder()` para obter uma instância de `BCryptPasswordEncoder`, que automaticamente se encarrega de codificar as senhas com segurança.

Ao definir o bean `PasswordEncoder` usando a anotação `@Bean`, o Spring Boot irá automaticamente pegá-lo e usá-lo para codificação de senha em todo o seu aplicativo, incluindo a configuração `inMemoryAuthentication()`.

Usar um codificador de senha forte como `BCryptPasswordEncoder` é crucial para aplicativos de produção para garantir a segurança das senhas do usuário. Com o registro automático de bean do Spring Boot, é simples usar o codificador de senha recomendado sem a necessidade de configuração adicional.

## HTTP (GET, POST, DELETE, etc.) no Spring Security

Para configurar `antMatchers` para diferentes métodos HTTP (GET, POST, DELETE, etc.) no Spring Security, você pode usar o objeto `HttpSecurity` em sua classe `SecurityConfig`. O método `antMatchers` permite especificar os padrões de URL e métodos HTTP para os quais você deseja aplicar configurações de segurança específicas.

Aqui está um exemplo de como configurar `antMatchers` para solicitações GET, POST e DELETE:

```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Autowired
    private UserDetailsServiceImpl userDetailsService;

    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception {
        auth.userDetailsService(userDetailsService).passwordEncoder(passwordEncoder());
    }

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests()
                .antMatchers(HttpMethod.GET, "/public/**").permitAll() // Allow GET requests to /public/** without authentication
                .antMatchers(HttpMethod.POST, "/api/**").hasRole("ADMIN") // Require ADMIN role for POST requests to /api/**
                .antMatchers(HttpMethod.DELETE, "/api/**").hasRole("ADMIN") // Require ADMIN role for DELETE requests to /api/**
                .anyRequest().authenticated() // Require authentication for any other requests
            .and()
            .httpBasic(); // Use HTTP Basic authentication
    }

    @Bean
    public PasswordEncoder passwordEncoder() {
        return new BCryptPasswordEncoder();
    }
}
```

Neste exemplo:

> 1. `HttpMethod.GET`: O método `permitAll()` é usado para permitir o acesso a qualquer solicitação `GET` com URLs começando com `/public/` sem exigir autenticação.

> 2. `HttpMethod.POST`: O método `.hasRole("ADMIN")` é usado para restringir o acesso a qualquer solicitação `POST` com URLs começando com `/api/` para usuários com a função "ADMIN".

> 3. `HttpMethod.DELETE`: O método `.hasRole("ADMIN")` é usado para restringir o acesso a qualquer solicitação `DELETE` com URLs começando com `/api/` para usuários com a função "ADMIN".

> 4. `anyRequest().authenticated()`: Esta linha especifica que qualquer outra requisição que não coincida com o `antMatchers` anterior deve ser autenticada, significando que o usuário deve estar logado para acessá-la.

Observe que esses são apenas exemplos e você pode personalizar os padrões e funções de URL para corresponder aos requisitos específicos de seu aplicativo. O método `antMatchers` permite que você defina o controle de acesso refinado com base nos padrões de URL e métodos HTTP usados em seu aplicativo.

### Spring Security sem usar a classe `WebSecurityConfigurerAdapter`

A referência ("Spring Security Without the WebSecurityConfigurerAdapter") discute uma nova abordagem para configurar o Spring Security sem usar a classe `WebSecurityConfigurerAdapter` tradicional. Essa nova abordagem é possibilitada pela introdução de uma maneira mais simples e simplificada de configurar o Spring Security usando uma combinação de `UserDetailsService`, `PasswordEncoder` e expressões lambda.

Antes do Spring Security 5.6, os desenvolvedores geralmente usavam a classe `WebSecurityConfigurerAdapter` para definir configurações de segurança personalizadas. No entanto, o Spring Security 5.6 introduziu uma nova API que aproveita a programação funcional e as expressões lambda para configurar a segurança de maneira mais concisa e menos padronizada.

Na abordagem tradicional usando `WebSecurityConfigurerAdapter`, você criaria uma classe de configuração que estende `WebSecurityConfigurerAdapter` e substituiria os métodos necessários para definir autenticação, autorização e outras configurações de segurança. Com a nova abordagem, você não precisa mais estender `WebSecurityConfigurerAdapter` ou criar uma classe de configuração. Em vez disso, você pode usar o objeto `http` diretamente para configurar a segurança em um estilo funcional.

Aqui está um exemplo de como você pode configurar o Spring Security sem usar `WebSecurityConfigurerAdapter`:

```java
import org.springframework.context.annotation.Bean;
import org.springframework.security.config.Customizer;
import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.core.userdetails.User;
import org.springframework.security.core.userdetails.UserDetailsService;
import org.springframework.security.crypto.password.PasswordEncoder;
import org.springframework.security.crypto.password.NoOpPasswordEncoder;
import org.springframework.security.crypto.password.PasswordEncoderFactories;
import org.springframework.security.crypto.password.PasswordEncoder;
import org.springframework.security.crypto.factory.PasswordEncoderFactories;
import org.springframework.security.crypto.password.PasswordEncoder;
import org.springframework.security.crypto.password.DelegatingPasswordEncoder;
import org.springframework.security.crypto.password.NoOpPasswordEncoder;

public class SecurityConfig {

    @Bean
    public UserDetailsService userDetailsService() {
        var userDetailsService = new InMemoryUserDetailsManager();
        var user = User.withUsername("user")
                .password("password")
                .authorities("ROLE_USER")
                .build();
        userDetailsService.createUser(user);
        return userDetailsService;
    }

    @Bean
    public PasswordEncoder passwordEncoder() {
        return PasswordEncoderFactories.createDelegatingPasswordEncoder();
    }

    public void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests(authorizeRequests ->
                authorizeRequests
                    .anyRequest().authenticated()
            )
            .formLogin(Customizer.withDefaults());
    }
}
```
Neste exemplo:

> 1. Definimos um bean `UserDetailsService` que cria um usuário na memória com o nome de usuário "user", a senha "password" e a função "ROLE_USER".

> 2. Criamos um bean `PasswordEncoder` usando `PasswordEncoderFactory.createDelegatingPasswordEncoder()`. Este método cria um `DelegatingPasswordEncoder`, que detecta automaticamente o codificador de senha com base no prefixo da senha codificada.

> 3. Usamos o objeto `http` diretamente para configurar a segurança. Neste exemplo, estamos usando o estilo funcional para permitir que todas as solicitações sejam autenticadas e usar o login de formulário padrão.

Observe que o uso de `NoOpPasswordEncoder` (como no exemplo) não é recomendado para uso em produção. Ele é usado aqui apenas para fins de simplicidade e demonstração. Em um ambiente de produção, é essencial usar um codificador de senha seguro como o BCrypt, que é ativado por padrão no Spring Security 5.6.

A nova abordagem permite uma configuração mais limpa e concisa do Spring Security e é especialmente útil para projetos mais simples ou com requisitos de segurança diretos. No entanto, para cenários mais complexos ou configurações avançadas, você ainda pode encontrar valor em usar `WebSecurityConfigurerAdapter` ou outros recursos avançados fornecidos pelo Spring Security.

## Spring Security usando `SecurityFilterChain`

Para configurar o Spring Security usando `SecurityFilterChain` e um banco de dados, podemos usar a nova API `SecurityFilterChain` introduzida no Spring Security 5.6. Essa abordagem nos permite definir várias configurações de segurança para diferentes padrões de URL e métodos HTTP e configurar autenticação e autorização usando um banco de dados como repositório de usuários.

Vamos atualizar a configuração de segurança para usar `SecurityFilterChain` e um banco de dados para autenticação:

> 1. Crie uma nova classe `SecurityConfig`:

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.authentication.AuthenticationManager;
import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.builders.WebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
import org.springframework.security.config.annotation.web.configurers.ExpressionUrlAuthorizationConfigurer;
import org.springframework.security.core.userdetails.UserDetailsService;
import org.springframework.security.crypto.password.PasswordEncoder;
import org.springframework.security.crypto.password.PasswordEncoderFactories;

@Configuration
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Autowired
    private UserDetailsService userDetailsService;

    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception {
        auth.userDetailsService(userDetailsService).passwordEncoder(passwordEncoder());
    }

    @Override
    public void configure(WebSecurity web) throws Exception {
        // Allow static resources to be accessed without authentication
        web.ignoring().antMatchers("/css/**", "/js/**", "/images/**");
    }

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .securityMatcher(new MySecurityMatcher()) // Apply custom security matcher if needed
            .authorizeRequests(this::configureAuthorization)
            .formLogin()
            .and()
            .httpBasic();
    }

    private void configureAuthorization(ExpressionUrlAuthorizationConfigurer<HttpSecurity>.ExpressionInterceptUrlRegistry authorizeRequests) {
        // Define the security configurations for different URL patterns
        authorizeRequests
            .antMatchers("/public/**").permitAll() // Allow access to public URLs without authentication
            .antMatchers("/api/admin/**").hasRole("ADMIN") // Require ADMIN role for URLs starting with /api/admin/
            .antMatchers("/api/**").authenticated(); // Require authentication for other URLs under /api/
    }

    @Bean
    public PasswordEncoder passwordEncoder() {
        return PasswordEncoderFactories.createDelegatingPasswordEncoder();
    }

    @Override
    @Bean
    public AuthenticationManager authenticationManagerBean() throws Exception {
        return super.authenticationManagerBean();
    }
}
```

> 2. Implemente o `UserDetailsService` para buscar detalhes do usuário do banco de dados:

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.security.core.userdetails.UserDetails;
import org.springframework.security.core.userdetails.UserDetailsService;
import org.springframework.security.core.userdetails.UsernameNotFoundException;
import org.springframework.stereotype.Service;

@Service
public class UserDetailsServiceImpl implements UserDetailsService {

    private final UserRepository userRepository;

    @Autowired
    public UserDetailsServiceImpl(UserRepository userRepository) {
        this.userRepository = userRepository;
    }

    @Override
    public UserDetails loadUserByUsername(String username) throws UsernameNotFoundException {
        UserModel user = userRepository.findByUsername(username);
        if (user == null) {
            throw new UsernameNotFoundException("User not found with username: " + username);
        }
        return user;
    }
}
```

> 3. Implemente o `UserRepository` para interagir com o banco de dados:

```java
import org.springframework.data.jpa.repository.JpaRepository;

public interface UserRepository extends JpaRepository<UserModel, Long> {
    UserModel findByUsername(String username);
}
```

Nesta configuração atualizada:

- Criamos uma nova classe `SecurityConfig` que estende `WebSecurityConfigurerAdapter` para configurar o Spring Security.


### Spring Security usando `SecurityFilterChain` sem usar a classe `WebSecurityConfigurerAdapter`

Se você deseja configurar o Spring Security sem usar `WebSecurityConfigurerAdapter`, pode fazê-lo usando a nova API `SecurityFilterChain` introduzida no Spring Security 5.6. Essa abordagem permite definir várias instâncias `SecurityFilterChain`, cada uma com seu próprio conjunto de regras de segurança para diferentes padrões de URL.

Veja como você pode configurar o Spring Security sem `WebSecurityConfigurerAdapter` usando `SecurityFilterChain` e um banco de dados para autenticação:

> 1. Crie uma nova classe `SecurityConfig`:

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Bean;
import org.springframework.security.authentication.AuthenticationManager;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
import org.springframework.security.config.annotation.web.configurers.ExpressionUrlAuthorizationConfigurer;
import org.springframework.security.core.userdetails.UserDetailsService;
import org.springframework.security.crypto.password.PasswordEncoder;
import org.springframework.security.crypto.password.PasswordEncoderFactories;
import org.springframework.security.web.SecurityFilterChain;

@EnableWebSecurity
public class SecurityConfig {

    @Autowired
    private UserDetailsService userDetailsService;

    @Bean
    public PasswordEncoder passwordEncoder() {
        return PasswordEncoderFactories.createDelegatingPasswordEncoder();
    }

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        http
            .securityMatcher(new MySecurityMatcher()) // Apply custom security matcher if needed
            .authorizeRequests(this::configureAuthorization)
            .formLogin()
            .and()
            .httpBasic();

        return http.build();
    }

    private void configureAuthorization(ExpressionUrlAuthorizationConfigurer<HttpSecurity>.ExpressionInterceptUrlRegistry authorizeRequests) {
        // Define the security configurations for different URL patterns
        authorizeRequests
            .antMatchers("/public/**").permitAll() // Allow access to public URLs without authentication
            .antMatchers("/api/admin/**").hasRole("ADMIN") // Require ADMIN role for URLs starting with /api/admin/
            .antMatchers("/api/**").authenticated(); // Require authentication for other URLs under /api/
    }
}
```

> 2. Implemente o `UserDetailsService` para buscar detalhes do usuário do banco de dados, semelhante ao exemplo anterior.

> 3. Implemente o `UserRepository` para interagir com o banco de dados, semelhante ao exemplo anterior.

Nesta configuração atualizada:

- Criamos uma nova classe `SecurityConfig`, e ela não estende `WebSecurityConfigurerAdapter`.
- Usamos `@EnableWebSecurity` para ativar o Spring Security.
- O `SecurityFilterChain` é definido como um bean que configura a segurança para diferentes padrões de URL.
- Usamos `HttpSecurity` para configurar as regras de autenticação e autorização, semelhante ao exemplo anterior.

Essa abordagem permite configurar o Spring Security sem usar `WebSecurityConfigurerAdapter` e fornece mais flexibilidade na definição de várias instâncias `SecurityFilterChain` para diferentes configurações de segurança.

## 

Usar `@EnableGlobalMethodSecurity` e colocar restrições na classe do controlador é outra maneira de configurar a segurança em nível de método no Spring Security. Essa abordagem permite que você proteja métodos individuais em seus controladores com base nas funções do usuário ou em outros critérios. Ele funciona bem em conjunto com a autenticação baseada em banco de dados e a configuração `SecurityFilterChain`.

Veja como você pode configurar a segurança em nível de método usando `@EnableGlobalMethodSecurity` e restringir o acesso na classe do controlador:

> 1. Atualize a classe `SecurityConfig`:

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.authentication.AuthenticationManager;
import org.springframework.security.config.annotation.method.configuration.EnableGlobalMethodSecurity;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
import org.springframework.security.config.annotation.web.configurers.ExpressionUrlAuthorizationConfigurer;
import org.springframework.security.core.userdetails.UserDetailsService;
import org.springframework.security.crypto.password.PasswordEncoder;
import org.springframework.security.crypto.password.PasswordEncoderFactories;
import org.springframework.security.web.SecurityFilterChain;

@Configuration
@EnableWebSecurity
@EnableGlobalMethodSecurity(prePostEnabled = true) // Enable method-level security
public class SecurityConfig {

    @Autowired
    private UserDetailsService userDetailsService;

    @Bean
    public PasswordEncoder passwordEncoder() {
        return PasswordEncoderFactories.createDelegatingPasswordEncoder();
    }

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        http
            .securityMatcher(new MySecurityMatcher()) // Apply custom security matcher if needed
            .authorizeRequests(this::configureAuthorization)
            .formLogin()
            .and()
            .httpBasic();

        return http.build();
    }

    private void configureAuthorization(ExpressionUrlAuthorizationConfigurer<HttpSecurity>.ExpressionInterceptUrlRegistry authorizeRequests) {
        // Define the security configurations for different URL patterns
        authorizeRequests
            .antMatchers("/public/**").permitAll() // Allow access to public URLs without authentication
            .antMatchers("/api/admin/**").hasRole("ADMIN") // Require ADMIN role for URLs starting with /api/admin/
            .antMatchers("/api/**").authenticated(); // Require authentication for other URLs under /api/
    }
}
```

> 2. Atualize a classe do controlador:

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/api")
public class MyController {

    @Autowired
    private MyService myService;

    @GetMapping("/public/{id}")
    public MyEntity getPublicEntity(@PathVariable Long id) {
        // Method accessible to all, no method-level security restrictions
        return myService.getPublicEntityById(id);
    }

    @GetMapping("/admin/{id}")
    public MyEntity getAdminEntity(@PathVariable Long id) {
        // Method accessible to users with the ADMIN role only
        return myService.getAdminEntityById(id);
    }

    @PostMapping("/secure")
    public MyEntity createSecureEntity(@RequestBody MyEntity entity) {
        // Method accessible to authenticated users only
        return myService.createSecureEntity(entity);
    }

    @DeleteMapping("/secure/{id}")
    public void deleteSecureEntity(@PathVariable Long id) {
        // Method accessible to authenticated users only
        myService.deleteSecureEntityById(id);
    }
}
```

> 3. Atualize a classe `MyService` para conter a lógica de negócios real para os métodos do controlador.

Nesta configuração atualizada:

- Adicionamos `@EnableGlobalMethodSecurity(prePostEnabled = true)` para ativar a segurança em nível de método usando anotações como `@PreAuthorize` e `@PostAuthorize`.
- Na classe `MyController`, temos métodos protegidos usando diferentes funções (as anotações `@PreAuthorize` podem ser usadas para restrições personalizadas baseadas em funções).
- Os métodos `@PostMapping` e `@DeleteMapping` são acessíveis apenas para usuários autenticados devido ao método `configureAuthorization` na classe `SecurityConfig`.

Usar `@EnableGlobalMethodSecurity` permite que você tenha um controle mais refinado sobre a segurança em nível de método e permite aplicar restrições diretamente nos métodos do controlador. Isso pode ser especialmente útil quando você tem diferentes regras de acesso para métodos individuais dentro do mesmo controlador.

### Permissões no Spring Security 

Adicionar permissões juntamente com funções no Spring Security permite que você defina um controle de acesso mais refinado para recursos ou ações individuais em seu aplicativo. Embora as funções forneçam direitos de acesso de alto nível (por exemplo, "ADMIN", "USER"), as permissões podem representar ações ou operações específicas que os usuários podem executar (por exemplo, "READ", "WRITE", "DELETE") em recursos específicos.

Configure a segurança em nível de método com permissões:

Agora que você definiu permissões para funções e usuários, você pode usá-los para configurar a segurança em nível de método usando as anotações `@PreAuthorize` e `@PostAuthorize` em seus controladores ou métodos de serviço.

```java
import org.springframework.security.access.prepost.PostAuthorize;
import org.springframework.security.access.prepost.PreAuthorize;

@RestController
@RequestMapping("/api")
public class MyController {

    @PreAuthorize("hasRole('ADMIN') or hasPermission('READ')")
    @GetMapping("/secure/{id}")
    public MyEntity getSecureEntity(@PathVariable Long id) {
        // Method accessible to users with the ADMIN role or READ permission
        return myService.getSecureEntityById(id);
    }

    @PreAuthorize("hasRole('ADMIN') or hasPermission('WRITE')")
    @PostMapping("/secure")
    public MyEntity createSecureEntity(@RequestBody MyEntity entity) {
        // Method accessible to users with the ADMIN role or WRITE permission
        return myService.createSecureEntity(entity);
    }

    @PreAuthorize("hasRole('ADMIN') or hasPermission('DELETE')")
    @DeleteMapping("/secure/{id}")
    public void deleteSecureEntity(@PathVariable Long id) {
        // Method accessible to users with the ADMIN role or DELETE permission
        myService.deleteSecureEntityById(id);
    }

    @PostAuthorize("hasRole('ADMIN') or hasPermission('READ', returnObject)")
    @GetMapping("/secure/{id}")
    public MyEntity getSecureEntity(@PathVariable Long id) {
        // Method accessible to users with the ADMIN role or READ permission
        return myService.getSecureEntityById(id);
    }
}
```

Neste exemplo:

- Adicionamos o campo `permissions` nas entidades `Role` e `User` para representar as permissões associadas.
- Usamos as anotações `@PreAuthorize` e `@PostAuthorize` para proteger os métodos com base em funções e permissões.

Ao introduzir o modelo de permissões, agora você pode definir um controle de acesso mais granular e adaptar a segurança do aplicativo com base em ações ou recursos individuais. Observe que as regras de segurança específicas e o uso de `@PreAuthorize` e `@PostAuthorize` podem variar dependendo dos requisitos do seu aplicativo.


## Configurando o projeto

A configuração do Spring Security no arquivo pom.xml para Maven pode ser feita da seguinte forma:

```xml
<dependencies>
    <!-- Other dependencies... -->

    <!-- Spring Security -->
    <dependency>
        <groupId>org.springframework.security</groupId>
        <artifactId>spring-security-web</artifactId>
        <version><!-- Replace with the desired Spring Security version --></version>
    </dependency>
    <dependency>
        <groupId>org.springframework.security</groupId>
        <artifactId>spring-security-config</artifactId>
        <version><!-- Replace with the desired Spring Security version --></version>
    </dependency>
    <!-- You may also need to include spring-security-core if it's not pulled transitively -->
    
    <!-- Other dependencies... -->
</dependencies>
```

```xml
<dependencies>
    <!-- Other dependencies... -->

    <!-- Spring Boot Starter Security -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-security</artifactId>
        <version><!-- Replace with the desired Spring Boot version --></version>
    </dependency>
    
    <!-- Other dependencies... -->
</dependencies>
```

Para atualizar a configuração para usar OAuth2 e OpenID Connect 1.0 com tokens, você pode integrar o Spring Secu

Aqui estão as etapas gerais para atualizar a configuração:

1. Adicione as dependências OAuth2 e OpenID Connect:

Certifique-se de ter as dependências necessárias em seu arquivo `pom.xml` para suportar OAuth2 e OpenID Connect:

```xml
<!-- Spring Security OAuth2 and OpenID Connect dependencies -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-oauth2-client</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.security</groupId>
    <artifactId>spring-security-oauth2-jose</artifactId>
</dependency>
```

2. Configure os provedores OAuth2 e OpenID Connect:

No arquivo `application.properties` ou `application.yml`, forneça a configuração para seus provedores OAuth2 e OpenID Connect:

```properties
# OAuth2 and OpenID Connect configuration
spring.security.oauth2.client.registration.<client-id>.client-id=<client-id>
spring.security.oauth2.client.registration.<client-id>.client-secret=<client-secret>
spring.security.oauth2.client.registration.<client-id>.scope=<scopes>
spring.security.oauth2.client.provider.<provider-name>.issuer-uri=<issuer-uri>
spring.security.oauth2.client.provider.<provider-name>.authorization-uri=<authorization-uri>
spring.security.oauth2.client.provider.<provider-name>.token-uri=<token-uri>
spring.security.oauth2.client.provider.<provider-name>.user-info-uri=<user-info-uri>
spring.security.oauth2.client.provider.<provider-name>.jwk-set-uri=<jwk-set-uri>
```

Substitua `<client-id>`, `<client-secret>`, `<scopes>`, `<provider-name>` e os espaços reservados de URI pelos valores reais de seu provedor OAuth2 e OpenID Connect.

# Proposta de Uso

1. Configure a classe `SecurityConfig`:

Atualize a classe `SecurityConfig` para usar OAuth2 e OpenID Connect para autenticação:

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.authentication.AuthenticationManager;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
import org.springframework.security.config.annotation.web.configurers.ExpressionUrlAuthorizationConfigurer;
import org.springframework.security.core.userdetails.UserDetailsService;
import org.springframework.security.crypto.password.PasswordEncoder;
import org.springframework.security.crypto.password.PasswordEncoderFactories;
import org.springframework.security.web.SecurityFilterChain;

@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Autowired
    private UserDetailsService userDetailsService;

    @Bean
    public PasswordEncoder passwordEncoder() {
        return PasswordEncoderFactories.createDelegatingPasswordEncoder();
    }

    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception {
        auth.userDetailsService(userDetailsService).passwordEncoder(passwordEncoder());
    }

    @Bean
    @Override
    public AuthenticationManager authenticationManagerBean() throws Exception {
        return super.authenticationManagerBean();
    }

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .securityMatcher(new MySecurityMatcher()) // Apply custom security matcher if needed
            .authorizeRequests(this::configureAuthorization)
            .oauth2Login() // Enable OAuth2 login support
                .userInfoEndpoint()
                    .userService(customOAuth2UserService()); // Configure custom user service for OAuth2
    }

    private void configureAuthorization(ExpressionUrlAuthorizationConfigurer<HttpSecurity>.ExpressionInterceptUrlRegistry authorizeRequests) {
        // Define the security configurations for different URL patterns
        authorizeRequests
            .antMatchers("/public/**").permitAll() // Allow access to public URLs without authentication
            .antMatchers("/api/admin/**").hasRole("ADMIN") // Require ADMIN role for URLs starting with /api/admin/
            .antMatchers("/api/**").authenticated(); // Require authentication for other URLs under /api/
    }

    // Define a custom OAuth2 user service to handle user details fetched from OAuth2 provider
    @Bean
    public OAuth2UserService<OAuth2UserRequest, OAuth2User> customOAuth2UserService() {
        return new CustomOAuth2UserService();
    }
}
```

2. Implemente o `OAuth2UserService`:

Crie um `OAuth2UserService` personalizado para lidar com os detalhes do usuário obtidos do provedor OAuth2. Isso mapeará os detalhes do usuário obtidos do provedor para o modelo de usuário do seu aplicativo.

```java
import org.springframework.security.core.Authentication;
import org.springframework.security.core.GrantedAuthority;
import org.springframework.security.oauth2.core.OAuth2AccessToken;
import org.springframework.security.oauth2.core.OAuth2RefreshToken;
import org.springframework.security.oauth2.core.user.OAuth2User;
import org.springframework.security.oauth2.core.user.OAuth2UserAuthority;

import java.util.Collection;
import java.util.Map;

public class CustomOAuth2User implements OAuth2User {
    private final OAuth2User delegate;
    private final UserModel userModel;

    public CustomOAuth2User(OAuth2User delegate, UserModel userModel) {
        this.delegate = delegate;
        this.userModel = userModel;
    }

    @Override
    public Map<String, Object> getAttributes() {
        return delegate.getAttributes();
    }

    @Override
    public Collection<? extends GrantedAuthority> getAuthorities() {
        // Merge the OAuth2User's authorities with the UserModel's roles and permissions
        Collection<? extends GrantedAuthority> authorities = delegate.getAuthorities();
        authorities.addAll(userModel.getRoles()); // Assuming UserModel has getRoles() method representing roles as authorities
        authorities.addAll(userModel.getPermissions()); // Assuming UserModel has getPermissions() method representing permissions as authorities
        return authorities;
    }

    @Override
    public String getName() {
        return delegate.getName();
    }

    // Implement other methods as needed
}
```

Se você deseja configurar o Spring Security sem usar `WebSecurityConfigurerAdapter`, você pode seguir os passos anteriores e fazer alguns ajustes na classe `SecurityConfig`. Veja como você pode fazer isso:

1. Atualize a classe `SecurityConfig`:

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.authentication.AuthenticationManager;
import org.springframework.security.config.annotation.method.configuration.EnableGlobalMethodSecurity;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
import org.springframework.security.config.annotation.web.configurers.ExpressionUrlAuthorizationConfigurer;
import org.springframework.security.core.userdetails.UserDetailsService;
import org.springframework.security.crypto.password.PasswordEncoder;
import org.springframework.security.crypto.password.PasswordEncoderFactories;
import org.springframework.security.oauth2.client.OAuth2AuthorizedClientService;
import org.springframework.security.oauth2.client.registration.ClientRegistrationRepository;
import org.springframework.security.oauth2.client.web.OAuth2AuthorizationRequestResolver;
import org.springframework.security.oauth2.client.web.OAuth2AuthorizedClientRepository;
import org.springframework.security.oauth2.client.web.OAuth2AuthorizedClientRepositoryFactory;
import org.springframework.security.oauth2.client.web.OAuth2AuthorizedClientRepositoryFactoryBean;
import org.springframework.security.oauth2.client.web.OAuth2AuthorizedClientServiceOAuth2AuthorizedClientManager;
import org.springframework.security.oauth2.client.web.OAuth2AuthorizedClientServiceOAuth2AuthorizedClientRepositoryAdapter;
import org.springframework.security.oauth2.client.web.OAuth2AuthorizedClientServiceOAuth2AuthorizedClientRepositoryFactory;
import org.springframework.security.oauth2.client.web.OAuth2LoginAuthenticationFilter;
import org.springframework.security.oauth2.client.web.OAuth2LoginAuthenticationProvider;
import org.springframework.security.oauth2.client.web.OAuth2LoginAuthenticationToken;
import org.springframework.security.oauth2.client.web.OAuth2LoginConfigurer;
import org.springframework.security.oauth2.client.web.OAuth2LoginConfigurer.OAuth2LoginAuthenticationFilterConfigurer;
import org.springframework.security.oauth2.client.web.OAuth2LoginConfigurer.OAuth2LoginAuthenticationProviderConfigurer;
import org.springframework.security.oauth2.core.endpoint.OAuth2AuthorizationRequest;
import org.springframework.security.web.SecurityFilterChain;

@Configuration
@EnableWebSecurity
@EnableGlobalMethodSecurity(prePostEnabled = true) // Enable method-level security
public class SecurityConfig {

    @Autowired
    private UserDetailsService userDetailsService;

    @Bean
    public PasswordEncoder passwordEncoder() {
        return PasswordEncoderFactories.createDelegatingPasswordEncoder();
    }

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http,
                                                  OAuth2AuthorizedClientService authorizedClientService,
                                                  OAuth2AuthorizedClientRepository authorizedClientRepository) throws Exception {
        http
            .securityMatcher(new MySecurityMatcher()) // Apply custom security matcher if needed
            .authorizeRequests(this::configureAuthorization)
            .oauth2Login() // Enable OAuth2 login support
                .userInfoEndpoint()
                    .userService(customOAuth2UserService(authorizedClientService, authorizedClientRepository)); // Configure custom user service for OAuth2

        return http.build();
    }

    private void configureAuthorization(ExpressionUrlAuthorizationConfigurer<HttpSecurity>.ExpressionInterceptUrlRegistry authorizeRequests) {
        // Define the security configurations for different URL patterns
        authorizeRequests
            .antMatchers("/public/**").permitAll() // Allow access to public URLs without authentication
            .antMatchers("/api/admin/**").hasRole("ADMIN") // Require ADMIN role for URLs starting with /api/admin/
            .antMatchers("/api/**").authenticated(); // Require authentication for other URLs under /api/
    }

    // Define a custom OAuth2 user service to handle user details fetched from OAuth2 provider
    @Bean
    public OAuth2UserService<OAuth2UserRequest, OAuth2User> customOAuth2UserService(OAuth2AuthorizedClientService authorizedClientService,
                                                                                   OAuth2AuthorizedClientRepository authorizedClientRepository) {
        return new CustomOAuth2UserService(authorizedClientService, authorizedClientRepository);
    }
}
```
2. Implemente o `CustomOAuth2UserService`:

Crie um `OAuth2UserService` personalizado para lidar com os detalhes do usuário obtidos do provedor OAuth2. Isso mapeará os detalhes do usuário obtidos do provedor para o modelo de usuário do seu aplicativo e armazenará o cliente autorizado OAuth2 no `OAuth2AuthorizedClientRepository`.

```java
import org.springframework.security.core.Authentication;
import org.springframework.security.oauth2.client.OAuth2AuthorizedClient;
import org.springframework.security.oauth2.client.OAuth2AuthorizedClientService;
import org.springframework.security.oauth2.client.registration.ClientRegistration;
import org.springframework.security.oauth2.client.web.OAuth2AuthorizedClientRepository;
import org.springframework.security.oauth2.client.web.OAuth2AuthorizedClientRepositoryAdapter;
import org.springframework.security.oauth2.client.web.OAuth2AuthorizedClientRepositoryFactory;
import org.springframework.security.oauth2.client.web.OAuth2AuthorizedClientServiceOAuth2AuthorizedClientRepositoryAdapter;
import org.springframework.security.oauth2.client.web.OAuth2AuthorizedClientServiceOAuth2AuthorizedClientRepositoryFactory;
import org.springframework.security.oauth2.client.web.OAuth2LoginAuthenticationToken;
import org.springframework.security.oauth2.core.user.OAuth2User;
import org.springframework.security.oauth2.core.user.OAuth2UserAuthority;

import java.util.Collection;
import java.util.Map;

public class CustomOAuth2UserService implements OAuth2UserService<OAuth2UserRequest, OAuth2User> {

    private final OAuth2AuthorizedClientService authorizedClientService;
    private final OAuth2AuthorizedClientRepository authorizedClientRepository;

    public CustomOAuth2UserService(OAuth2AuthorizedClientService authorizedClientService,
                                   OAuth2AuthorizedClientRepository authorizedClientRepository) {
        this.authorizedClientService = authorizedClientService;
        this.authorizedClientRepository = authorizedClientRepository;
    }

    @Override
    public OAuth2User loadUser(OAuth2UserRequest userRequest) throws OAuth2AuthenticationException {
        OAuth2User delegate = defaultOAuth2UserService.loadUser(userRequest);

        // Load user details from OAuth2 provider
        UserModel userModel = loadUserFromOAuth2Provider(delegate);

        // Create a custom OAuth2User with the merged authorities (roles and permissions)
        OAuth2User customOAuth2User = new CustomOAuth2User(delegate, userModel);

        // Store the OAuth2 authorized client in the OAuth2AuthorizedClientRepository
        OAuth2LoginAuthenticationToken authentication = (OAuth2LoginAuthenticationToken) SecurityContextHolder.getContext().getAuthentication();
        if (authentication != null) {
            String clientRegistrationId = userRequest.getClientRegistration().getRegistrationId();
            String userNameAttributeName = userRequest.getClientRegistration().getProviderDetails()
                    .getUserInfoEndpoint().getUserNameAttributeName();
            OAuth2AuthorizedClient authorizedClient = new OAuth2AuthorizedClient(userRequest.getClientRegistration(),
                    authentication.getName(), delegate.getAuthorities(), delegate.getAttributes(), userNameAttributeName,


                    userRequest.getAccessToken(), userRequest.getRefreshToken());
            authorizedClientRepository.saveAuthorizedClient(authorizedClient, authentication, request, response);
        }

        return customOAuth2User;
    }

    // Implement the method to load user details from the OAuth2 provider
    private UserModel loadUserFromOAuth2Provider(OAuth2User delegate) {
        // Load and map user details from the OAuth2 provider response to your UserModel entity
        // Here, you can fetch roles and permissions associated with the user from the database or the OAuth2 provider's claims.
    }
}
```

3. Ajuste outras partes do seu aplicativo conforme necessário, como os métodos do controlador protegidos usando `@PreAuthorize` e `@PostAuthorize`.

Observe que o código acima é um exemplo simplificado para demonstrar a integração de OAuth2 e OpenID Connect com Spring Security. Dependendo do seu provedor OAuth2 específico e caso de uso, pode ser necessário ajustar o código e a configuração de acordo. Além disso, pode ser necessário implementar outras partes do aplicativo e integrar com a API do seu provedor OAuth2 para buscar detalhes do usuário e informações de reivindicação.

# Referências

6. https://datatracker.ietf.org/doc/html/rfc6947
7. https://openid.net/specs/openid-connect-core-1_0.html
8. https://central.sonatype.com/artifact/org.springframework.boot/spring-boot-starter-oauth2-client/3.1.1
9. https://spring.io/guides/tutorials/spring-boot-oauth2/
10. https://www.baeldung.com/spring-security-5-oauth2-login
11. https://stackoverflow.com/questions/71081479/what-is-the-difference-between-spring-boot-starter-oauth2-client-spring-cloud-s
12. https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#web.security.oauth2.client
13. https://docs.spring.io/spring-security/reference/servlet/oauth2/client/index.html
14. https://docs.spring.io/spring-security/site/docs/5.2.5.RELEASE/reference/html/modules.html
15. https://github.com/spring-projects/spring-security/wiki/OAuth-2.0-Features-Matrix#client-support
16. https://github.com/spring-projects/spring-security
17. https://medium.com/javarevisited/securing-microservices-with-oauth2-and-spring-security-8e1a19871831#:~:text=To%20secure%20microservices%20using%20OAuth2,provides%20access%20to%20protected%20resources.
18. https://www.baeldung.com/spring-security-oauth-auth-server
19. https://github.com/serlesen/authorization-server