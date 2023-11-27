# workflow-builder

**TBD**

## Prerequisites
* Configure GitHub user in Backstage
* Configure Backstage with Orchestrator plugin
* Add the following configuration under the `catalog` component:
```yaml
  rules:
    - allow: [Component, System, Group, Resource, Location, Template, API, User, Domain]
  locations:
    # Register System and Group entities for the Orchestrator
    - type: url
      target: https://github.com/dmartinol/workflow-gpt/blob/main/entities/workflow-resources.yaml
```

```bash
BACKSTAGE_BACKEND_URL=http://localhost:7007
```

```bash
mvn quarkus:dev
```
```bash
curl -v -H "Content-Type: application/json" -X POST http://localhost:8080/workflow-builder -d @input.json
```

```bash
> cat input.json
{
  "orgName": "YOUR_GITHUB_ID",
  "repoName": "test-swf-builder",
  "owner": "janus-orchestrator",
  "system": "janus-orchestrator",
  "groupId": "com.redhat.parodos",
  "artifactId": "test-swf-builder",
  "version": "1.0.0-SNAPSHOT"
}
```