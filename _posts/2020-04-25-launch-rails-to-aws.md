---
layout: post
title:  "Launching a rails application on AWS"
categories: rails
date:   2020-04-25 19:00:00 +0700
permalink: launch-rails-to-aws/
---
Here's the steps to launch an empty Rails app to AWS. By the end of the steps you should see Rails home page on the domain of your compute instance in aws.

# Launch an EC2 instance
AWS EC2 is a virtual server instance in which you'll deploy your Rails app, to launch it follow this steps:

1. Logged in to your aws console, go to console.aws.amazon.com/ec2/
2. Launch an EC2 instance. Choose ubuntu server as AMI (Amazon Machine Image)
3. Choose a key pair to access the new instance, if this is your first time of creating a new EC2 instance, just select "Create a new key pair" and klik "Download Key Pair".You'll get an `instance-name.pem` key to be used to connect to your new EC2 later, download and save it to the computer.
4. Wait until the new EC2 instance is created
5. After it's created, go to your EC2 dashboard and click "Connect" it will give you guidance about how to connect to your new instance. Simply said, you need to use the key you get from step-3 to connect to your new instance via SSH. It will looked to something similar to this: "ssh -i "instance-name.pem" ubuntu@ec2-18-144-71-537.ap-southeast-1.compute.amazonaws.com", follow the steps and connect to your new EC2 instance via ssh.

# Install ruby
After you successfully logged in to your newly created EC2 instance via ssh, now you can install ruby in order to run your rails app. 

## Install ruby via debian package manager (apt-get)
You can install ruby via debian repository, but usually the version of ruby that will be available in the repository will not be the latest. To check the version of ruby that you will install, run

```
sudo apt-cache policy ruby
```

if the version of ruby match with one you needed, then you can just install it with:

```
sudo apt-get install ruby
```

but if the version doesn't match what you need, you should install it via ruby version manager. Continue to the next section.

## Install rbenv
rbenv is a version manager for ruby. To install it, follow this steps:

Install the necessary package to compile ruby:

```
$ sudo apt install autoconf bison build-essential libssl-dev libyaml-dev libreadline6-dev zlib1g-dev libncurses5-dev libffi-dev libgdbm5 libgdbm-dev 
```

Clone rbenv to ~/.rbenv

```
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
```
 
add rbenv/bin into the front of your PATH

```
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
$ echo 'eval "$(rbenv init -)"' >> ~/.bashrc
```

Install ruby-build plugin

```
$ git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
```

Now you should be able to see the available ruby version to be installed, run:

```
$ rbenv install -l
```

The output of that command should show you the list of ruby versions that you can install.

Now, install ruby. For example, I want to install ruby version 2.6.6

```
$ rbenv install 2.6.6
```

Set it as our default version of ruby:

```
$ rbenv global 2.5.1
```

# Install bundler
At this point you should have ruby installed in your EC2. Now install bundler:

```
$ gem install bundler
```

# Install nginx
To install nginx, just run:

```
sudo apt-get install nginx
```

to see if you're successfully install nginx, run:

```
curl localhost
```

you should see html response from nginx.

# Enable HTTPS traffic to your EC2 instance
To allow your EC2 instance receive traffic from the internet, you need to add HTTPS as an allowed inbound traffic in
your **Security Group**.

To do that:

1. Open your EC2 dashboard, click on Instances menu. You will see the list of your EC2 instance in the table.
2. On the line of your EC2 instance scroll to right until you see column `Security Groups`, in my case it will contain value of 'launch-wizard-1'.
   Click it and you will be redirected to Security Groups dashboard.
3. On the security group table, click the link on the ID column of security group that has name matching with the Security Group of your EC2 (in my case 'launch-wizard-1'
4. You will see three tabs on the bottom half on the dashboard showing: Inbound rules, Outbound rules, and Tags. Click on Inbound rules
5. Click 'Edit inbound rules', you will be redirected to Edit inbound rules dashboard, click 'Add Rule' and choose HTTPS. Repeat the process to add HTTP.
6. Click save rules

Now your EC2 instance will receive the internet traffic coming into port 80 (http) and 443 (https).
If you enter the domain of your EC2 instance in browser with http (instead of https) you should now see an nginx welcome page.

# Setup SSL certificate to your domain with Let's Encrypt
[Let's encrypt](https://letsencrypt.org/getting-started/) is a Certificate Authority that gives you a free certificate.
[Certbot](https://certbot.eff.org/) is a client that can automate the process to obtains this certificate.
Visit the website and input your system stack.
If you use the same stack with this tutorial (ubuntu and nginx) then you should be directed to [this page](https://certbot.eff.org/lets-encrypt/ubuntubionic-nginx)

Follow the instruction to install the certbot client and run the certbot command to automatically get the certificate.

# Upload your Rails code to EC2
It's up to you how you upload the code to your EC2 instance, I myself prefer to use deployment automation by using
[Capistrano](https://capistranorb.com/).
