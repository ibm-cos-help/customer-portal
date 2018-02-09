---

copyright:

  years: 1994, 2018

lastupdated: "2017-12-04"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:tip: .tip}
{:screen: .screen}
{:new_window: target="_blank"}


# Tutorial Introdução
{: #getting-started}

Neste tutorial, percorreremos o processo para que sua conta do SoftLayer entre em funcionamento para que você possa começar a ordenação e o gerenciamento de seus recursos de infraestrutura.
{:shortdesc}

## Antes de começar
{: #prereqs}

Será necessária uma conta do [{{site.data.keyword.Bluemix}} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://control.bluemix.net/){:new_window}. Efetue login no portal do cliente com suas credenciais do IBMid. A maioria dos novos usuários usa o IBMid para autenticação.

Para usuários com contas que não usam o IBMid para autenticação, efetue login no portal do cliente com as credenciais que você recebeu no e-mail que foi enviado quando sua conta foi criada inicialmente.
{: tip}

## Etapa 1: configurar sua conta
{: #account-setup}

A configuração de sua conta inclui a verificação das informações de contato e dos detalhes de faturamento de sua conta:
 * Para verificar os detalhes de contato da empresa, acesse **Conta** > **Gerenciar** > **Contatos da empresa**. As informações de contato da empresa de sua conta são usadas para notificá-lo sobre quaisquer problemas ou mudanças em sua conta.
 * Para verificar os detalhes de perfil de sua empresa, acesse **Conta** > **Gerenciar** > **Perfil da empresa**. As informações de perfil da empresa contêm detalhes sobre o portador da conta principal.
 * Para verificar seus detalhes de faturamento, acesse **Conta** > **Faturamento** > **Método de pagamento**. O método de pagamento mensal é o cartão de crédito faturado de forma recorrente para os pagamentos associados à sua conta.

## Etapa 2: incluir usuários e designar permissões
{: #users-permissions}

Para incluir usuários em sua conta e configurar permissões iniciais, acesse **Conta** > **Usuários**.
 * Para convidar usuários para ambos os recursos de plataforma e infraestrutura em sua conta com base nas permissões específicas designadas por você, clique em **Convidar usuários**. Em seguida, você será direcionado para a UI do {{site.data.keyword.Bluemix_notm}} Identity and Access Management (IAM) para convidar usuários e designar acesso. Consulte [Convidando usuários e designando acesso](/docs/iam/iamuserinv.html) para obter mais informações.
 * Para incluir apenas usuários com acesso à VPN, clique em **Incluir usuário somente de VPN**. Insira as informações pessoais, configure as permissões do portal e configure o acesso ao dispositivo para o usuário.

Ao configurar permissões de infraestrutura no convite inicial, você escolhe um de três conjuntos de permissões: Apenas visualização, Usuário básico, Superusuário. Após os usuários aceitarem o convite, é possível customizar seus acessos editando suas permissões do portal. Consulte [Permissões de infraestrutura](/docs/iam/infrastructureaccess.html) para obter mais informações.
{: tip}

## Etapa 3: ativar o acesso à rede privada da infraestrutura do {{site.data.keyword.Bluemix_notm}}
{: #enable-private-network}

A rede privada de infraestrutura do {{site.data.keyword.Bluemix_notm}} é oferecida para usuários e dispositivos gratuitamente. Toda a largura da banda que é usada na rede privada é ilimitada e gratuita. A rede privada oferece muitos benefícios, incluindo a replicação de ambientes de dispositivo para outros data centers para failover, acessibilidade do sistema front-end para servidores de banco de dados e acesso e gerenciamento seguros para seus sistemas.

Para permitir o acesso de usuário à rede privada, edite o acesso à VPN no portal do cliente:
  1. Selecione **Conta** > **Acesso à VPN** na barra de menus.  
  2. Clique no link na coluna Acesso à VPN.
  3. Selecione uma opção no menu **Tipo de VPN** e clique em **Salvar**.  

Para usuários em contas que usam a autenticação do IBMid, o usuário da VPN do SoftLayer para acesso à VPN é usado. O nome do usuário da VPN é definido no perfil do usuário. O nome de usuário da VPN é diferente do nome de usuário que é padronizado para o endereço de e-mail e ID da conta do IBMid.
{: tip}

## Etapa 4: assinar notificações
{: #get-notified}

Para ser notificado sobre problemas do sistema que possam ocorrer e eventos de manutenção planejados, é possível assinar notificações por meio do Sistema de Gerenciamento de Eventos. Ao criar uma conta ou se você for incluído em uma, as suas assinaturas para notificações serão canceladas por padrão.

Acesse o Sistema de Gerenciamento de Eventos no portal do cliente para escolher quais notificações você deseja assinar:
  1. Selecione **Conta** > **Gerenciar** > **Assinaturas** na barra de menus.
  2. Clique em uma assinatura específica na lista que é mostrada.
  3. Selecione a caixa de seleção **Sim** na coluna Inscrito.
  4. Clique em **Visualizar todas as assinaturas** para retornar à lista de assinaturas disponíveis e assinar outros tipos, se necessário.

## Próximas Etapas
{: #next-steps}

Após sua conta ser configurada, acesse o catálogo do [{{site.data.keyword.Bluemix_notm}} ![Ícone de link externo](../icons/launch-glyph.svg)](https://console.bluemix.net/catalog/?category=infrastructure){:new_window} e comece a pedir dispositivos.