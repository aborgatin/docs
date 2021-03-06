# Website on LAMP or LEMP stack

To configure a static website or dynamic website on your PHP:

* [Create a VM with a pre-installed web server](#create-vm)
* [Upload the website files](#upload-files)
* [Configure DNS](#configure-dns)

## Creating a VM with a pre-installed web server {#create-vm}

Before creating a VM:

1. Go to the Yandex.Cloud [management console](https://console.cloud.yandex.ru) and select the folder where you want to perform the operations.
1. Make sure the selected folder has a network with a subnet that the VM can be connected to. For that, on the folder page, click the tile **Yandex Virtual Private Cloud**. If the list contains a network, click on its name to see the list of subnets. If there is neither network nor subnet, [create them](../../vpc/quickstart.md).

To create a VM:

1. On the folder page of the [management console](https://console.cloud.yandex.ru), click **Create resource** and select **Virtual machine**.

1. In the **Name** field, enter the VM name.

    [!INCLUDE [name-format](../../_includes/name-format.md)]

1. Select the [availability zone](../../overview/concepts/geo-scope.md) to locate the VM in.

1. Select a public image:
   * **LEMP** for Linux, nginx, MySQL, and PHP.
   * **LAMP** for Linux, Apache, MySQL, and PHP

   For static websites, we recommend using **LEMP**.

1. In the **Computing resources** section, select the [type of core usage](../../compute/concepts/vm-types.md) (partial or full) and specify the necessary number of vCPUs and amount of RAM.

   The minimum configuration is enough for functional testing:
   * **Guaranteed vCPU share**: 5%.
   * **vCPU**: 1.
   * **RAM**: 1 GB.

1. In the **Network settings** section, select the subnet to connect the VM to when creating it.

1. Specify data required for accessing the VM.
    - Enter the username in the **Login** field.
    - In the **SSH key** field, paste the contents of the public key file.
You need to create a key pair for SSH connection yourself. To generate keys, use third-party tools, such as `ssh-keygen` utilities on Linux and macOS or [PuTTygen](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) on Windows.

1. Click **Create VM**.

Creating the VM may take several minutes. When the VM status changes to `RUNNING`, you can [upload the website files to it](#upload-files).

When a VM is being created, it is assigned an IP address and hostname (FQDN). This data can be used for SSH access.

#### See also

- [[!TITLE]](../../compute/operations/vm-control/vm-connect-ssh.md)

## Uploading website files {#upload-files}

[!INCLUDE [upload-files](../_solutions_includes/upload-web-site-files.md)]

## Configuring DNS {#configure-dns}

The domain name that you want to use for your website must be associated with the created VM.

[!INCLUDE [configure-a-record-and-cname](../_solutions_includes/configure-a-record-and-cname.md)]

