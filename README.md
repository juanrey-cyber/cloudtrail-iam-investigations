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

## Analysis
- An IAM policy attachment action was detected via CloudTrail.
- The action was initiated by the root account.
- Attaching a policy modifies the effective permissions of the target user.

## Risk Assessment
- Attaching IAM policies can result in privilege escalation.
- If misused, this action may grant users permissions beyond their intended role.
- Severity: Medium

## Mitigation and Conclusion
- IAM policy attachments should be restricted and audited.
- Root account usage for permission changes should be minimized.
- CloudTrail provides visibility into privilege escalation attempts.
- The observed action was legitimate and part of account setup.



