## Git hub Actions

GitHub Actions es una plataforma de integración y despliegue continuos (CI/CD) que te permite automatizar tu mapa de compilación, pruebas y despliegue. Puedes crear workflows, crear y probar cada solicitud de cambios en tu repositorio o desplegar solicitudes de cambios fusionadas a producción.

![GitHutbActions](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/83f1e40e-95b8-4c7d-b3a4-0239e2bd6c52/Untitled.png)

### Workflows

Un flujo de trabajo es un proceso automatizado configurable que ejecutará uno o más jobs. Los flujos de trabajo se definen mediante un archivo de YAML que se verifica en tu repositorio y se ejecutará cuando lo active un evento dentro de este o puede activarse manualmente o en una programación definida.
Estructura del workflow

Para llevar un correcto orden:

En el repositorio, crear el directorio `.github/workflows/` para almacenar los archivos de flujo de trabajo.

```yaml
name: Primer_Workflow # Nombre de workflow
on: # Se utiliza el comando on para setear que eventos harán que se active el workflow. Por ejemplo, cuando alguien suba a cualquier rama del repositorio
  push:
    branches:
      - Antony
jobs: # Agrupa todos los trabajos que se ejecutan en el flujo de trabajo
  Test_job: # Nombre de los jobs
   runs-on: ubuntu-latest # confgura que ejecutor tendrá el job
   steps: # agrupa los pasos que se realizara en este job
      - name: Prueba
        run: echo "Hello World" 
```

Como setear credenciales AWS

```yaml
name: Primer workflow
on:
  push:
    branches:
      - Antony
jobs:
  Prueba:
    runs-on: ubuntu-latest
    permissions:
      id-token: write
      contents: read
    steps:
      - name: Configure AWS credentials from Test account
        uses: aws-actions/configure-aws-credentials@v2
        with:
          role-to-assume: arn:aws:iam::111111111111:role/my-github-actions-role-test
          aws-region: sa-east-1
```
