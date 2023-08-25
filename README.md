aws-cfn-netapp-ontap
====================

AWS CloudFormation stacks for NetApp ONTAP

[![Lint](https://github.com/dceoy/aws-cfn-netapp-ontap/actions/workflows/lint.yml/badge.svg)](https://github.com/dceoy/aws-cfn-netapp-ontap/actions/workflows/lint.yml)

Installation
------------

1.  Check out the repository.

    ```sh
    $ git clone --recurse-submodules git@github.com:dceoy/aws-cfn-netapp-ontap.git
    $ cd aws-cfn-netapp-ontap
    ```

2.  Install [Rain](https://github.com/aws-cloudformation/rain) and set `~/.aws/config` and `~/.aws/credentials`.

3.  Deploy stacks for VPC.

    ```sh
    $ rain deploy \
        --params ProjectName=nao-dev \
        aws-cfn-vpc-for-slc/vpc-private-subnets-with-gateway-endpoints.cfn.yml \
        nao-dev-vpc-private-subnets-with-gateway-endpoints
    ```

4.  Deploy stacks for EFS.

    ```sh
    $ rain deploy \
        --params ProjectName=nao-dev,VpcStackName=nao-dev-vpc-private-subnets-with-gateway-endpoints \
        fsx-for-netapp-ontap.cfn.yml nao-fsx-for-netapp-ontap
    ```
