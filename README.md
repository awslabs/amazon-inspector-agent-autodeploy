# Inspector-Agent-Autodeploy
This script is designed to run in AWS Lambda and will not work elsewhere.

This is an AWS Lambda job in Python to automatically deploy Inspector agent to newly-launched EC2 instances

The job requires that the EC2 instance have the SSM (EC2 Simple System Manager) agent installed, and the agent must have a role attached with necessary SSM permissions.  For details on this, see https://docs.aws.amazon.com/ssm/latest/APIReference/Welcome.html.  The easiest way to do this is with userdata at instance launch: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/install-ssm-agent.html 

The job is triggered by a CloudWatch event every time a new instance enters the running state. The job checks to make sure that the SSM agent is running.  It then uses SSM to install and start the Inspector agent.
