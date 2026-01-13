# Case 01 – AWS CloudTrail IAM CreateUser Investigation

## Executive Summary
A security investigation was conducted to validate and audit privileged IAM activity using AWS CloudTrail. The case focuses on detecting and analyzing a CreateUser event performed by the AWS root account.

This investigation demonstrates how CloudTrail captures IAM write-level management events and supports accountability and traceability for administrative actions.

## Detection Source
AWS CloudTrail – Event History (Management Events)

## Environment
- AWS Account
- AWS IAM
- AWS CloudTrail

## Timeline
- IAM user creation detected via CloudTrail
- Root account identified as the actor
- IAM user protected with MFA after creation

## Event Details
- Event Name: CreateUser
- Event Source: iam.amazonaws.com
- Event Type: Write (Management Event)
- Actor: Root Account
- Target Resource: IAM User (juan-admin)

## Analysis
The CloudTrail log confirms that a privileged IAM action was executed by the root account. The event includes full metadata, request parameters, and affected resources, enabling reliable auditing of administrative activity.

## Risk Assessment
Creating IAM users using the root account represents a medium-risk administrative action. Without audit logging, such actions could result in unauthorized access or privilege abuse.

## Mitigation
- CloudTrail enabled for management events
- Logs retained for forensic review
- MFA enabled on the created IAM user

## Evidence
See redacted CloudTrail event evidence:
- evidence-cloudtrail-createuser.png

## Skills Demonstrated
- AWS CloudTrail log analysis
- IAM security auditing
- Privileged access monitoring
- Security documentation
