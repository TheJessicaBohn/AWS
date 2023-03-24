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
- MFA: Multi Factor Authenticator
  - Contra senha de autenticação, Ex. duplo fator de verificação.
  - **MFA Virtuais:** Software em um dispositivo remoto que simule um hardware
  - **U2 Security Key:** É um token físico (USB) em contato direto com o computador. Ele é um padrão opensource, criado pela FIDOAlliance.
  - **MFA TOTP :** É um token de hardware gera um código numérico de seis dígitos com base no algoritmo de senha de uso único com marcação temporal (TOTP).
  - ### Configurando um MFA:
    - Vá em Find Services, e busque por: "IAM"
    - Ao entrar na tela "Welcome to Identify and Access Managemente" clique em :"Manage Password Policy"
    - Após clique em: "Change password policy"
    - E então altere o ambiente de acordo com a necessidade de segurança.
    - Ao voltar para a tela "Welcome to Identify and Access Managemente", clique em "Activate MFA on your root account", e depois em "Manage MFA"
    - Ao entrar na tela "Your Security Credentials", clique em "Multi-factor authentication (MFA) e clique em "Activate MFA".
    - Ao clicar nessa opção ele vai abrir uma modal "Manage MFA device", com as opções de tipos de MFA previamente apresentas. Nesse caso vou utilizar a MFA virtual pois é a que eu tenho acesso nesse momento. Clique em "Continue";
    - Ele vai abrir uma tela chamada "Set up virtual MFA device", clique em "Show QR Code", será aperto um QR Code para ser escaneado (tire print pois caso você perca seu dispositivo, você conseguirá se conectar novamente), e logo abixo terão dois campos de "MFA code 1" e "MFA code 2", após escaneado os dois campos deverão ser preenchidos com os códigos que vão aparecer no dispositivo que escaneou o QR Code. Após isso clique em "Assing MFA".
    - Agora só possivel entrar na conta que foi feita a ativação do MFA, se for aceito pelo Multi-factor authentication.
## Links importantes
 - [Documentação oficial AWS](https://docs.aws.amazon.com/)
 - [Webinars](https://aws.amazon.com/pt/about-aws/events/)
 - [Alguns Tutoriais](https://aws.amazon.com/pt/getting-started/hands-on/?getting-started-all.sort-by=item.additionalFields.sortOrder&getting-started-all.sort-order=asc&awsf.getting-started-category=*all&awsf.getting-started-level=*all&awsf.getting-started-content-type=*all)
 
 ## Dicas e extras:
 - [AWS Free Tier](https://aws.amazon.com/pt/free/?trk=c9dcfe7b-33fc-4345-b0c3-77b810bbd58c&sc_channel=ps&ef_id=Cj0KCQjw8e-gBhD0ARIsAJiDsaW0WMm9KlDYhElMKdfWBlwaAI2O_p_eUiX1c9jnp7jG0gPNVSn9jAsaAmYAEALw_wcB:G:s&s_kwcid=AL!4422!3!454435137261!e!!g!!aws%20free%20tier!10758390156!106168762716&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=*all):
  - Como vários tipos de serviços a AWS tem faixas de gratuidade, para ser utilizada, fique atento para não ser taxado depois:
    - Sempre gratúito;
    - 12 meses de gratuidade;
    - Testes;
