# kite-deploy

kite-deploy is one of sub-projects of kite, which is to run Linux application or kernel test on public and private cloud platform, such as VMWare ESXi, OpenStck, AWS EC2, Google Cloud Platform, Azure, etc.

kite-deploy will provide an easy way to deploy Linux guest/instance/VM on public and private cloud platform.

## deploy instance/VM on cloud

### deploy VMWare ESXi VM

    ansible-playbook -v -i inventory -e cloud_platform=esxi deploy.yaml

### deploy OpenStack instance

    ansible-playbook -v -i inventory -e cloud_platform=openstack deploy.yaml

### deploy AWS EC2 instance

    ansible-playbook -v -i inventory -e cloud_platform=aws deploy.yaml

### deploy Google Cloud Platform instance

    ansible-playbook -v -i inventory -e cloud_platform=gcp deploy.yaml

## remove instance/VM on cloud

### remove VMWare ESXi VM

    ansible-playbook -v -i inventory -e cloud_platform=esxi remove.yaml

### remove OpenStack instance

    ansible-playbook -v -i inventory -e cloud_platform=openstack remove.yaml

### remove AWS EC2 instance

    ansible-playbook -v -i inventory -e cloud_platform=aws remove.yaml

### remove Google Cloud Platform instance

    ansible-playbook -v -i inventory -e cloud_platform=gcp remove.yaml

## kite-deploy configuration

You can set these environment variables to configure to run kite-deploy

    TEST_OS           The OS to run the tests in. Currently supported values:
                          "rhel-8-0"
                          "rhel-8-1"
                          "rhel-8-2"
                          "rhel-8-3"
                          "rhel-8-4"

    ARCH              Image architecture
                          "x86_64"
                          "aarch64"

    PIPELINE_ID       CKI pipeline ID

    VSPHERE_SERVER    The vSphere server hostname or IP address

    VSPHERE_USERNAME  Username to login vSphere server

    VSPHERE_PASSWORD  Password to login vSphere server

    ESXI_HOST         ESXi host name or IP address

    ESXI_DATACENTER   Datacenter name

    ESXI_DATASTORE    Datastore name

    ESXI_FIRMWARE     ESXi firmware, bios or efi

    VAULT_PASSWORD    Password to decrypt openstack configuration file

    AWS_ACCESS_KEY    AWS access key for AWS API authentication

    AWS_SECRET_KEY    AWS secret key for AWS API authentication

    AWS_REGION        AWS region

    AWS_INSTANCE_TPYE     AWS instance type. Suggested instance types:
                          x86_64:
                              "t2.medium": Xen based instance with xen_netfront NIC
                              "t3.medium": KVM based instance with Elastic Network Adapter (ena)
                              "t3a.medium": KVM based instance with AMD CPU
                              "m4.large": Xen based instance with the Intel 82599 VF interface (SRIOV)
                              "m5.large": Mostly used instance
                              "m5dn.large": Local NVMe-based SSDs
                          ARM64:
                              "a1.large": Custom built AWS 64-bit Arm Neoverse cores
                              "m6gd.large": AWS Graviton2 Processor with 64-bit Arm Neoverse cores
                                            Local NVMe-based SSDs
                              "t4g.medium": AWS Graviton2 Processor with 64-bit Arm Neoverse cores

    GCP_PROJECT                 Google Cloud Platform project name

    GCP_SERVICE_ACCOUNT_NAME    Google Cloud Platform service account name

    GCP_SERVICE_ACCOUNT_FILE    Google Cloud Platform service account file path

    GCP_INSTANCE_TPYE           Google Cloud Platform instance type. Suggested instance types:
                                x86_64:
                                    "e2-standard-2": 2CPU/8G/Intel Skylake, Broadwell, Haswell, and AMD EPYC Rome
                                    "n2-standard-2": 2CPU/8G/Intel Cascade Lake
                                    "n2d-standard-2": 2CPU/8G/AMD EPYC Rome/nvme/AMD Secure Encrypted Virtualization
                                    "c2-standard-4": 4CPU/16G/Intel Scalable Processors (Cascade Lake)
                                    "n1-standard-2": 2CPU/7.5G/Intel Skylake, Broadwell, Haswell, Sandy Bridge, and Ivy Bridge
