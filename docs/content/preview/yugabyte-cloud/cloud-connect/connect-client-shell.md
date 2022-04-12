---
title: Connect via client shells
linkTitle: Client shell
description: Connect to Yugabyte Cloud clusters from your desktop using a client shell
headcontent:
image: /images/section_icons/deploy/enterprise.png
menu:
  preview:
    identifier: connect-client-shell
    parent: cloud-connect
    weight: 20
isTocNested: true
showAsideToc: true
---

Connect to your YugabyteDB cluster from your desktop using the YugabyteDB [ysqlsh](../../../admin/ysqlsh/) and [ycqlsh](../../../admin/ycqlsh) client shells installed on your computer. Because YugabyteDB is PostgreSQL-compatible, you can also use [psql](https://www.postgresql.org/docs/current/app-psql.html) to connect.

You can download and install the YugabyteDB Client Shell and connect to your database by following the steps below for either YSQL or YCQL.

Before you can connect using a shell, you need to add your computer to an IP allow list for the cluster. Refer to [Assign IP Allow Lists](../../cloud-secure-clusters/add-connections/).

{{< note title="Note" >}}

You must add your computer to the cluster [IP allow list](../../cloud-secure-clusters/add-connections/) before you can connect from a remote shell.

When connecting via Yugabyte Client Shell, ensure you are running the latest versions of the shells (Yugabyte Client 2.6 or later). See [How do I connect to my cluster?](../../cloud-faq/#how-do-i-connect-to-my-cluster) in the FAQ for details.

{{< /note >}}

## Connect via Client Shell

<ul class="nav nav-tabs nav-tabs-yb">
  <li >
    <a href="#ysqlsh" class="nav-link active" id="ysqlsh-tab" data-toggle="tab" role="tab" aria-controls="ysqlsh" aria-selected="true">
      <i class="icon-postgres" aria-hidden="true"></i>
      ysqlsh
    </a>
  </li>
  <li>
    <a href="#ycqlsh" class="nav-link" id="ycqlsh-tab" data-toggle="tab" role="tab" aria-controls="ycqlsh" aria-selected="false">
      <i class="icon-cassandra" aria-hidden="true"></i>
      ycqlsh
    </a>
  </li>
</ul>

<div class="tab-content">
  <div id="ysqlsh" class="tab-pane fade show active" role="tabpanel" aria-labelledby="ysqlsh-tab">
    {{% includeMarkdown "connect/ysql.md" /%}}
  </div>
  <div id="ycqlsh" class="tab-pane fade" role="tabpanel" aria-labelledby="ycqlsh-tab">
    {{% includeMarkdown "connect/ycql.md" /%}}
  </div>
</div>

## Connect using psql

To connect using [psql](https://www.postgresql.org/docs/current/app-psql.html), first download the CA certificate for your cluster by clicking **Connect**, selecting **YugabyteDB Client Shell**, and clicking **Download CA Cert**. Then use the following connection string:

```sh
psql --host=<HOST_ADDRESS> --port=5433 \
--username=<DB USER> \
--dbname=yugabyte \
--set=sslmode=verify-full \
--set=sslrootcert=<ROOT_CERT_PATH>
```

Replace the following:

- `<HOST_ADDRESS>` with the value for host as shown on the **Settings** tab for your cluster.
- `<DB USER>` with your database username.
- `yugabyte` with the database name, if you're connecting to a database other than the default (yugabyte).
- `<ROOT_CERT_PATH>` with the path to the root certificate on your computer.

For information on using other SSL modes, refer to [SSL modes in YSQL](../../cloud-secure-clusters/cloud-authentication/#ssl-modes-in-ysql).

## Connect using third party clients

Because YugabyteDB is PostgreSQL-compatible, you can use third-party PostgreSQL clients to connect to your YugabyteDB clusters in Yugabyte Cloud.

To connect, follow the client's configuration steps for PostgreSQL, and use the following values:

- **host** as shown on the **Settings** tab for your cluster
- **port** 5433
- **username** and **password** of a user with permissions for the cluster

For detailed steps for configuring popular third party tools, see [Third party tools](../../../tools/). In that section, configuration steps are included for the following tools:

- DBeaver
- DbSchema
- pgAdmin
- SQL Workbench/J
- TablePlus
- Visual Studio Workbench

## Related information

- [ysqlsh](../../../admin/ysqlsh/) — Overview of the command line interface (CLI), syntax, and commands.
- [YSQL API](../../../api/ysql/) — Reference for supported YSQL statements, data types, functions, and operators.
- [ycqlsh](../../../admin/ycqlsh/) — Overview of the command line interface (CLI), syntax, and commands.
- [YCQL API](../../../api/ycql/) — Reference for supported YCQL statements, data types, functions, and operators.

## Next steps

- [Add database users](../../cloud-secure-clusters/add-users/)
- [Connect an application](../connect-applications/)