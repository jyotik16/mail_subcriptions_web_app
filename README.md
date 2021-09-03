# Mail Subscriptions Web App

#EndPoints

@/subscription/create

Takes an email-address in the request body and subscribes the provided email-address to the daily mail subscription service
If subscribed at 11:47pm, the user will recieve a mail every day at the same time i.e 11:47pm via dynamic cron expressions
If Already subscribed, EmailAlreadyRegisteredException is thrown
A Quartz Trigger is created with the email-address being the identity (so that same email-address can not be subscribed twice) and added to a Quartz job responsible for sending the daily mail when the trigger is fired.

@/subscription/status/{emailId}

Tells if the provided emailId is registered to the daily mail subsription service i.e a trigger with identity same as the email address is scheduled with the created Quartz job

@/subscription/cancel/{emailId}

Unsubscribes the provided emailId from daily mail subscription service if it's registered i.e unschedules the trigger with identity same as the email address from the created Quartz Job
