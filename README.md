# terraform-dependabot-tutorial

[This link](https://docs.github.com/en/code-security/dependabot/dependabot-version-updates/configuration-options-for-the-dependabot.yml-file#terraform) is the official documentation for the GitHub Dependabot Terraform support.

## Configure Dependabot

If you do not already have a dependabot.yml file create `.github/dependabot.yml`. [This link](https://docs.github.com/en/code-security/dependabot/dependabot-version-updates/configuration-options-for-the-dependabot.yml-file#configuration-options-for-the-dependabotyml-file) provides detailed documentaion for each of the configuration items.

Add the following configuration:

```yaml
version: 2
updates:
  - package-ecosystem: "terraform"
    directory: "/" # Dependabot doesn't recursively search for directories
    schedule:
      interval: "daily" # weekdays only
      time: "09:00"
      timezone: "America/New_York"
    open-pull-requests-limit: 10 
    allow:
      - dependency-type: "all"
```

Dependencies supported by terraform ecosystem:

- Modules hosted on Terraform Registry or a publicly reachable Git repository.
- Terraform providers.
- Private Terraform Registry.

You can also enable it by navigating to the security tab for the repository -> Dependabot alerts -> Enable Dependabot Alerts -> Dependabot version updates and click `Configure`

## Triggering Dependabot

Dependabot will check your dependencies at the interval define, but you can also manually trigger it.

- First commit: Dependabot will perform a dependency scan the first time you commit a `dependabot.yml` file to a repository.
- Dependency Graph: You can go to the security tab for the repository -> Dependabot alerts -> Enable Dependabot Alerts and enable Dependabot dependency graph. Then you can do to insights -> Dependency Graph -> Dependabot -> Recent job updates and click `Check for updates`
