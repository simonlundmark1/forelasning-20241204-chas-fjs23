# Agenda

## Avancerad versionshantering med Git – Fördjupning och best practices.

- [Git - olika arbetsflöden](git.md)

## AI-verktyg för CI/CD-automatisering

*Exempel på verktyg vi kommer använda:*

- Cursor
- Claude
- ChatGPT
- Github Copilot

## Implementering av webbtjänster med Javascript – Från backend till frontend med verktyg som Jira och Docker.

- Demo i Reseplaneraren
    - Sätta upp Jira
    - Integrera Jira med Github
    - Github
        - Branch protection rules
            - Code reviews => Någon ska kolla på koden innan den mergas
            - Status checks => Kör olika automatiserade tester
    - Github Actions
        - Skapa en pipeline för att bygga och testa appen
        - Skapa en pipeline för att bygga en Docker image och pusha till Docker Hub

## Serverless Framework – Introduktion och praktisk tillämpning.

Mål: Deploya en serverless funktion i Azure Functions och en i AWS Lambda

Teori: [Intro till serverless](serverless.md)
Demo i Azure: [azure-functions-demo.md](azure-functions-demo.md)
Övning i AWS: [aws-lambda-demo.md](aws-lambda-demo.md)