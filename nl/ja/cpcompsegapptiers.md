---

copyright:

  years: 1994, 2019

lastupdated: "2019-02-25"

keywords: available hardware firewalls, application tiers, web servers, securing environment, activating firewall 

subcollection: customer-portal

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:tip: .tip}
{:screen: .screen}
{:new_window: target="_blank"}

# 環境の保護と拡大縮小
{: #cp_compsegapptierssecscal}

アプリケーションをホスティングするときにシステム管理者が考慮する必要のある最も重要な 2 つの観点は、アプリケーションのセキュリティーおよびスケーラビリティーです。
{:shortdesc}

## ファイアウォールを使用したシステムの保護
{: #cp_bpsecuresystem}

使用可能なハードウェア・ファイアウォールを使用して、デバイスが常にセキュアであることを確実にします。 ルールが適切に確立されていれば、ダウン時間なしにオンデマンドでハードウェア・ファイアウォールをプロビジョンして、不要なアクティビティーからサーバーを保護することができます。

ファイアウォールは、すべてのデバイスに対するアドオン・サービスであり、実効性を確保するには手動で構成して使用可能にする必要があります。 不要なポートをロックし、パブリック・ポートを使用不可にすることによって、プライベート・ネットワーク・ベースのシステムで、システムへの外部からのアクセス可能性をさらに管理できるようになります。 カスタマー・ポータルでの定期的な脆弱点スキャンによって未処理または不明のセキュリティー・リスクが特定され、リスクを素早く軽減することができます。

ファイアウォールを注文した後は、ファイアウォールを有効にし、ルールを設定する必要があります。

### ファイアウォールのアクティブ化
{: #cp_bpnofirewalbypass}

システムの保護はファイアウォールの購入で始まりますが、ファイアウォールの購入だけでは保護されません。 ファイアウォールは、プロビジョンされた後は**バイパス・モード**であり、ルールは設定されていません。 ファイアウォールを稼働中にするには、望まないアクティビティーのブロックをファイアウォールが開始できるように、ルールを作成し、ファイアウォールをアクティブ化する必要があります。


## アプリケーション層のセグメント化による環境の保護
{: #cp_copmsecenv}

論理アプリケーション層を物理インフラストラクチャー層にセグメント化することによって、より強力なセキュリティーをアクセス制御リスト (ACL) の使用を介して提供できます。 アプリケーション層をセグメント化するときに考慮する必要のある最も重要な要素の 1 つは、どこからのどのトラフィックが各層にアクセスするのを許可するのかということです。 この情報を決定するには、アプリケーションが基本的にどのように動作するのかについて、および、ユーザーが要求するコンテンツを提供するためにどのサービスとどのサービスが互いに依存しているのかについて検討してください。

例えば、2 つの層からなるアプリケーションが Web フロントエンドとデータベース・バックエンドに依存していると想定してみましょう。 このアプリケーションのために、ポート 80 および 443 (SSL を使用している場合) が Web サーバー上でインターネットに対して開いているようにします。 また、インターネットに対するすべてのポートをロックし、{{site.data.keyword.BluSoftlayer_full}} インフラストラクチャーのプライベート・ネットワークを使用することによって VPN を介してサーバーを管理します。 さらに、データベース・サーバー上のパブリック IP アドレスをアンバインドし、そこへのすべてのトラフィックをポート 1433 (MSSQL の場合) またはポート 3306 ({{site.data.keyword.mysql}} の場合) を介して Web サーバーから渡すようにします。 データベース・サーバーを Web サーバーと同じようにプライベート・ネットワークを介して管理します。 また、データベース・サーバー上にソフトウェア・ファイアウォールをセットアップして Web サーバーから特定のデータベース・ポートへのすべてのトラフィックをロックします。

このように環境をセットアップすることによって、インターネットからの SSH または RDP へのアクセスが防止されること、およびデータベースへのすべてのインターネット・トラフィックが無効になることで、セキュリティーが強化されます。 Web 層とデータベース層の間の ACL を作成すると、Web サーバーへの不正アクセスがあった場合にデータベースへの不正アクセスがより困難になります。

## アプリケーション層のセグメント化による環境の拡大縮小
{: #cp_copmscaleenv}

多層環境では、垂直ホスト・アーキテクチャーまたは単一ホスト・アーキテクチャーに比べて拡大縮小も簡単です。 より多くのリソースを必要とするサービス用に拡大を許可することによって、アプリケーションを簡単にスケールアウトできるように多層環境をセットアップできます。 例えば、上記のシナリオでは、Web サーバーが酷使されている場合、別の Web サーバーをデプロイすることができます。 その後、サイトまたはアプリケーションのデータを複製し、2 つの Web サーバーが Web 負荷を分担できるように、負荷を平衡させるかラウンドロビン DNS をセットアップすることができます。 ラウンドロビン DNS または負荷の平衡化は、複数の Web サーバーが着信要求に応答することを可能にすることによって、環境での高可用性を実現します。 1 つのサーバーがダウンしても、別のノードがユーザー要求の処理に使用可能です。

データベースをスケールアウトすることもできます。 例えば、{{site.data.keyword.mysql}} データベースの場合、1 つのオプションは、別の物理サーバーをセットアップし、それを {{site.data.keyword.mysql}} 複製セットアップで従属として使用することです。 データベース書き込みのすべてをマスターにセグメントし、すべての読み取りを 1 つ以上の従属にセグメントすることで、より多くの負荷をサポートするようにデータベースをスケールアウトできます。 このタイプのセットアップでは、従属の状況をマスターに変更できるため、ある程度の高可用性も追加されます。 これにより、{{site.data.keyword.mysql}} マスター・ノードがダウンした場合、読み取りと書き込みの両方のトラフィックを従属に送付するようにできます。

上記は、環境の保護および拡大縮小を行うための多くの方法のうちのいくつかを示したものにすぎません。 セキュリティーおよびスケーラビリティーの観点での環境の最適な設計方法に関して質問または懸案事項がある場合は、{{site.data.keyword.BluSoftlayer_notm}} インフラストラクチャーの営業担当エンジニアリング・チームがご支援可能です。
