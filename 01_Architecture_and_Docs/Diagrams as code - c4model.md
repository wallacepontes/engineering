# Diagrams as code - C4 model

## PlantUml

### C1 Level
```plantuml
@startuml S611_SICOF_Context
!include <C4/C4_Container.puml>

SHOW_PERSON_OUTLINE()
Person(usuario, "Usuário", "O usuário pode ser qualquer funcionário ou parceiro com acesso aos sistemas do banco")

Container(s611, "S611 SICOF", "Software System", "Sistema de cálculo do IOF, processamento em lote e matriz de parâmetros")
System_Ext(sext, "Sistema Externo", "Qualquer sistema externo que usa o S611")
System_Ext(batch, "Batch", "Qualquer aplicação batch que seja executada de forma assíncrona")
Rel(usuario, s611, "Acessa", "HTTPS")
Rel_Neighbor(s611,sext, "Usa", "JSON")
Rel_Neighbor(batch,s611, "Consome", "SOAP/REST")

SHOW_LEGEND()
@enduml
```

![C1 Level Example](https://www.plantuml.com/plantuml/svg/NLBDRjH03BxdASoUjb95LQdYX53Baj95rMRPx8fZv9trqg3CE1tFYCBR50wSU8gy69v9-2cdEBQ_x_DdpwK4z27Q3keNv-TDlLnKrys2NQ27K3nhdUdYWU3buk9iSP7ps3hoptj5l2gA-gRwqApBJLsjccgtlLskolb9iIOlxEPH8lgMJs6sapWyQZZJk88u_K7FIYtauJvYTnyrE4PdMdPZcIFqw0srdi6m1JGame0i8Aq4iYXmODYZCpmxAOe_qyr5hQXKSWJPKHAk-HW-eoUeloHmJeqqe6EOuR4piUF4kAokJw7tdFJGaWiCPA7ZG41WCVZsQuBeSCCtIy6pgFp8sfGFOIwwkt_ODKNUPVFlVnkLgKPZ3JG9KH0ud-4ftHw3kLFmw_Hzme9zrneSVWpV6N9NvX7wb8Z9n827REx8NhLGPFZfZ6U7Ah2Xxk-5feLTPST9ucQxNTTZLxEYzkFTdgUrJkPsOzyxlVp_RUEy4wKUHTXItdPrjJxRbFLM0UFBkItVbgit-c8koHsYxNu1)


### C2 Level 2

#### Container 611
```plantuml
@startuml S611_SICOF_Container
!include <C4/C4_Container.puml>

SHOW_PERSON_OUTLINE()
AddElementTag("backendContainer", $fontColor=$ELEMENT_FONT_COLOR, $bgColor="#335DA5", $shape=EightSidedShape(), $legendText="backend container\neight sided")
AddRelTag("async", $textColor=$ARROW_COLOR, $lineColor=$ARROW_COLOR, $lineStyle=DashedLine())
AddRelTag("sync/async", $textColor=$ARROW_COLOR, $lineColor=$ARROW_COLOR, $lineStyle=DottedLine())

title Container diagram for S611 Motor de Cálculo

Person(usuario, "Usuário", "O usuário pode ser qualquer funcionário ou parceiro com acesso aos sistemas do banco")

System_Boundary(c1, "S611 Motor de cálculo") {
Container(s611web, "S611 Web", "React", "Front-end do s611")
Container(backend, "S611 Cálculo Serviço", "Spring Boot, Docker Container", "Back-end do s611", $tags="backendContainer")
Container(backend2, "S611 Manter Serviço", "Spring Boot, Docker Container", "Back-end do s611", $tags="backendContainer")
Container(backend3, "S611 Cálculo Batch", "Spring Boot, Docker Container", "Back-end do s611", $tags="backendContainer")
Container(backend4, "S611 Calculadora BNB", "Spring Boot, Docker Container", "Back-end do s611", $tags="backendContainer")

Container(database, "Message BUS ", "RabbitMQ", "F611ENT.CALC")
ContainerDb(database2, "BD DCRD611", "SQL Database", "Base de dados do S611")
}

System_Ext(auth, "BNB Auth SSO [Keyclock]", "Single Sign-On e autenticação das aplicações" )
System_Ext(ldap, "LDAP", "[Dreads/CAPGV]" )
System_Ext(externo, "Sistema Externo", "Qualquer sistema externo que usa o S611")
System_Ext(batch, "Batch", "Qualquer aplicação batch que seja executada de forma assíncrona")

Rel(usuario, s611web, "Acessa", "HTTPS")

Rel(auth, ldap, "Envia/Recebe", "OAuth/JWT")
Rel(auth, s611web, "Acessa", "OAuth/JWT")
Rel(auth, backend, "Acessa", "OAuth/JWT")
Rel_Neighbor(s611web,backend2, "Usa", "JSON")
Rel_Back(s611web,backend, "Usa", "JSON")
Rel_Back(backend,backend4, "Usa", "JSON")
Rel_Back(backend4,backend3, "Usa", "JSON")

Rel_Neighbor(backend,externo, "Usa", "JSON")
Rel_Neighbor(batch,backend, "Consome", "SOAP/REST")
Rel_Neighbor(backend2, database2, "Envia e Recebe", "sync, JDBC")
Rel(backend, database, "Envia e Recebe", "sync, JDBC")
Rel(backend3, database, "Envia e Recebe", "sync, JDBC")
SHOW_LEGEND()
@enduml
```

#### Container 640
```plantuml
@startuml S640_SICONF_Container
!include <C4/C4_Container.puml>
!include <tupadr3/material/queue>
!include <tupadr3/devicons2/react_original>

SHOW_PERSON_OUTLINE()
AddElementTag("backendContainer", $fontColor=$ELEMENT_FONT_COLOR, $bgColor="#335DA5", $shape=EightSidedShape(), $legendText="backend container\neight sided")
AddRelTag("async", $textColor=$ARROW_COLOR, $lineColor=$ARROW_COLOR, $lineStyle=DashedLine())
AddRelTag("sync/async", $textColor=$ARROW_COLOR, $lineColor=$ARROW_COLOR, $lineStyle=DottedLine())

title Container diagram for S640 SICONF - Sistema de Controle Financeiro e Contábil de Operações de Crédito

Person(usuario, "Usuário", "O usuário pode ser qualquer funcionário ou parceiro com acesso aos sistemas do banco")

System_Boundary(c1, "S640 SICONF - Sistema de Controle Financeiro e Contábil de Operações de Crédito") {
Container(s640web, "S640 SICONF Web", "Container: React/TS", "Front-end", $sprite="react_original")
Container(administrativo, "Administrativo", "Container: Spring Boot", "Back-end", $tags="backendContainer")
Container(dominio, "Domínio", "Spring Boot, Docker Container", "Back-end", $tags="backendContainer")
Container(desembolso, "Desembolso", "Spring Boot, Docker Container", "Back-end", $tags="backendContainer")
Container(controle_restricoes, "Controle Restrições", "Spring Boot, Docker Container", "Back-end", $tags="backendContainer")
Container(ger_lancamentos, "Gerenciador de Lançamentos", "Spring Boot, Docker Container", "Back-end", $tags="backendContainer")
Container(operacao_servico, "Operação Serviço", "Spring Boot, Docker Container", "Back-end", $tags="backendContainer")
Container(ger_pendencias, "Gerenciador Pendências", "Spring Boot, Docker Container", "Back-end", $tags="backendContainer")
Container(transferencia_atraso, "Transferência Atraso", "Spring Boot, Docker Container", "Back-end", $tags="backendContainer")
Container(ger_debito_automatico, "Gerenciador Débito Automático", "Spring Boot, Docker Container", "Back-end", $tags="backendContainer")
Container(calculo_servico, "Cálculo Serviço", "Spring Boot, Docker Container", "Back-end", $tags="backendContainer")
Container(ger_calculo, "Gerenciador Cálculo", "Spring Boot, Docker Container", "Back-end", $tags="backendContainer")
Container(evento_contabil, "Evento Contábil", "Spring Boot, Docker Container", "Back-end", $tags="backendContainer")
Container(ger_prejuizamento, "Gerenciador Prejuizamento", "Spring Boot, Docker Container", "Back-end", $tags="backendContainer")
Container(controle_parcelas, "Controle de Parcelas", "Spring Boot, Docker Container", "Back-end", $tags="backendContainer")
Container(ger_credito_conta, "Gerenciador Crédito Conta", "Container: Spring Boot", "Back-end", $tags="backendContainer")
Container(previsao_liquidacao, "Previsão Liquidação", "Container: Spring Boot", "Back-end", $tags="backendContainer")
Container(renegociacao_servico, "Renegociação Serviço", "Container: Spring Boot", "Back-end", $tags="backendContainer")

ContainerQueue(mq, "IBM MQ ", "Mainframe: IBMMQ", "F611ENT.CALC", $sprite="queue")
ContainerDb(db2, "DB2 DCRD640", "DB2", "Base de dados")
}

System_Ext(auth, "BNB Auth SSO [Keyclock]", "Single Sign-On e autenticação das aplicações" )
System_Ext(ldap, "LDAP", "[Dreads/CAPGV]" )
System_Ext(externo, "Sistema Externo", "Qualquer sistema externo")
System_Ext(batch, "Batch", "Qualquer aplicação batch que seja executada de forma assíncrona")

Rel(usuario, s640web, "Acessa", "HTTPS")

Rel(auth, ldap, "Envia/Recebe", "OAuth/JWT")
Rel(auth, s640web, "Acessa", "OAuth/JWT")
Rel_Neighbor(s640web, administrativo, "Usa", "JSON")
Rel_Neighbor(s640web,dominio, "Usa", "JSON")
Rel(s640web, operacao_servico, "Usa", "JSON")
Rel(s640web, desembolso, "Usa", "JSON")
Rel( desembolso, ger_lancamentos, "Usa", "JSON")
Rel(s640web, ger_lancamentos, "Usa", "JSON")
Rel(s640web, controle_restricoes, "Usa", "JSON")
Rel(s640web, transferencia_atraso, "Usa", "JSON")
Rel(s640web, ger_pendencias, "Usa", "JSON")

Rel(transferencia_atraso, controle_restricoes, "Usa", "JSON")

Rel_Back( evento_contabil, ger_prejuizamento, "Usa", "JSON")
Rel_Back( evento_contabil, transferencia_atraso, "Usa", "JSON")
Rel_Back( evento_contabil, ger_calculo, "Usa", "JSON")
Rel_Back( evento_contabil, calculo_servico, "Usa", "JSON")
Rel_Back( evento_contabil, renegociacao_servico, "Usa", "JSON")
Rel_Back( evento_contabil, controle_parcelas, "Usa", "JSON")

Rel_Back( ger_pendencias, transferencia_atraso, "Usa", "JSON")
Rel_Back( ger_pendencias, operacao_servico, "Usa", "JSON")
Rel_Back( ger_pendencias, desembolso, "Usa", "JSON")
BiRel( ger_pendencias, ger_debito_automatico, "Usa", "JSON")
Rel( ger_pendencias, ger_prejuizamento, "Usa", "JSON")
Rel( ger_pendencias, renegociacao_servico, "Usa", "JSON")
BiRel( ger_pendencias, controle_parcelas, "Usa", "JSON")
BiRel( ger_pendencias, previsao_liquidacao, "Usa", "JSON")

Rel(ger_debito_automatico,ger_lancamentos, "Usa", "JSON")
Rel_Back( ger_debito_automatico, ger_credito_conta, "Usa", "JSON")

SHOW_LEGEND()
@enduml
```

### C3 Level 3

```plantuml
@startuml
!include <C4/C4_Component.puml>

SHOW_PERSON_OUTLINE()
Container(s640web, "S640 SICONF WEB", "React.JS/Nginx", "Front-end", $sprite="react_original")

System_Boundary(c1, "API") {
Component(calcController, "ControleCalculoController", "Componente: Spring Rest Controller", "Controller de acesso aos cálculos")
Component(calculoFichaNormalService, "CalculoFichaNormalService", "Componente: Spring Service", "Cálculo da ficha normal da operação")
Component(calculoParcialFichaNormalService, "CalculoParcialFichaNormalService", "Componente: Spring Service", "Cálculo parcial da ficha normal da operação")
Component(recalculoParcelaService, "RecalculoParcelaService", "Componente: Spring Service", "Recálculo de parcela")
Component(calculoFichaAtrasoService, "CalculoFichaAtrasoService", "Componente: Spring Service", "Cálculo da ficha atraso")
Component(calculoParcelaNormalService, "CalculoParcelaNormalService", "Componente: Spring Service", "Cálculo da parcela em situação de normalidade")
}
System_Ext(s611CalculoServico, "S611CalculoServico", "S611 Motor de Cálculo")
System_Ext(s640EventoContabil, "S640EventoContabil", "S640 Evento Contábil")
System_Ext(s640PendenciaOperacao, "S640PendenciaOperacao", "S640 Pendência Operação")
System_Ext(s648OperacaoServico, "S648OperacaoServico", "S648 Operação Serviço")

Rel(s640web, calcController, "Acessa", "HTTPS")
Rel(calcController,calculoFichaNormalService, "Usa")
Rel(calcController,calculoParcialFichaNormalService, "Usa")
Rel(calcController,recalculoParcelaService, "Usa")
Rel(calcController,calculoFichaAtrasoService, "Usa")
Rel(calcController,calculoParcelaNormalService, "Usa")

Rel(calculoFichaAtrasoService,s611CalculoServico, "Usa", "WSClient / JSON")
Rel(calculoFichaNormalService,s611CalculoServico, "Usa", "WSClient / JSON")
Rel(calculoParcelaNormalService,s611CalculoServico, "Usa", "WSClient / JSON")
Rel(calculoParcialFichaNormalService,s611CalculoServico, "Usa", "WSClient / JSON")

Rel(calculoFichaAtrasoService,s640EventoContabil, "Usa", "WSClient / JSON")
Rel(calculoFichaNormalService,s640EventoContabil, "Usa", "WSClient / JSON")
Rel(calculoParcelaNormalService,s640EventoContabil, "Usa", "WSClient / JSON")
Rel(calculoParcialFichaNormalService,s640EventoContabil, "Usa", "WSClient / JSON")

Rel(calculoFichaAtrasoService,s640PendenciaOperacao, "Usa", "WSClient / JSON")
Rel(calculoFichaNormalService,s640PendenciaOperacao, "Usa", "WSClient / JSON")
Rel(calculoParcelaNormalService,s640PendenciaOperacao, "Usa", "WSClient / JSON")
Rel(calculoParcialFichaNormalService,s640PendenciaOperacao, "Usa", "WSClient / JSON")

Rel(calculoFichaAtrasoService,s648OperacaoServico, "Usa", "WSClient / JSON")
Rel(calculoFichaNormalService,s648OperacaoServico, "Usa", "WSClient / JSON")
Rel(calculoParcelaNormalService,s648OperacaoServico, "Usa", "WSClient / JSON")
Rel(calculoParcialFichaNormalService,s648OperacaoServico, "Usa", "WSClient / JSON")

SHOW_LEGEND()
@enduml
```

## [Mermaid](https://mermaid.js.org/syntax/c4.html)

```mermaid
    C4Deployment
    title Deployment Diagram for Internet Banking System - Live

    Deployment_Node(mob, "Customer's mobile device", "Apple IOS or Android"){
        Container(mobile, "Mobile App", "Xamarin", "Provides a limited subset of the Internet Banking functionality to customers via their mobile device.")
    }

    Deployment_Node(comp, "Customer's computer", "Microsoft Windows or Apple macOS"){
        Deployment_Node(browser, "Web Browser", "Google Chrome, Mozilla Firefox,<br/> Apple Safari or Microsoft Edge"){
            Container(spa, "Single Page Application", "JavaScript and Angular", "Provides all of the Internet Banking functionality to customers via their web browser.")
        }
    }

    Deployment_Node(plc, "Big Bank plc", "Big Bank plc data center"){
        Deployment_Node(dn, "bigbank-api*** x8", "Ubuntu 16.04 LTS"){
            Deployment_Node(apache, "Apache Tomcat", "Apache Tomcat 8.x"){
                Container(api, "API Application", "Java and Spring MVC", "Provides Internet Banking functionality via a JSON/HTTPS API.")
            }
        }
        Deployment_Node(bb2, "bigbank-web*** x4", "Ubuntu 16.04 LTS"){
            Deployment_Node(apache2, "Apache Tomcat", "Apache Tomcat 8.x"){
                Container(web, "Web Application", "Java and Spring MVC", "Delivers the static content and the Internet Banking single page application.")
            }
        }
        Deployment_Node(bigbankdb01, "bigbank-db01", "Ubuntu 16.04 LTS"){
            Deployment_Node(oracle, "Oracle - Primary", "Oracle 12c"){
                ContainerDb(db, "Database", "Relational Database Schema", "Stores user registration information, hashed authentication credentials, access logs, etc.")
            }
        }
        Deployment_Node(bigbankdb02, "bigbank-db02", "Ubuntu 16.04 LTS") {
            Deployment_Node(oracle2, "Oracle - Secondary", "Oracle 12c") {
                ContainerDb(db2, "Database", "Relational Database Schema", "Stores user registration information, hashed authentication credentials, access logs, etc.")
            }
        }
    }

    Rel(mobile, api, "Makes API calls to", "json/HTTPS")
    Rel(spa, api, "Makes API calls to", "json/HTTPS")
    Rel_U(web, spa, "Delivers to the customer's web browser")
    Rel(api, db, "Reads from and writes to", "JDBC")
    Rel(api, db2, "Reads from and writes to", "JDBC")
    Rel_R(db, db2, "Replicates data to")

    UpdateRelStyle(spa, api, $offsetY="-40")
    UpdateRelStyle(web, spa, $offsetY="-40")
    UpdateRelStyle(api, db, $offsetY="-20", $offsetX="5")
    UpdateRelStyle(api, db2, $offsetX="-40", $offsetY="-20")
    UpdateRelStyle(db, db2, $offsetY="-10")


```

## References

1. [cannot-open-url](https://forum.plantuml.net/17086/cannot-open-url)
2. [Mermaid](https://mermaid.js.org/syntax/c4.html)
