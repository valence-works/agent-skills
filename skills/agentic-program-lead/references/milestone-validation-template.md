# End-to-End Milestone Validation Template

Every major milestone should have a demonstration that proves the promised outcome rather than inferring success from closed issues.

```markdown
# Milestone: <name>

## Promised outcome
<What a real user/operator/system can now accomplish.>

## Preconditions
- <starting environment/state>
- <required accounts/data/configuration>

## Actor
<Customer / operator / administrator / system>

## Demonstration
1. <Start from a realistic initial state>
2. <Perform real action>
3. ...
N. <Reach promised outcome>

## Expected evidence
- <observable UI/API/deployment/result>
- <logs/metrics/health evidence where relevant>

## Failure / recovery checks
- <important failure path if required for this milestone>

## Result
PASS | FAIL

## Evidence
<links, logs, screenshots, test run, deployment URL, workflow run, etc.>

## Follow-up
<issues created/reopened when validation fails or exposes gaps>
```

## Validation rules

- Exercise integration boundaries, not only unit-level behavior.
- Use the production-like path appropriate to the stage.
- Do not substitute compilation, mocked tests, or issue completion for the promised end-to-end behavior.
- Keep the milestone open until the demonstration passes.
