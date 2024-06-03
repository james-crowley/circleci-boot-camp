## Milestone 1: Exploring the Orb Registry & Enhancing Secret Management with Contexts

### Overview
This milestone focuses on leveraging the CircleCI orb registry to enhance the security of our CI/CD pipeline. Orbs are reusable packages of YAML configuration that streamline repetitive tasks and integration with third-party tools. We'll incorporate security tools like Snyk and GitGuardian into our pipeline using orbs, abstracting away complexity and simplifying setup for developers.

Enterprises can create custom orbs to enforce specific workflows or requirements for their projects, publishing them as either private or public orbs. Developers can seamlessly include these orbs in their CircleCI configurations, enhancing productivity and consistency. Exploring the orb registry offers a glimpse into the diverse interactions and capabilities facilitated by orbs.

In this milestone, we will also explore different methods of injecting secrets into your CircleCI environment. Security is paramount and is a fundamental aspect of the CircleCI platform. Up to this point in the labs, we have utilized environment variables in project settings.

However, while storing secrets in project settings is convenient, it may not be the most scalable approach, especially in an enterprise setting. To address this, CircleCI introduces the concept of Contexts. Contexts allow you to manage secrets at the organization level, enabling you to share secrets across multiple projects and reuse them where applicable. Additionally, contexts offer advanced security features such as restricting access to secrets based on teams, projects, and pipeline values, providing granular control over secret access.

CircleCI also provides a way to avoid storing secrets within the CircleCI environment altogether. With OpenID Connect (OIDC), you can integrate with various secrets managers such as AWS Secrets Manager and HashiCorp Vault. Using OIDC, you can pull down secrets during runtime, thus not relying on CircleCI to store your secrets. This approach is best practice, especially for enterprises. External vaults offer more features than storing secrets in CircleCI, such as automatic password rotation and more granular permissions. While we won't cover how to setup OIDC with Vault today, you can find more information at [Integrate CircleCI with HashiCorp Vault using OIDC](https://circleci.com/blog/oidc-with-vault/).

In this milestone, we will demonstrate how to transition our API keys for Snyk and GitGuardian to a context and restrict access to our project.

### Steps

1. **Grab Snyk and GitGuardian API Keys:**
   - Obtain API keys for [Snyk](https://docs.snyk.io/snyk-api/authentication-for-api) and [GitGuardian](https://docs.gitguardian.com/api-docs/personal-access-tokens) to authenticate with their respective services.

2. **Create and Configure a Context:**
   - Create a context named `ambassador`.
   - Add two values to the context: `GITGUARDIAN_API_KEY` and `SNYK_TOKEN`.

3. **Restrict Context Access:**
   - Limit the use of the `ambassador` context to our project.
   - Use expression restrictions to further control context access based on specific conditions, such as restricting access to the main branch and disabling SSH access.
     ```pipeline.git.branch == "main" and not job.ssh.enabled```
     Replace `"main"` with the name of your current branch.

3. **Add Orbs to Configuration File:**
   - Integrate Snyk and GitGuardian orbs into the CircleCI configuration file (`config.yml`) to incorporate security checks into the pipeline.

4. **Opt In To Use 3rd Party Orbs:**
   - In the CircleCI UI, go to Organization Settings, then to Security. You will need to allow uncertified orbs to be used, please switch the `No` to a `Yes`.

5. **Run Pipeline to See the Results:**
   - Trigger the pipeline to execute the configured jobs and observe the results, including security checks performed by Snyk and GitGuardian.

### Objectives
- Obtain and securely store API keys for Snyk and GitGuardian.
- Integrate Snyk and GitGuardian orbs into the CircleCI configuration file.
- Successfully execute the pipeline and verify the results, including security checks provided by the incorporated orbs.
- Understand the importance of managing secrets securely in CircleCI.
- Familiarize yourself with the concept of Contexts in CircleCI.
- Learn how to transition project-level secrets to organization-level contexts.
- Gain proficiency in configuring context access restrictions for enhanced security.
- Update the configuration file to utilize the newly created context for secret injection.
