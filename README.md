aws-cfn-filesystem
==================

AWS CloudFormation stacks for file systems

[![Lint](https://github.com/dceoy/aws-cfn-filesystem/actions/workflows/lint.yml/badge.svg)](https://github.com/dceoy/aws-cfn-filesystem/actions/workflows/lint.yml)

Installation
------------

1.  Check out the repository.

    ```sh
    $ git clone --recurse-submodules git@github.com:dceoy/aws-cfn-filesystem.git
    $ cd aws-cfn-filesystem
    ```

2.  Install [Rain](https://github.com/aws-cloudformation/rain) and set `~/.aws/config` and `~/.aws/credentials`.

3.  Deploy stacks for VPC.

    ```sh
    $ rain deploy \
        --params ProjectName=fs-dev \
        aws-cfn-vpc-for-slc/vpc-private-subnets-with-gateway-endpoints.cfn.yml \
        fs-dev-vpc-private-subnets-with-gateway-endpoints
    $ rain deploy \
        --params VpcStackName=fs-dev-vpc-private-subnets-with-gateway-endpoints \
        aws-cfn-vpc-for-slc/vpc-interface-endpoints-for-ssm-and-ec2.cfn.yml \
        fs-vpc-interface-endpoints-for-ssm-and-ec2
    ```

4.  Deploy stacks for NetApp ONTAP.

    ```sh
    $ rain deploy \
        --params ProjectName=fs-dev,VpcStackName=fs-dev-vpc-private-subnets-with-gateway-endpoints \
        fsx-for-netapp-ontap.cfn.yml fs-fsx-for-netapp-ontap
    ```
