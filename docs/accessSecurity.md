# Access Security

The solution implements access seurity. It is not possible to access any data or any information from the system without an authenticated request. To ensure this TrustSource uses a proxy, which is requesting and verifying every request, before executing it. There are two possible Authentication providers:
- TrustSource
- External Identity Provider

## TrustSource as Identity Provider

To access TrustSource, a username / password combination has to be provided. To keep this confidential is a key repsonsibility of every user. 

We recommend using a 3rd party identity provider that supports multi factor authenticiation. 

### Adding new users

While using TrustSource as the Identity Provider you have the option to invite users to join your account. These users are allowed to be from any organisation. It is in the responsibility of the account owner (role Account Admins) to invite only trustworthy users. 

New users will receive an invitation by email with a link they need to activate their access. in the next step, they require to set a password. A forgotten password can be reset anytime using the forgotten password link. Thus, if a user from an insecure domain is invited, a malicious suspect might take over the mail account and use the reset function to gain access.

However, it is also in the repsonsibility of the account owner to remove access for users when it is not longer required.

### Assigning Roles

Every user requires one or more roles. Depending on the roles, the rights are set. A detailed overview can be found in the [TrustSource Knowledgebase](https://support.trustsource.io/). It is in the responsibility of the account owner to manage the rights for each user. We recommend to favour a restrictive approach and review the need of roles on a regular basis.

### Deleting users

TrustSource keeps audit logs of all events users initiate. These logs contain the user ID. For better readability the visualization uses the real user name for display. However, it is always possible to remove a user's name using the >Right to be Forgotten (RTBF)< button. This will delete the name information but keep the then nameless ID.

Deleting the user will close the account. No more access will be possible for that user. The audit logs will keep showing the name.  

## 3rd Party Identity Provider

Depending on your subscription, you may want to add an external Identity Provider. This could be either your corporate Active Directory, Github or Apple. The benefit of these providers is for example the support for One Time Password (OTP) authentication, but also more comfort in managing users. Given a user leaves the company, your HR will take care to remove him from the corproate directory. If you use this as Identity Provider, the user will immediately loose access to TrustSource as well. If you decide for manual user management, you will have to provide a routine - either manual or automated - to ensure the removal in TrustSource will take place in time. 

In addition these providers may also provide an OID token containing claims concerning their roles in TrustSource. In Active Directory this typically is organized through memebership of Security Groups. Thus you would assign every user to a set of security groups, according to the roles they shall have in TrustSource ([see role mapping](https://support.trustsource.io)).

To setup a 3rd party provider, you will require a user with the role "Account Admin". The first user creating an account automatically will own this a role. The role allows to invite/add new users - see [Account Admin Role](!https://support.trustsource.io/) in the online help - as well as arrange account settings. 

You may check your roles by hovering under your profile icon in the upper left corner. If the correct role is not set, you will need to contact an Account Admin to set the role. PLEASE NOTE: It is not possible to modify your own role! You will need to create a second Account Admin to change your role settings. 

It is in **your repsonsibility** to assign roles with caution. If users have access or manipulate content within the application, TrustSource may not help. Our employees **do not have access to your account data**. However, all access will be logged in the access log, which is visible to Account Admin roles.  

It is in **your responsibility** to setup and maintain the 3rd party provider connection details. If you need assistance, look at [our knowledge base](!https://support.trustsource.io/AD_integration) for help or contact support. 

### Enforce 3rd party login

If you setup a 3rd party provider, the authentictaion by the application still remains active. This will allow users that are available _only_ within TrustSource also to access the service. This might be a good solution in case you want external partners, which you do not want to manage / add to your internal AD to access the service. However, it bears also the risk, that these useres are not addressed with your user access management procedures, e.g. regular account review.

However, you may encforce that only accounts existing in your AD will be allowed to access the service. This will automatically prevent all users from loging in using the _local_ authentication. To do so, a known user with Account Admin role needs to create a ticket at TrustSource Support to initiated / deactivate IDM enforcement. PLEASE BE PREPARED: Our support will validate the origin of the request. 

### Configure SMTP

TrustSource is configured to send all communications using `@trustsource.io` addresses. While using a 3rd party provider, you may prefer to use your own server for sending authentication and password reset emails. This can be done in the ACCOUNT ADMIN > SMTP section. As long as the server is not set up, all mails will go through the TrustSource mail server. See [our knowledge base](!https://support.trustsource.io/AD_integration) for more details on how to setup the integration.

It is in **your responsibility** to setup and maintain this configuration. 
