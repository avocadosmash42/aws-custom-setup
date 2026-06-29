## AWS Custom Setup ##

Just some helper files and resources.  To help setup the accounts akin to the ones with best-practices that I've had the privilege to learn from workplaces.

### IAM ###
* ``gh-cdk-perms-boundary.yaml`` - opens up and controls some AWS resources for IAM manipulation.  Controlling costs.

* ``trust-relatipnships.json`` - When bootstrapping a Region or a new Region, some of the default IAM Roles' Trust Relationships need modifying.  This will allow for easier ops with GitHub Actions.  For now, this is just a copied template.  Add the bits that are missing/tailor to your account number.  At the time of writing, could not find a Cloudformation parameter to enter this.

Needs applying to:
* cdk-hnb659fds-cfn-deploy-role-{Account_ID}-{Region}
* cdk-hnb659fds-cfn-exec-role-{Account_ID}-{Region}
* cdk-hnb659fds-cfn-file-publishing-role-{Account_ID}-{Region}
* cdk-hnb659fds-cfn-image-punlishing-role-{Account_ID}-{Region}
* cdk-hnb659fds-cfn-lookup-role-{Account_ID}-{Region}

This needs to be repeated per Region of intended use.

* ``AllBillingAndCostAccess.yaml`` - By default, child accounts (under root) are limited to Billing and Cost-related resources/tools.  This allows easier admin within the child account.  Assign to your IAM User once deployed.

Remember, where applicable: \
```aws cloudformation deploy --template-file /path_to_template/template.json --stack-name my-new-stack --region```