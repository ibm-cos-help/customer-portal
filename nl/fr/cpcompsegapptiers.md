---

copyright:

  years: 1994, 2018

lastupdated: "2018-01-11"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:tip: .tip}
{:screen: .screen}
{:new_window: target="_blank"}

# Sécurisation et évolutivité de votre environnement
{: #cp_compsegapptierssecscal}

Quand il s'agit d'héberger une application, deux des aspects les plus critiques à prendre en compte pour tout administrateur système sont la sécurité et l'évolutivité de l'application.
{:shortdesc}

## Sécurisation de vos systèmes avec des pare-feux
{: #cp_bpsecuresystem}

Les pare-feux sont des services de modules complémentaires pour tout appareil que vous devez configurer et activer manuellement afin de vous assurer qu'ils sont efficaces. Vous pouvez verrouiller les ports superflus et désactiver les ports publics pour des systèmes basés sur un réseau privé afin de gérer au plus près l'accessibilité externe à vos systèmes. L'exécution d'analyses de vulnérabilité régulières sur le portail client identifie les risques de sécurité en suspens ou inconnus afin de vous permettre de rapidement atténuer ces risques.

### Activation de votre pare-feu
{: #cp_bpnofirewalbypass}

L'achat d'un pare-feu constitue une première étape dans la protection de vos systèmes, mais se contenter d'acheter un pare-feu ne vous protégera pas. Une fois votre pare-feu mis à disposition, il se trouve en **mode contournement** et ne comporte aucune règle définie. Pour que votre pare-feu soit opérationnel, vous devez créer des règles et activer le pare-feu afin qu'il commence à bloquer tout activité indésirable. 


## Sécurisation de votre environnement par segmentation de vos groupes de serveurs d'application
{: #cp_copmsecenv}

En segmentant vos groupes de serveurs d'application logiques en niveaux d'infrastructure physique, vous pouvez fournir un plus grand niveau de sécurité via l'utilisation de listes de contrôle d'accès (ACL). Lorsque vous segmentez vos groupes de serveurs d'application, l'un des composants les plus critiques à prendre en compte est le trafic que vous autorisez à chaque niveau et depuis quelle origine. Pour déterminer ce point, vous devez réfléchir à la façon dont votre application fonctionne à la base, et déterminer les services qui sont basés les uns sur les autres afin de fournir à l'utilisateur final le contenu demandé. 

Par exemple, avec une application à deux niveaux reposant sur un front end Web et un back end de base de données, vous aurez besoin de vous assurer que les ports 80 et 443 (si vous utilisez SSL) sont ouverts à Internet sur vos serveurs Web. Vous voudrez probablement aussi verrouiller tous les ports Internet et gérer votre serveur par réseau privé virtuel (VPN) en utilisant le réseau privé de l'infrastructure {{site.data.keyword.BluSoftlayer_full}}. Dans ce scénario, vous voudrez probablement déconnecter l'adresse IP publique sur votre serveur de base de données et faire passer tout le trafic vers ce serveur via le port 1433 (pour MSSQL) ou le port 3306 (pour {{site.data.keyword.mysql}}) depuis votre serveur Web. Votre serveur de base de données pourrait être géré via le réseau privé tout comme votre serveur Web, et vous pourriez configurer un pare-feu logiciel sur le serveur de base de données afin de verrouiller tout le trafic depuis le serveur Web sur des ports de base de données spécifiques. 

En configurant votre environnement de cette façon, vous augmentez le niveau de sécurité en empêchant les personnes d'accéder à SSH ou RDP depuis Internet et en désactivant la totalité du trafic Internet vers votre base de données. La création de listes de contrôle d'accès entre la couche Web et la couche de base de données rend plus difficile la compromission de votre base de données si votre serveur Web venait à être compromis.

## Mise à l'échelle de votre environnement par la segmentation de vos groupes de serveurs d'application
{: #cp_copmscaleenv}

Un environnement multiniveau offre également une simplicité d'évolutivité comparativement à des architectures verticales ou à hôte unique. Vous pouvez configurer un environnement multiniveau pour faciliter l'évolutivité de votre application en autorisant l'adaptation des services ayant besoin de ressources supplémentaires. Par exemple, dans le scénario précédent, si votre serveur Web est sursollicité, il vous suffit de déployer un autre serveur Web, de répliquer le site ou les données d'application, et de configurer l'équilibrage de charge ou le round robin DNS pour activer vos deux serveurs Web de façon à fractionner votre charge Web. Le round robin DNS ou l'équilibrage de charge fournit une haute disponibilité à votre environnement en activant plusieurs serveurs Web pour répondre aux demandes entrantes. Si un seul serveur tombe en panne, un autre noeud est disponible pour gérer les demandes d'utilisateur final. 

Vous pouvez également ajuster votre base de données. Par exemple, avec une base de données {{site.data.keyword.mysql}}, une option consiste à configurer un autre serveur physique et à l'utiliser comme "esclave" dans une configuration de réplication maître/esclave {{site.data.keyword.mysql}}.  Vous pouvez segmenter toutes les opérations d'écriture de votre base de données sur le "maître" et toutes les opérations de lecture vers un ou plusieurs "esclaves" afin de mettre à l'échelle la base de données de façon à supporter davantage de charge. Ce type de configuration ajoute également un niveau de haute disponibilité en vous permettant de changer le statut d'un "esclave" en "maître" et de router vers lui le trafic de lecture et d'écriture au cas où votre noeud "maître" {{site.data.keyword.mysql}} tomberait en panne.

Ces idées ne représentent que quelques-unes des nombreuses façons de sécuriser et mettre à l'échelle votre environnement. Si vous avez des questions ou des doutes liés à la façon optimale de concevoir votre environnement d'un point de vue sécurité ou évolutivité, l'infrastructure {{site.data.keyword.BluSoftlayer_notm}} est dotée d'une équipe d'ingénierie de vente qui peut vous aider.