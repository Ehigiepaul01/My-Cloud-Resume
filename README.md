# Cloud Resume — AWS Deployment

A cloud-hosted resume project built to demonstrate practical AWS infrastructure, Infrastructure as Code concepts, and CI/CD.

## Architecture

```text
GitHub
  │
  └── GitHub Actions
        │
        └── AWS S3
              │
              └── Static resume website
```

## What this project demonstrates

- AWS S3 static website hosting
- Automated deployment with GitHub Actions
- Infrastructure configuration with AWS CloudFormation
- IAM-based deployment authentication
- Repeatable build and deployment workflow
- Basic cloud security and least-privilege considerations

## Repository structure

```text
.
├── .github/
│   └── workflows/
│       └── deploy.yml
├── Cloud Resume/
├── cloudformation/
└── README.md
```

> The exact directory names above may vary with the current project structure; the deployment workflow is the source of truth for the active build path.

## CI/CD

A push to the `main` branch triggers the deployment workflow. The pipeline checks out the repository, prepares the Node.js environment, builds the project, and synchronizes the generated site to the S3 bucket.

The workflow is being modernized to use GitHub Actions' OIDC authentication with AWS rather than long-lived AWS access keys stored as repository secrets.

## Security improvements

- Prefer short-lived GitHub OIDC credentials over static AWS access keys.
- Restrict the AWS IAM role to the S3 bucket and actions required for deployment.
- Keep the S3 bucket encrypted at rest.
- Do not commit AWS credentials, `.env` files, or other secrets.
- Review IAM permissions periodically and remove unused access.

## Infrastructure as Code

The project includes CloudFormation configuration for the AWS resources used by the resume deployment. This makes the infrastructure reproducible rather than relying entirely on manual console configuration.

## Future improvements

- Add CloudFront for HTTPS delivery and global caching.
- Add AWS Certificate Manager for TLS.
- Add Route 53 custom-domain configuration.
- Add automated validation and security scanning to CI.
- Add deployment rollback/versioning strategy.
- Add monitoring and basic operational documentation.

## Technologies

**Cloud:** AWS S3, CloudFormation  
**CI/CD:** GitHub Actions  
**Web:** HTML, CSS, JavaScript  
**Automation:** YAML, Node.js

## Author

Paul Ehigie — Systems & Cloud Infrastructure Engineer in training, with production IT infrastructure experience across Linux, hosting, DNS, SSL, web infrastructure, and server operations.
