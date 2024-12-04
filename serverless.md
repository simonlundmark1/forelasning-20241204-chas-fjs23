# Serverless

## 1. Introduktion och praktisk tillämpning.

### Olika typer av molntjänster för att produktionssätta kod

*Högnivå till lågnivå*

- Software as a Service (SaaS)
    - Exempel: Google Workspace, Microsoft 365

- Function as a Service (FaaS) <-- Vi kommer att använda detta
    - Exempel: AWS Lambda, Azure Functions

- Platform as a Service (PaaS)
    - Exempel: AWS Elastic Beanstalk, Azure App Service

- Infrastructure as a Service (IaaS)
    - Exempel: AWS EC2, Azure Virtual Machines    

*Vi har även detta begrepp*

- Infrastructure as Code (IaC)
    - Vilket innebär att vi beskriver vår infrastruktur med hjälp av kod.
    - Vad händer om hela molnmiljön försvinner? Failover!

---

## Vad är Serverless Framework?

- Med Serverless Framework kan vi skapa och distribuera serverlösa funktioner.
- Automatisk skalning baserat på efterfrågan
- Betala endast för den tid koden körs
- Ingen serverhantering krävs

### Fördelar med Serverless

1. **Kostnadseffektivt**
   - Betala endast för faktisk användning
   - Ingen kostnad för inaktiv tid
   - Automatisk skalning eliminerar överprovisioning

2. **Snabb utveckling**
   - Fokus på affärslogik istället för infrastruktur
   - Enklare driftsättning
   - Färdiga integrationer med molntjänster

3. **Hög tillgänglighet**
   - Inbyggd redundans
   - Automatisk felhantering
   - Global distribution möjlig

### Vanliga användningsfall

1. **API-endpoints**
   - REST API:er
   - GraphQL-servrar
   - Webhooks

2. **Databearbetning**
   - Bildbehandling
   - Filkonvertering
   - Dataanalys
   - ETL-processer (Extract, Transform, Load)

3. **Schemalagda jobb**
   - Backup
   - Rapportgenerering
   - Datasynkronisering

4. **Realtidsbearbetning**
   - IoT-data
   - Chattapplikationer
   - Streaming-tjänster

### Molnleverantörernas ekosystem

#### AWS
- **Lambda** - Serverlösa funktioner
- **API Gateway** - API-hantering
- **DynamoDB** - NoSQL-databas
- **S3** - Objektlagring
- **EventBridge** - Händelsehantering
- **SQS/SNS** - Meddelandeköer

#### Azure
- **Azure Functions** - Serverlösa funktioner
- **API Management** - API-hantering
- **Cosmos DB** - NoSQL-databas
- **Blob Storage** - Objektlagring
- **Event Grid** - Händelsehantering
- **Service Bus** - Meddelandeköer

#### Google Cloud
- **Cloud Functions** - Serverlösa funktioner
- **API Gateway** - API-hantering
- **Firestore** - NoSQL-databas
- **Cloud Storage** - Objektlagring
- **Pub/Sub** - Meddelandehantering

### Arkitekturmönster för Serverless

1. **Event-driven arkitektur**
   - Löst kopplade komponenter
   - Asynkron kommunikation
   - Skalbar och flexibel

2. **Microservices**
   - Små, oberoende funktioner
   - Enklare att underhålla och uppdatera
   - Bättre felhantering

3. **Backend-for-Frontend (BFF)**
   - Specialiserade API:er för olika klienter
   - Optimerad datahämtning
   - Förbättrad prestanda

### Begränsningar och utmaningar

1. **Cold starts**
   - Fördröjning vid första anropet
   - Kan påverka användarupplevelsen
   - Lösningar: Provisioned Concurrency, Keep-warm strategier

2. **Vendor lock-in**
   - Beroende av specifika molntjänster
   - Kan försvåra migrering
   - Lösning: Abstraktionslager, portabel kod

3. **Debugging och övervakning**
   - Distribuerad loggning
   - Komplex felsökning
   - Verktyg: CloudWatch, Application Insights

4. **Kostnadskontroll**
   - Oförutsägbar användning
   - Risk för överraskande kostnader
   - Lösning: Budgetvarningar, användningsgränser

---

## Bästa praxis

1. **Funktionsdesign**
   - Håll funktioner små och fokuserade
   - Implementera idempotens
   - Hantera fel gracefully

2. **Säkerhet**
   - Använd minsta möjliga behörigheter
   - Kryptera känslig data
   - Implementera autentisering och auktorisering

3. **Prestanda**
   - Optimera minnesutnyttjande
   - Minimera cold starts
   - Använd caching när möjligt

4. **Kostnadsoptimering**
   - Övervaka användning
   - Sätt upp budgetvarningar
   - Optimera funktioners körtid

---

## Framtiden för Serverless

- Förbättrad cold start-hantering
- Bättre utvecklarverktyg
- Ökad integration med edge computing
- Mer sofistikerade orkestreringsmöjligheter

---

## Demo / Övning

