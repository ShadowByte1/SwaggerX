# SwaggerX
Swagger UI Extensive Nuclei template for mass Scanning

Description: This Nuclei template is designed to detect potential Swagger UI Config URL injection vulnerabilities. The template specifically targets endpoints commonly used in API documentation systems, such as Swagger UI, and checks for the presence of the configUrl parameter, which can be exploited to inject external configuration files, leading to potential XSS attacks or other security risks.

The template is finely tuned to minimize false positives by focusing on Swagger-specific patterns, such as the presence of keywords like "swagger," "api-docs," or versioned paths typically associated with Swagger UI setups.

Usage:

# Basic Scan: To run a basic scan against a list of domains:
```
cat domains.txt | nuclei -t swagger.yaml
```

# Single URL Scan: To scan a single URL:

```
echo "https://example.com" | nuclei -t swagger.yaml
```

# Template Structure:

Matchers: The template employs several matchers, including regex patterns that are specific to Swagger UI paths and versioning.
Attack Vector: The injection vector is the configUrl parameter, a known entry point for injecting external configuration URLs.
Example Outputs:

[swagger-ui-config-url-injection] [http] [low] https://example.com/v0.10/index.html?configUrl=https://xss.smarpo.com/test.json
This template is useful for security researchers and penetration testers looking to identify misconfigured or vulnerable Swagger UI instances in web applications.

# Notes:

Please note it may produce False Positives however if it does alert with the Config but does not execute please try with the other XSS Swagger Url
