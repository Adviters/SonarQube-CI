# SonarQube CI Centralizado

Este repositorio centraliza los workflows de SonarQube para reutilizar configuración estándar.

## Cómo funciona?
Los repos reutilizan workflows con:
uses: adviters/sonarqube-ci/.github/workflows/sonarqube.yml@main

## Requisitos
Configurar secrets:
- SONAR_HOST_URL
- SONAR_TOKEN

## Branch de análisis
Por defecto:
develop

## Implementación JS/TS
Crear:
.github/workflows/sonarqube.yml


Contenido:
```
name: SonarQube
on:
  push:
    branches: ["develop"]
  pull_request:
 
permissions:
  contents: read
  pull-requests: write
  issues: write
 
jobs:
  sonar:
    permissions:
      contents: read
      pull-requests: write
      issues: write
    uses: adviters/sonarqube-ci/.github/workflows/sonarqube.yml@main
    secrets: inherit
    with:
      sonar_sources: src
```

## Implementación .NET
Solo cambiar uses:
```
  uses: adviters/sonarqube-ci/.github/workflows/sonarqube-net.yml@main
```

## Pasos
1. Crear secrets
2. Crear workflow (archivo .yml)
3. Ajustar branch (en el ejemplo esta como develop)
4. Push


## Objetivo
Estandarizar pipelines y centralizar configuración
