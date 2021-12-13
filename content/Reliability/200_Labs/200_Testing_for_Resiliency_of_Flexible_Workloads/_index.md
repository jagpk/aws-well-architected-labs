---
title: "Level 200: Testing for Resiliency of Flexible Workloads"
menutitle: "Test Resiliency of Flexible Workloads"
description: "Deploy a sample application flexible to run on mixed purchase options and instance types. Inject faults simulating EC2 Spot Instance interruptions. These are used as part of Chaos Engineering to test workload resiliency"
date: 2020-04-24T11:16:08-04:00
chapter: false
weight: 6
hidden: false
tags:
  - test_resiliency
---
## Authors

* Seth Eliot, Principal Reliability Solutions Architect, AWS Well-Architected
* Jagdeep Phoolkumar, Senior Specialist Solutions Architect, EC2 Spot Instances

## Introduction

This purpose of this lab is to guide you through the steps to test resiliency of workloads that are flexible to run on mixed purchase options (such as On-demand and Spot Instances) and Instances with similar attributes (such as vCPU and memory). Flexible workloads allow higher chances of acquiring EC2 capacity, and to further ensure the implementation is resilient to failure such as Spot Instance interruptions. We can inject Spot Instance interruption into your application to test it's resiliency. This may be a familiar concept to companies that practice Failure Mode Engineering Analysis (FMEA). It is also a key component of Chaos Engineering, which uses such failure injection to test hypotheses about workload resiliency. One primary capability that AWS provides is the ability to test your systems at a production scale, under load.

It is not sufficient to only design for failure, you must also test to ensure that you understand how the failures like Spot Instance interruptions will cause your systems to behave. The act of conducting these tests will also give you the ability to create playbooks how to investigate failures.

In this lab, you will deploy a 2-tier Web Application, with a reverse proxy (Application Load Balancer) and  on Amazon EC2 Auto Scaling with multiple instance types and purchase options.

The skills you learn will help you build resilient workloads in alignment with the [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)

## Goals:

* Reduce fear of implementing resiliency testing by providing examples of automated testing using [AWS Fault Injection Simulator](https://aws.amazon.com/fis/) (FIS)
* Resilience testing of application running on [Auto Scaling groups with multiple instance types and purchase options](https://docs.aws.amazon.com/autoscaling/ec2/userguide/ec2-auto-scaling-mixed-instances-groups.html)
* Learn how to implement resiliency using those tests
* Learn how to execute baseline load test using [Distributed Load Testing on AWS](https://aws.amazon.com/solutions/implementations/distributed-load-testing-on-aws/)to measure performance KPIs during fault simulations
* Learn how to think about what a failure will cause within your infrastructure
* Learn how common AWS services can reduce mean time to recovery (MTTR)

## Prerequisites:

* An
[AWS Account](https://portal.aws.amazon.com/gp/aws/developer/registration/index.html) that you are able to use for testing, that is not used for production or other purposes.
* An Identity and Access Management (IAM) user or federated credentials into that account that has permissions to create Amazon Virtual Private Cloud(s) (VPCs), including subnets, security groups, internet gateways, NAT Gateways, Elastic IP Addresses, and route tables. The credentials must also be able to create the database subnet group needed for a Multi-AZ RDS instance. The credential will need permissions to create IAM Role, instance profiles, AWS Auto Scaling launch configurations, application load balancers, auto scaling group, and EC2 instances.
* An IAM user or federated credentials into that account that has permissions to deploy the deployment automation, which consists of IAM service linked roles, AWS Lambda functions, and an AWS Step Functions state machine to execute the deployment.

## Note:

This 200 level lab covers only EC2 Spot Instances interruptions injection. If you would prefer a more feature-rich 300 level lab that demonstrates EC2 failure, RDS failure, and AZ failure then see [Level 300: Testing for Resiliency of EC2, RDS, and AZ]({{% ref "/Reliability/300_Labs/300_Testing_for_Resiliency_of_EC2_RDS_and_S3" %}}).

{{% notice note %}}
NOTE: You will be billed for any applicable AWS resources used if you complete this lab that are not covered in the [AWS Free Tier](https://aws.amazon.com/free/).
{{% /notice %}}

{{< prev_next_button link_next_url="./1_prerequisite/" button_next_text="Start Lab" first_step="true" />}}

## Steps:
{{% children /%}}
