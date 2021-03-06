---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-06"

keywords: IBM Cloud, Activity Tracker, download events

subcollection: cloud-activity-tracker

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}


# イベントのダウンロード
{: #downloading_events}

イベントをローカル・ファイルにダウンロードすることができます。 イベントのダウンロードは、1 つのセッションのコンテキスト内で行います。 どのイベントがダウンロードされるのかはセッションによって指定されます。 ダウンロードが完了した後、セッションを削除する必要があります。
{:shortdesc}

イベントをローカル・ファイルにダウンロードするには、以下のステップを実行します。

## ステップ 1: {{site.data.keyword.cloud_notm}} にログインする
{: #prereq}

{{site.data.keyword.cloud_notm}} にログインします。 以下のステップを実行します。

1. [ibmcloud login](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_login) コマンドを実行して、{{site.data.keyword.cloud_notm}} にログインします。
2. [ibmcloud target](/docs/cli/reference/ibmcloud?topic=cloud-cli-ibmcloud_cli#ibmcloud_target) コマンドを実行して、{{site.data.keyword.cloudaccesstrailshort}} サービスをプロビジョンする組織とスペースを設定します。

**注:** {{site.data.keyword.cloudaccesstrailshort}} がプロビジョンされる組織とスペースを設定してください。

## ステップ 2: 使用可能なイベントを識別する
{: #step2}

`ibmcloud at status` コマンドを使用して、スペース・ドメイン内の使用可能なイベントに関する情報を表示します。

* スペース・ドメイン内のイベントに関する情報を取得するには、コマンド `ibmcloud at status` を実行します。
* アカウント・ドメイン内のイベントに関する情報を取得するには、オプション `-a` を指定してコマンド `ibmcloud at status` を実行します。

詳しくは、[イベント情報の表示](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-viewing_event_status#viewing_event_status)を参照してください。
  


## ステップ 3: セッションを作成する
{: #step3}

ダウンロードに使用可能なイベント・データのスコープを定義するため、および、ダウンロードの状況を保持するために、セッションが必要です。 

セッションを作成するには、コマンド `ibmcloud at session create` を使用します。 デフォルトでは、セッションには最近 2 週間のデータが含まれます。  オプションで、セッション作成時に開始日と終了日を指定することができ、それによって、イベントの期間、特定の時刻、およびスコープを指定することができます。 

**注:** 

* 開始日と終了日を指定すると、セッションはそれらの日付の間 (開始日と終了日を含む) のイベントへのアクセスを提供します。 
* セッション当たり 2 週間を超えるデータをダウンロードすることはできません。 したがって、期間は 2 週間未満でなければなりません。
* 1 つのスペース・ドメインのイベントをダウンロードするか、または、1 つの地域内のアカウント・ドメインのイベントをダウンロードできます。

特定の 1 日のイベントをダウンロードするために使用されるセッションを作成するには、次のコマンドを実行します。

```
ibmcloud at session create -s 2017-07-25 -e 2017-07-25
```
{: codeblock}

セッションは、以下の情報を返します。

* ダウンロードされる日付範囲。
* アカウント全体での使用可能なイベントを含めるのか、現行スペースでの使用可能なイベントのみを含めるのかについての情報。 デフォルトでは、ログインしているスペースのイベントが取得されます。
* イベントをダウンロードするために必要なセッション ID。
* セッションを作成するユーザー ID。

以下に例を示します。

```
$ ibmcloud at session create 
+--------------+-------------------------------------------+
| Name         | Value                                     |
+--------------+-------------------------------------------+
| username     | xxx@yyy.com                               |
| create-time  | 2017-07-25T10:29:28.541092735Z            |
| access-time  | 2017-07-25T10:29:28.541092735Z            |
| date-range   | {"End":"2017-07-25","Start":"2017-07-25"} |
| type-account | {"Type":"ActivityTracker"}                |
| id           | 32c657c5-31c0-4a3c-a139-b380871c737a      |
| space        | 66fe4565-abab-46c9-cdcd-qf4565342345      |
+--------------+-------------------------------------------+
```
{: screen}

**ヒント:** アクティブ・セッションのリストを表示するには、コマンド `ibmcloud at session list` を実行します。

以下に例を示します。

```
ibmcloud at session list
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| Id                                   | Space                                |Username             | Create-time                    | Access-time                    |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
| 32c657c5-31c0-4a3c-a139-b380871c737a | 66fe4565-abab-46c9-cdcd-qf4565342345 |xxx@yyy.com          | 2017-07-25T10:29:28.541092735Z | 2017-07-25T10:29:28.541092735Z |
+--------------------------------------+--------------------------------------+---------------------+--------------------------------+--------------------------------+
```
{: screen} 


## ステップ 4: イベントをファイルにダウンロードする
{: #step4}

セッション・パラメーターで指定されたイベントをダウンロードするには、次のコマンドを実行します。

```
ibmcloud at download -o Events_File_Name Session_ID
```
{: codeblock}

ここで、

* Events_File_Name は、出力ファイルの名前です。
* Session_ID は、セッションの GUID です。 この値は前のステップで取得します。 **Id** フィールドの値を使用します。

以下に例を示します。

```
ibmcloud at download -o Events_File_Name.log 32c657c5-31c0-4a3c-a139-b380871c737a
 29.89 KiB / 12.19 KiB [================================] 245.14% 9.73 MiB/s 0s
Download completed successfully
```
{: screen}

進行状況表示は、イベントがダウンロードされるに従って 0% から 100% に進んでいきます。

**注:** 

* ダウンロードされたデータのフォーマットは、圧縮 JSON です。 例えば、Linux システムでイベントをダウンロードする場合、.gz ファイルを unzip し、それを開いて JSON フォーマットのデータを表示します。 
* 圧縮 JSON は、ElasticSearch または Logstash による取り込みに適しています。 例えば、Linux システムで作業していて、-o が指定されていない場合、データは stdout に出力されるので、自分の Elastic スタックに直接パイプすることができます。
* JSON を構文解析できる任意のプログラムでデータを処理することもできます。 

## ステップ 4: セッションを削除する

ダウンロードが完了した後、`ibmcloud at session delete` コマンドを使用してセッションを削除する必要があります。 

セッションを削除するには、次のコマンドを実行します。

```
ibmcloud at session delete Session_ID
```
{: codeblock}

ここで、Session_ID は、前のステップで作成したセッションの GUID です。 **Id** フィールドの値を使用します。

以下に例を示します。

```
ibmcloud at session delete 32c657c5-31c0-4a3c-a139-b380871c737a
+---------+------------------------+
| Name    | Value                  |
+---------+------------------------+
| message | Delete session success |
+---------+------------------------+
```
{: screen}




