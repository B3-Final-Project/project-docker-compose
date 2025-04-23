# Projet-B3-Ynov

## Setup

### Prerequisites

- Node.js
- Git
- AWS CLI (WSL if on windows)
- sops (WSL if on windows)

### Installation

1. Clone the repository
    ```bash
    git clone --recurse-submodules https://github.com/MaxPW777/Projet-B3-Ynov.git 
    ```
2. Install AWS CLI (use WSL if on windows)
3. add this configuration to your `~/.aws/config` file
    ```
   [profile b3]
   sso_start_url = https://d-80670b5ad9.awsapps.com/start
   sso_region = eu-west-3
   sso_account_id = 989418411786
   sso_role_name = PowerUserAccess
   region = eu-west-3
   output = json
   ```
4. log in with your aws user account with aws cli 
   ```bash
   aws sso login --profile b3
   ```
5. decrypt the env files
   ```bash 
   npm run sops:decrypt
   ```
   
### Running the project

to run the project, you can run:
```bash
docker compose up --build
```

note: the build command is required when changing npm packages or env variables
otherwise use:
```bash
docker compose up
```

## Tech Stack

- **Frontend**: Next.js, React, Tailwind CSS
- **Backend**: Node.js, NestJS
- **Database**: PostgreSQL, MongoDB
- **DevOps**: Docker, GitHub Actions
- **Deployment**: AWS ECS, AWS S3, AWS CloudFront

## Organisation

- **Management**: GitHub Projects
- **Communication**: Discord
