Amazon Pinpoint can send push notifications, in-app notifications, emails, text messages, voice messages, and messages over custom channels. It includes segmentation, campaign, and journey features that help you send the right message to the right customer at the right time over the right channel. #AWSService 

Difference from [[SES]] and [[SNS]] is that you do not manage individual messages - rather it's a full campaign with templates and journeys.
![[Pinpoint Integration.png|512]]
Fig. PinPoint Solution Architecture
- Journeys automate multi-step campaigns. Each activity in a journey is either an action (such as sending an email), a time-based wait, splitting the journey segment based on customer action (such as opening an email vs not opening the email) or enforcing a holdout.