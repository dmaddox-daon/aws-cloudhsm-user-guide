# Lost Connection to the Cluster<a name="troubleshooting-lost-connection"></a>

When you [configured the AWS CloudHSM client](install-and-configure-client-linux.md#edit-client-configuration), you provided the IP address of the first HSM in your cluster\. This IP address is saved in the configuration file for the AWS CloudHSM client\. When the client starts, it tries to connect to this IP address\. If it can't—for example, because the HSM failed or you deleted it—you might see errors like the following:

```
LIQUIDSECURITY: Daemon socket connection error
```

```
LIQUIDSECURITY: Invalid Operation
```

To resolve these errors, update the configuration file with the IP address of an active, reachable HSM in the cluster\.

**To update the configuration file for the AWS CloudHSM client**

1. Use one of the following ways to find the IP address of an active HSM in your cluster\.
   + View the **HSMs** tab on the cluster details page in the [AWS CloudHSM console](https://console.aws.amazon.com/cloudhsm/home)\.
   + Use the AWS Command Line Interface \(AWS CLI\) to issue the [http://docs.aws.amazon.com/cli/latest/reference/cloudhsmv2/describe-clusters.html](http://docs.aws.amazon.com/cli/latest/reference/cloudhsmv2/describe-clusters.html) command\.

   You need this IP address in a subsequent step\.

1. Use the following command to stop the client\.

------
#### [ Amazon Linux ]

   ```
   $ sudo stop cloudhsm-client
   ```

------
#### [ Amazon Linux 2 ]

   ```
   $ sudo service cloudhsm-client stop
   ```

------
#### [ CentOS 6 ]

   ```
   $ sudo stop cloudhsm-client
   ```

------
#### [ CentOS 7 ]

   ```
   $ sudo service cloudhsm-client stop
   ```

------
#### [ RHEL 6 ]

   ```
   $ sudo stop cloudhsm-client
   ```

------
#### [ RHEL 7 ]

   ```
   $ sudo service cloudhsm-client stop
   ```

------
#### [ Ubuntu 16\.04 LTS ]

   ```
   $ sudo service cloudhsm-client stop
   ```

------
#### [ Windows ]

   You can use **Ctrl**\+**C** to stop the client\.

------

1. Use the following command to update the client's configuration file, providing the IP address that you found in a previous step\.

   ```
   $ sudo /opt/cloudhsm/bin/configure -a <IP address>
   ```

1. Use the following command to start the client\.

------
#### [ Amazon Linux ]

   ```
   $ sudo start cloudhsm-client
   ```

------
#### [ Amazon Linux 2 ]

   ```
   $ sudo service cloudhsm-client start
   ```

------
#### [ CentOS 6 ]

   ```
   $ sudo start cloudhsm-client
   ```

------
#### [ CentOS 7 ]

   ```
   $ sudo service cloudhsm-client start
   ```

------
#### [ RHEL 6 ]

   ```
   $ sudo start cloudhsm-client
   ```

------
#### [ RHEL 7 ]

   ```
   $ sudo service cloudhsm-client start
   ```

------
#### [ Ubuntu 16\.04 LTS ]

   ```
   $ sudo service cloudhsm-client start
   ```

------
#### [ Windows ]

   ```
   C:\Program Files\Amazon\CloudHSM>start "cloudhsm_client" cloudhsm_client.exe C:\ProgramData\Amazon\CloudHSM\data\cloudhsm_client.cfg
   ```

------