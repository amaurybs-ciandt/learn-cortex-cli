## Code Scan (Cortex CLI)
Quando estamos trabalhando com bases de repositórios dentro de um projeto, geralmente usamos um repositório de código para servir de base para todo nosso projeto, é ali que estarão todos os arquivos, artefatos, bibliotecas, credenciais de acessos e os principais arquivos fontes.

Para melhoria da segurança e uma postura robusta, é considerado boa prática verificar e executar um scan dentro dessa base de código para evitar exposição de credenciais e outros arquivos. Vejammos um exemplo bem rico de detalhes do comando abaixo:

```bash
./cortexcli --api-base-url <URL> --api-key <KEY> --api-key-id <ID> code scan -h
Update available: CortexCLI 0.17.0 → 0.18.0

To upgrade, check the platform UI or run the following command:
crtx_resp=$(curl --fail "https://api-ciandt.xdr.us.paloaltonetworks.com/public_api/v1/unified-cli/releases/download-link?os=linux&architecture=amd64" -H "x-xdr-auth-id: 133" -H "Authorization: ${CORTEX_API_KEY}") && crtx_url=$(echo $crtx_resp | jq -r ".signed_url") && crtx_file=$(echo $crtx_resp | jq -r ".file_name") && curl -o $crtx_file $crtx_url
NAME:
   Cortex CLI code scan - Scans a code repository

USAGE:
   Cortex CLI code scan [command options]

OPTIONS:
   --repo-id                           Repository ID (Required) [$CORTEX_CODE_REPO_ID]
   --directory                         Directory path to scan (directory or file Required) [$CORTEX_CODE_DIRECTORY]
   --file                              File path to scan (directory or file Required) [$CORTEX_CODE_FILE]
   --branch                            Branch name [$CORTEX_CODE_BRANCH]
   --output-file-path                  Output path [$CORTEX_CODE_OUTPUT_FILE_PATH]
   --framework                         List of frameworks to scan [$CORTEX_CODE_FRAMEWORK]
   --skip-framework                    List of frameworks to skip [$CORTEX_CODE_SKIP_FRAMEWORK]
   --create-repo-if-missing            Should create repository if it is missing (default: false) [$CORTEX_CODE_CREATE_REPO_IF_MISSING]
   --upload-mode                       Determines upload behavior: 'upload' uploads results, 'no-upload' disables uploads, and 'no-code' excludes code blocks from findings. [$CORTEX_CODE_UPLOAD_MODE]
   --repo-root-for-plan-enrichment     Enriches Terraform plan findings by mapping them to their original .tf files [$CORTEX_CODE_REPO_ROOT_FOR_PLAN_ENRICHMENT]
   --var-file                          Variable files to load in addition to the default files, Currently only supported for source Terraform (.tf file) and Helm chart scans. [$CORTEX_CODE_VAR_FILE]
   --source                            Source of execution, for example - Jenkins, CLI, etc [$CAS_SOURCE]
   --output                            Report output format (json/etc.) [$CORTEX_CODE_OUTPUT]
   --deep-analysis                     Enable or disable deep analysis mode of the TF plan and file connection (default: false) [$CORTEX_CODE_DEEP_ANALYSIS]
   --download-external-modules         Download external terraform modules from public git repositories and terraform registry (default: false) [$CORTEX_CODE_DOWNLOAD_EXTERNAL_MODULES]
   --external-modules-download-path    Specified path to download external modules, default is '.external_modules' [$CORTEX_CODE_EXTERNAL_MODULES_DOWNLOAD_PATH]
   --ignore-existing-secrets           Ignores secrets that already exist in the periodic scan (default: false) [$CORTEX_CODE_IGNORE_EXISTING_SECRETS]
   --validate-secrets                  Check if the secrets are valid (default: false) [$CORTEX_CODE_VALIDATE_SECRETS]
   --skip-path                         Filepath (file or directory) to skip [$CORTEX_CODE_SKIP_PATH]
   --compact                           Do not display code blocks in the output (default: false) [$CORTEX_CODE_COMPACT]
   --summary-position                  Whether the summary will be appended on top (before the checks results) or on bottom (after check results), default is on top. [$CORTEX_CODE_SUMMARY_POSITION]
   --no-fail-on-crash                  Return exit code 0 instead of 2 which indicates a failure in the integration with the platform (default: false) [$CORTEX_CODE_NO_FAIL_ON_CRASH]
   --timeout value                     Timeout for triggered local scan processes. Defaults to 15 minutes. Numeric values without units are interpreted as seconds (e.g., '30' = 30s). (default: 15m) [$CORTEX_CODE_TIMEOUT]
   --help, -h                          show help

```