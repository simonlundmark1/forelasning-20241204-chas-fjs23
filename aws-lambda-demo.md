# AWS Lambda Demo med NodeJS

## Förutsättningar
- Node.js installerat (version 14.x eller senare)
- AWS-konto (du kan skapa ett gratis konto på aws.amazon.com)
- AWS CLI installerat
- AWS SAM CLI installerat

## Steg 1: Installera nödvändiga verktyg

```bash
# Installera AWS CLI
# För Windows (kör i PowerShell som administratör)
msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi

# För macOS
brew install awscli

# Installera AWS SAM CLI
# För Windows (kör i PowerShell som administratör)
winget install Amazon.SAM-CLI

# För macOS
brew tap aws/tap
brew install aws-sam-cli
```

## Steg 2: Konfigurera AWS CLI
```bash
aws configure
```
Ange dina AWS-uppgifter:
- AWS Access Key ID
- AWS Secret Access Key
- Default region (t.ex. eu-north-1)
- Default output format (json)

## Steg 3: Skapa ett nytt Lambda-projekt
1. Skapa en ny projektmapp:
```bash
sam init
```
Välj följande alternativ:
- AWS Quick Start Templates
- Node.js 14.x
- Hello World Example

## Steg 4: Granska och uppdatera funktionskoden
Din funktionskod finns i `hello-world/app.js`. Här är ett exempel på hur koden kan se ut:

```javascript
exports.lambdaHandler = async (event, context) => {
    try {
        const name = event.queryStringParameters?.name || 'användare';
        const response = {
            statusCode: 200,
            body: JSON.stringify({
                message: `Hej ${name}! Detta är ett svar från din Lambda-funktion.`,
                event: event,
            }),
        };
        return response;
    } catch (err) {
        console.log(err);
        return {
            statusCode: 500,
            body: JSON.stringify({
                message: 'Något gick fel!',
                error: err,
            }),
        };
    }
};
```

## Steg 5: Testa lokalt
1. Bygg projektet:
```bash
sam build
```

2. Starta lokal testning:
```bash
sam local start-api
```

3. Testa funktionen genom att öppna en webbläsare och gå till:
```
http://localhost:3000/hello?name=DittNamn
```

## Steg 6: Publicera till AWS
1. Publicera din funktion:
```bash
sam deploy --guided
```
Följ instruktionerna och ange:
- Stack Name (t.ex. min-lambda-stack)
- AWS Region
- Bekräfta övriga säkerhetsfrågor

## Steg 7: Testa den publicerade funktionen
Efter publiceringen får du en API Gateway URL som ser ut ungefär så här:
```
https://[api-id].execute-api.[region].amazonaws.com/Prod/hello?name=DittNamn
```

## Tips och felsökning
- Använd `sam logs` för att se loggarna från din Lambda-funktion
- Kontrollera IAM-roller och behörigheter i AWS Console
- Använd AWS CloudWatch för detaljerad övervakning
- Testa lokalt med olika event-mallar: `sam local invoke -e events/event.json`

## Nästa steg
- Lägg till fler triggers (API Gateway, S3, DynamoDB, etc.)
- Implementera säkerhet med API-nycklar och AWS Cognito
- Konfigurera CloudWatch Alarms
- Utforska Step Functions för mer komplexa arbetsflöden
- Implementera CI/CD med AWS CodePipeline

## Viktiga kommandon för referens
```bash
# Bygga projektet
sam build

# Testa lokalt
sam local start-api

# Publicera
sam deploy --guided

# Se loggar
sam logs -n FunktionsNamn --stack-name min-lambda-stack

# Radera stack
aws cloudformation delete-stack --stack-name min-lambda-stack
```
