# cloudtrail-iam-investigations

## Hypothesis
Attaching IAM policies to users represents a privilege escalation event that must be audited through CloudTrail write events.

## Evidence to collect
- CloudTrail Event history
- EventName: AttachUserPolicy
- EventSource: iam.amazonaws.com
- userIdentity
- requestParameters.userName
- requestParameters.policyArn

## Evidence
- EventName: AttachUserPolicy
- EventSource: iam.amazonaws.com
- Actor: Root account
- Target user: juan-admin
- Policy attached: IAMUserChangePassword
