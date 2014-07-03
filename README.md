project-server-setup
====================

Configuration for setting up development and cloud servers for a new internal or client project at Cloudspace.  The repo also contains initial Capistrano deploy setups and a dev environment Vagrantfile you can use as a starting point.

# Basic config

Copy these files and directory into the root of your project and customize as needed.

# Launching AWS Boxes

1. Login to the EC2 console with your Amazon IAM account using the IAM login for your client.  (For cloudspace use https://cloudspace.signin.aws.amazon.com/console) If you don't have an Amazon IAM user setup, request one from DevOps.
2. Click "EC2"
3. Click "Launch Instance"
4. Find the AMI for your project in my amis or community amis.  Usually you will use one of the default builds from https://github.com/cloudspace-devops/packer-image-scripts to start; then create a custom build using packer as needed.  If you are sure you can use ami-c8cf3ba0.
5. Scroll down, select instance size (m1.small is a good start, then move to c3.large as needed) and click "Next: Configure Instance Details"
6. Normally you can just leave the defaults and click "Next: Add Storage."  If you need to set any keys or system jobs, especially with CoreOS, use cloud-init in the User Data field under Advanced Details.  See http://cloudinit.readthedocs.org/en/latest/topics/examples.html for more information.
7. Select your storage site (usually 8GB to start) & volume type (General Purpose SSD is the same price as Magnetic so you should usually select GPSSD), and click "Next: Tag Instance."
8. Name your instance and click "Next: Configure Security Group"
9. Create or select your security group.  For most Cloudspace projects, select the existing "default" group. Click "Review and Launch."
10. Scroll down and click "Launch."
11. Choose an existing keypair or make a new one.  For most Cloudspace projects, select the "ops" key pair and check the box acknowledging you have access to the key.
12. Click "Launch Instances."
13. Scroll down and click "View Instances."
14. Grab the public ip of your launched container and toss that in the .env file under the environment you are setting up.
