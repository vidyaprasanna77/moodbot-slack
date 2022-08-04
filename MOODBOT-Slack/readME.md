connecting the basic Moodbot to slack 

step 1: create a new trained bot 
step 2 : add the following lines to the    credentials.yml file
uncommand the slack and add the details of slack_channel,slack_token,slack_signing_secret.

go to the slack add a channel (eg. name:bot)To get a channel id, right click on the channel in Slack and choose Copy Link. The id will be the last component in the URL.

next step is to get values for slack_token and slack_signing_secret

1.To create the app go to Your Apps and click on Create New App.Fill the app name and select the development workspace 
2.go to OAuth & permissions and scroll down to scopes.Add the below mentioned scopes
app_mentions:read,
channels:history,
chat:write,
groups:history,
im:history,
mpim:history and
reactions:write

3.On the same page click install APP to workspace . once add , slack will show ou a Bot User Oauth access token. copy this token to the slack_token.The token should start with xoxb

step 3: head over to basic information to get the signing secret. copy the signing secret into your slack_signing_secret

this setup  will allow your bot to send messages

For receiving messages download ngrok .signup with ngrok and generate an authtoken like this
ngrok config add-authtoken 2CsLzq8Umm3W8Bn6bad8TkIuGSb_7jgLQ1H6wMRwNi1gnGoU8

To start a HTTP tunnel : type
ngrok http 5005 

1. To configure your bot to receive messages, your bot needs to be running. start by the command
    rasa run

2.Go to app home, scroll to bottom and select the checkbox for
Allow users to send Slash commands and messages from the messages tab.

3.configure the webhook by heading to Event Subscriptions and turning Enable events on.
on request tab : paste the url copied from ngrok cmd prompt eg.https://92832de0.ngrok.io/webhooks/slack/webhook

4.As a last step, you'll need to Subscribe to bot events on the same page. You'll need to add the following events:

message.channels,
message.groups,
message.im and
message.mpim.

5.save the changes . now your bot is ready to use.