# Azure Functions Demo med NodeJS

## Förutsättningar
- Node.js installerat (version 14.x eller senare)
- Visual Studio Code
- Azure Functions Core Tools
- Ett Azure-konto (du kan skapa ett gratis konto på azure.com)

## Steg 1: Installera nödvändiga verktyg

```bash
# Installera Azure Functions Core Tools
npm install -g azure-functions-core-tools@4

# Installera Azure CLI
# För Windows (kör i PowerShell som administratör)
winget install Microsoft.AzureCLI
# För macOS
brew install azure-cli
```

## Steg 2: Skapa ett nytt Azure Functions-projekt
1. Öppna terminalen och skapa en ny mapp:
```bash
mkdir min-azure-function
cd min-azure-function
```

2. Initiera ett nytt Functions-projekt:
```bash
func init --javascript
```

## Steg 3: Skapa en ny funktion
```bash
func new
```
Välj "HTTP trigger" och ge funktionen namnet "HelloWorld"

## Steg 4: Granska och uppdatera funktionskoden
Din funktionskod finns nu i `HelloWorld/index.js`. Här är ett exempel på hur koden ser ut:

```javascript
module.exports = async function (context, req) {
    context.log('JavaScript HTTP trigger function processed a request.');

    const name = (req.query.name || (req.body && req.body.name));
    const responseMessage = name
        ? "Hej, " + name + "! Detta är ett svar från din Azure Function."
        : "Skicka med en name-parameter i din förfrågan för att få en personlig hälsning.";

    context.res = {
        status: 200,
        body: responseMessage
    };
}
```

## Steg 5: Testa lokalt
1. Starta funktionen lokalt:
```bash
func start
```

2. Testa funktionen genom att öppna en webbläsare och gå till:
```
http://localhost:7071/api/HelloWorld?name=DittNamn
```

## Steg 6: Publicera till Azure
1. Logga in på Azure:
```bash
az login
```

2. Skapa en funktionsapp i Azure:
```bash
az group create --name MinResourceGrupp --location northeurope
az storage account create --name minlagring123 --location northeurope --resource-group MinResourceGrupp --sku Standard_LRS
az functionapp create --resource-group MinResourceGrupp --consumption-plan-location northeurope --runtime node --runtime-version 14 --functions-version 4 --name min-funktion-app-123 --storage-account minlagring123
```

3. Publicera din funktion:
```bash
func azure functionapp publish min-funktion-app-123
```

## Steg 7: Testa den publicerade funktionen
Efter publiceringen får du en URL som ser ut ungefär så här:
```
https://min-funktion-app-123.azurewebsites.net/api/HelloWorld?name=DittNamn
```

## Tips och felsökning
- Kontrollera att alla verktyg är korrekt installerade genom att köra `func --version`
- Om du får problem med behörigheter i Azure, kontrollera att du är inloggad med rätt konto
- Använd `func azure functionapp logs tail` för att se live-loggar från din publicerade funktion

## Nästa steg
- Lägg till fler triggers (Timer, Blob Storage, etc.)
- Implementera säkerhet med API-nycklar
- Koppla din funktion till en databas
- Utforska Durable Functions för mer komplexa arbetsflöden
