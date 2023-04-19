AWS provides up to 5 Elastic IP address per your account. You can increase the number.
#antipattern Using a static IP is often a poor architectural decision.
#BestPractice Use a [[DNS]] and assign that to a random public IP instead.
If you get an Elastic IP address and do not associate it - AWS will charge you.
Elastic IP is sticky across restarts of the [[EC2]] instance. You can release the IP Address only after it has been disassociated.
