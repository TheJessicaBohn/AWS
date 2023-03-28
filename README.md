# AWS
- Tópicos:
  - Configurações iniciais AWS CLI
  - EC2: Ambiente computacional da AWS e seus recursos 
  - VPC: Ambient Networking 
  - Route 53: DNS
  - S3: Armazenamento 
  - Cloud Watch: Monitoramento 
  - IAM: Gestão de acessos

## Configurações iniciais AWS:
- [Criar conta aqui](https://console.aws.amazon.com/);
- ### Configurando um MFA:
  - Vá em Find Services, e busque por: **IAM**
  - Ao entrar na tela **Welcome to Identify and Access Managemente** clique em : **Manage Password Policy**
  - Após clique em: **Change password policy**
  - E então altere o ambiente de acordo com a necessidade de segurança.
  - Ao voltar para a tela **Welcome to Identify and Access Managemente**, clique em **Activate MFA on your root account**, e depois em **Manage MFA**
  - Ao entrar na tela **Your Security Credentials**, clique em **Multi-factor authentication (MFA)** e clique em **Activate MFA**.
  - Ao clicar nessa opção ele vai abrir uma modal **Manage MFA device**, com as opções de tipos de MFA previamente apresentas. Nesse caso vou utilizar a MFA virtual pois é a que eu tenho acesso nesse momento. Clique em **Continue**;
    - Ele vai abrir uma tela chamada **Set up virtual MFA device**, clique em **Show QR Code**, será aperto um QR Code para ser escaneado (tire print pois caso você perca seu dispositivo, você conseguirá se conectar novamente), e logo abixo terão dois campos de **MFA code 1** e **MFA code 2**, após escaneado os dois campos deverão ser preenchidos com os códigos que vão aparecer no dispositivo que escaneou o QR Code. Após isso clique em **Assing MFA**.
    - Agora só possivel entrar na conta que foi feita a ativação do MFA, se for aceito pelo Multi-factor authentication.

## AWS CLI:
- O que é: um console de configurações remotas por linha de comando(existe para Windowns, Linux e Mac), feito em Python(tem que instalar no PC), que funciona como uma especie de GitBash;
- Download da ferramenta para [AWS CLI Windows](https://awscli.amazonaws.com/AWSCLIV2.msi);
  - clique para executar e **Next** até **Finish**;
- Download da ferramenta para [AWS CLI Linux](https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip);
  - no terminal ```unzip awscli-exe-linux-x86_64.zip``` e depois ```sudo ./aws/install```;
- Download da ferramenta para [AWS CLI MAC](https://awscli.amazonaws.com/AWSCLIV2.pkg);
  - no terminal ```sudo installer -pkg ./AWSCLIV2.pkg -target /```
- Após feita a instalação digite ```aws --version``` no seu terminal de preferência;
![image](https://user-images.githubusercontent.com/47541659/228098070-a173a1ce-5f5f-43d1-ab7c-95752c772134.png)
### Configurando um novo usuário na pagina web para utilização no CLI:
- Abra o link na web onde você criou o seu login, e busque por: **IAM**
- Na tela **Welcome to Identity and Access Management** será necessário criar um novo grupo e um novo usuário para poder utilizar no CLI, como uma medida de segurança, em não utilizar o usuário root;
- Clique em **Groups** -> **Create New Group** -> em **Set Group Name** adicione o nome desejado ex: adms. -> em **Attach Policy** selecione as politicas desejadas, ex: **AdministratorAccess**, essa no caso já da acesso total para o grupo.
- Voltando e clicando em **Users** -> **Add User** -> em **Add User** adicione o nome desejado ex: administrador. -> em **Select AWS access type** escolha o tipo de acesso desse usuário: **Programmatic access**(acesso por linha de comando via API, SDK, CLI) ou **AWS Management Console access**(ou acesso pagina web), como vamos utilizar esse usuário no CLI que foi instalado, escolha a primeira opção. **Next** -> em **Set permissions** pode-se colocar o usuário em um grupo ou anexar uma politica de acesso diretamente, como o grupo já foi criado, apenas adicione o grupo. **Next** -> em **Add Tags** adicione um "indicador" se quiser.  **Next** -> em **Review**: é a verificação final das configurações adicionadas pelas telas anteriores. -> **Create user**;
- Após isso ele nos mostrará se o usuário foi criado com sucesso, e através de qual url esse usuário vai pode fazer o acesso. E logo abaixo numa tabela de usuários existem as informações **Access key ID**(login do usuario), e a **Secret access key**(senha).
- Acima da tabela existe um botão de **Download .csv**, onde possui os dados acima, é importante salvar para posteriormente resgatar a sua conta de usuário.
### Configurando usuário no CLI:
- No terminal de sua preferência digite: ```aws configure```, para começar os procedimentos de configuração do CLI localmente.
  - Então vai aparecer um campo solicitando o usuário que será configurado: **AWS Access Key ID [None]:** então na frente cole o seu Access Key ID, criado na página web da AWS.
  - Agora ele solicita a senha: **AWS Secret Access Key [None]:** o mesmo passo anterior só que com a Secret Key.
  - **Defaul region name [None]:** us-east-l (nesse caso é um exemplo, mas pode-se escolher outro).
  - Por ultimo ele dá a opção de como os dados vão sair na tela para o usuário no campo **Defaul output format [None]:** text .Nesse caso pode-se escolher **texto** ou **json**, pode escolher a sua favorita;
  - De enter e agora o seu CLI está configurado.

## Configurações de VPC:
- Vá em Find Services, e busque por: **VPC**;
- Na tela **Resources by Region**, é possivel ver todos os recursos das VPCs, como sub-nets, route-tables, NAT- Gateways, etc.
- Também é possivel ver nessa tela a parte de segurança;
- VPNs;
 
 ## Dicas e extras:
 - [AWS Free Tier](https://aws.amazon.com/pt/free/?trk=c9dcfe7b-33fc-4345-b0c3-77b810bbd58c&sc_channel=ps&ef_id=Cj0KCQjw8e-gBhD0ARIsAJiDsaW0WMm9KlDYhElMKdfWBlwaAI2O_p_eUiX1c9jnp7jG0gPNVSn9jAsaAmYAEALw_wcB:G:s&s_kwcid=AL!4422!3!454435137261!e!!g!!aws%20free%20tier!10758390156!106168762716&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=*all):
  - Como vários tipos de serviços a AWS tem faixas de gratuidade, para ser utilizada, fique atento para não ser taxado depois:
    - Sempre gratúito;
    - 12 meses de gratuidade;
    - Testes;

## Glossário:
- **AWS Command Line Interface (AWS CLI):** é uma ferramenta unificada para o gerenciamento de seus produtos da AWS. Com apenas uma ferramenta para baixar e configurar, você poderá controlar vários produtos da AWS pela linha de comando e automatizá-los usando scripts;
- **Amazon Elastic Compute Cloud (Amazon EC2)** é um recurso de ambiente para computação virtual dimencionável. Ele possui:
   - **instâncias**: Dentro delas existe as **Imagens de máquina da Amazon (AMIs)**, que empacotam os bits de que você precisa para seu servidor (incluindo o sistema operacional, software adicional, configurações  de capacidade de CPU memória, armazenamento e redes). 
   - Balancemanto de carga 
   - Auto Scaling
   - Security Group : firewall
   - Armezenamento: de discos, Ex. EBS.
   - Segurança: secrets keys, access keys, chave privada, etc;
- **Identity and Access Management (IAM):** é um gerenciador onde é possível especificar quem ou o que pode acessar serviços e recursos na AWS, gerenciar permissões refinadas de maneira centralizada e analisar o acesso para refinar as permissões na AWS.
- **MFA: Multi Factor Authenticator**
  - Contra senha de autenticação, Ex. duplo fator de verificação.
  - **MFA Virtuais:** Software em um dispositivo remoto que simule um hardware
  - **U2 Security Key:** É um token físico (USB) em contato direto com o computador. Ele é um padrão opensource, criado pela FIDOAlliance.
  - **MFA TOTP :** É um token de hardware gera um código numérico de seis dígitos com base no algoritmo de senha de uso único com marcação temporal (TOTP).
-**S3 Amazon Simple Storage Service (Amazon S3):** é um serviço de armazenamento e gerenciamento de objetos que oferece:
  - Escalabilidade;
  - Disponibilidade de dados;
  - Segurança;
  - Performance. 
  - No seu armazenamento pode conter: data lakes, sites, aplicações móveis, backup e restauração, arquivamento, aplicações corporativas, dispositivos IoT e análises de big data. 
- **Virtual Private Cloud(VPC):** É uma camada de rede virtual configurada pelo usuário que permite realizar particionamento de niveis de recursos da AWS, para proteger de interferências de outra rede, da internet ou mesmo de outra conta AWS. Ele possui os seguintes recursos:
  - **Nuvens privadas virtuais (VPC):** é uma rede virtual muito semelhante a uma rede tradicional só que privada.
  - **Sub-redes**: é uma gama de endereços IP na VPC. Uma sub-rede deve residir em uma única zona de disponibilidade.
  - **Endereçamento IP:** endereços IPv4 e endereços IPv6 podem ser  atribuídos VPCs e sub-redes.
  - **Roteamento:** pode-se usar tabelas de rotas para determinar para onde o tráfego da sub-rede ou do gateway será direcionado.
  - **Gateways:** Um gateway conecta a VPC a uma outra rede. Por exemplo, use um gateway da Internet para conectar a VPC à Internet. 
  - **Endpoints:** um endpoint da VPC para se conectar a Serviços da AWS de modo privado, sem usar um gateway da Internet ou um dispositivo NAT.
  - **Conexões de emparelhamento:** conexão de emparelhamento da VPC para rotear o tráfego entre os recursos em duas VPCs.
  - **Espelhamento de tráfego:** Copie o tráfego de rede das interfaces de rede e envie aos dispositivos de segurança e monitoramento para inspeção profunda dos pacotes.
  - **Gateways de trânsito:** um gateway de trânsito funciona como um hub central, para rotear tráfego entre VPCs, conexões VPN e conexões do AWS Direct Connect.
  - **Logs de fluxo da VPC:** captura informações sobre o tráfego IP de entrada e saída nas interfaces de rede da VPC.
  - **Conexões da VPN:** Conecte as VPCs às redes on-premises usando a AWS Virtual Private Network (AWS VPN).
  
## Links importantes
 - [Documentação oficial AWS](https://docs.aws.amazon.com/)
 - [Webinars](https://aws.amazon.com/pt/about-aws/events/)
 - [Alguns Tutoriais](https://aws.amazon.com/pt/getting-started/hands-on/?getting-started-all.sort-by=item.additionalFields.sortOrder&getting-started-all.sort-order=asc&awsf.getting-started-category=*all&awsf.getting-started-level=*all&awsf.getting-started-content-type=*all)

## Fontes
- https://docs.aws.amazon.com/pt_br/IAM/latest/UserGuide/id_credentials_mfa_enable_physical.html
- https://aws.amazon.com/pt/cli/#:~:text=A%20AWS%20Command%20Line%20Interface,e%20automatiz%C3%A1%2Dlos%20usando%20scripts.
- https://docs.aws.amazon.com/pt_br/AWSEC2/latest/UserGuide/concepts.html
- https://docs.aws.amazon.com/pt_br/vpc/latest/userguide/what-is-amazon-vpc.html
- https://docs.aws.amazon.com/pt_br/AmazonS3/latest/userguide/Welcome.html
- https://docs.aws.amazon.com/pt_br/cli/latest/userguide/cli-chap-welcome.html
- https://aws.amazon.com/pt/iam/
