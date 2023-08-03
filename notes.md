#### 03/08/2023

Curso de Redes: construindo um projeto com VLANs, políticas de acesso e conexão com internet

@01-Redes locais virtuais (VLANs) 

@@01
Apresentação

Olá! Meu nome é Lucas, sou instrutor aqui na Alura.
Audiodescrição: Lucas Mata Lucas Mata é uma pessoa branca, de cabelos pretos. Tem nos olhos óculos da mesma cor. No corpo, uma camisa branca. Ao fundo, o estúdio da Alura, onde há uma parede lisa com a iluminação azul e roxa e uma estante à direita com alguns itens decorativos, incluindo livros e quadros com temática geek.
Estou aqui para te dar as boas-vindas no curso de Redes.

Este conteúdo foi pensado para quem está aprofundando o conhecimento na construção e operação de redes para diversos ambientes.

Vamos abordar os principais protocolos, dispositivos e configurações para a construção de conexões eficientes. Para acompanhar nosso curso de melhor forma, sugerimos a visita ao curso inicial da formação de Redes.

Mesmo que haja conhecimento prévio em redes, recomendamos verificar o primeiro curso, onde há conceitos e tópicos que abordamos de forma bem prática. Se está iniciando agora, ele é um bom ponto de partida.

O que vamos estudar aqui?
Vamos começar entendendo:

O que são e como criar LANs (Redes Locais Virtuais);
Como melhorar a estabilidade da rede usando links de redundância;
Como alocar endereços IP de modo eficiente;
Como definir listas de acesso;
Como implementar a conexão com redes externas, realizando a tradução de endereços IP.
E como veremos todos esses tópicos? De forma prática, construindo uma rede para um instituto, o Instituto Inovae, que possui alguns requisitos. Por exemplo, vamos ter que conectar mais de 600 dispositivos nesta rede, gerenciar diferentes setores e ambientes, fazer a inclusão de servidores e a conexão com a rede externa (internet).

No final do curso, teremos um projeto com todas as conexões e configurações funcionando.

Aproveite os recursos da plataforma. Além dos vídeos, temos atividades e o apoio do nosso fórum e da comunidade no Discord.

Então, vamos começar essa nova jornada pelo mundo das redes?

https://cursos.alura.com.br/course/redes-conceitos-iniciais-criacao-intranet/task/129301

@@02
Criando redes locais (LANs)

Fomos contratados pelo Instituto Inovae para construir uma rede que atenda aos requisitos dessa instituição.
Briefing do projeto
Essa instituição possui dois setores principais:

Setor Administrativo
Setor de Pesquisa
O primeiro engloba funções de suporte, como recursos humanos e setor financeiro. Já o segundo é o núcleo da instituição, composto por especialistas, pesquisadoras e professoras.

Os principais requisitos para essa rede são:

Acesso à internet
Servidores com políticas de acesso
Conexão de mais de 600 computadores
Sistema
Em relação ao primeiro requisito, todas as pessoas colaboradoras, tanto do setor administrativo quanto do setor de pesquisa, precisam ter a capacidade de se conectar com a rede global de computadores, a internet.

Vamos precisar incluir alguns servidores com políticas de acesso, pois não serão todos os servidores que estarão acessíveis a todas as pessoas colaboradoras da companhia. Alguns podem ser acessíveis apenas à gerência, por exemplo.

Além da conexão de mais de 600 computadores na rede que vamos construir, devemos prever o sistema de telefonia, que operará sobre a infraestrutura de rede da instituição.

Isso levanta a pergunta:*** como vamos começar a construir essa rede?*** Vamos precisar simular a conexão de mais de 600 computadores em um ambiente de simulação que vamos usar, o Cisco Packet Tracer?

Observação: Para entender como instalar o Cisco Packet Tracer, basta retomar o Curso 1 da Formação de Redes.
Criando a rede
Vamos abrir o Packet Tracer, para que possamos entender melhor como vamos trabalhar ao longo deste projeto. Veremos que dois ambientes diferentes foram configurados antecipadamente.

Imagem com dois ambientes virtuais, lado a lado, no Cisco Packet Tracer. Cada um é constituído de três ícones alinhados em triângulo. O ícone do topo representa um switch e os outros dois, computadores. O switch está conectado aos computadores por setas pretas, no meio das quais há dois triângulos apontando para o switch, representando o fluxo da rede. No ambiente à esquerda, há o texto "2950-24 Switch1" abaixo do switch, o texto "PC-PT - PC0" abaixo do computador esquerdo e o texto "PC-PT - PC1" abaixo do computador direito. No ambiente à direita, há o texto "2950-24 Switch0" abaixo do switch, o texto "PC-PT - PC2" abaixo do computador esquerdo e o texto "PC-PT - PC3" abaixo do computador direito.

Nossa estratégia aqui será reduzir o problema de tal forma que possamos atender a todos os requisitos, mesmo que estejamos usando apenas alguns dispositivos para simular essa rede.

Nós vamos simular dois laboratórios: chamaremos o primeiro de "Laboratório A" e o segundo de "Laboratório B". Então no esquema da esquerda, onde temos o "PC0" e o "PC1", podemos facilmente renomear esse PC, clicando sobre o título "PC0" e substituindo-o por "Pesquisador_A". Vamos renomear o "PC1" e colocar o nome de "Gerência".

Renomearemos também o nome do switch conectado aos dois PCs. Seu nome será "Switch_A". Já o switch do ambiente esquerdo receberá o nome de "Switch_B".

E para diferenciar bem esse ambiente, acessaremos a barra secundária de ícones no canto superior esquerdo da tela, onde selecionaremos o ícone de retângulo preto denominado "Draw Rectangle" (Desenhar retângulo).

Com ela, clicaremos e arrastaremos o mouse a partir do canto superior esquerdo do ambiente esquerdo e desenharemos um retângulo em volta dele, usando as mesmas configurações que o Cisco tem por padrão. Faremos o mesmo para o ambiente direito.

Por fim, vamos fechar a janela intitulada "Palette Dialog", aberta à direita da barra de ícones quando selecionamos a ferramenta de triângulo. Para isso, basta acessá-la e clicar no "x" do canto superior direito.

Em seguida, vamos inserir uma nota, clicando no ícone de folha de papel denominado "Place Note" (Inserir nota). Posicionando o cursor na parte inferior de cada um dos ambientes, vamos clicar e inserir os textos "Laboratório A" à esquerda e "Laboratório B" à direita.

Pressionaremos "Esc" para desselecionar tudo e reposicionaremos os textos, alinhando-os corretamente. Renomearemos a rede "PC2" para "Pesquisador-B. No lugar de "PC3", vamos escrever "Coordenação", que também corresponde a um setor administrativo.

Vamos afastar os computadores "Coordenação" e "Pesquisador-B" para tornar os textos mais legíveis.

Temos um switch em cada laboratório e usamos cabos de conexão direta entre o "switch" e o PC, pois são dispositivos diferentes e, portanto, possuem placas de rede diferentes.

Precisamos selecionar uma conexão entre os "Switches" dos dois ambientes para que esses computadores estejam conectados na rede interna do instituto.

Como são "switches" do mesmo modelo, vamos precisar utilizar um cabo de conexão cruzada. Portanto, vamos acessar a barra inferior da tela que possui ícones de conexões e selecionar o ícone do cabo de conexão cruzada ("Copper Cross-Over"), constituído pelo desenho de uma linha pontilhada em zigue-zague.

Clicando no switch A, selecionaremos na lista suspensa a porta "FastEthernet0/3", conectando a linha pontilhada do switch A para o switch B.

Imagem anterior, com a adição de um retângulo cinza ao redor de cada um dos ambientes com os textos "Laboratório A", à esquerda e "Laboratório B", à direita, e uma linha pontilhada preta na horizontal, conectando o switch esquerdo ao switch direito.

Agora, o que podemos fazer é, por exemplo, atribuir um IP estático para esses PCs. Vamos clicar no ícone de computador do "Pesquisador_A", que abrirá uma janela de mesmo nome. Em seu interior, acessaremos a aba "Desktop", clicaremos na opção "IP Configuration" e vamos atribuir no campo "IPv4 Address" o endereço de IP 193.65.0.1.

193.65.0.1
COPIAR CÓDIGO
Vamos pressionar "Ctrl+A" e "Ctrl+C" para acelerar o processo de configuração em outros PCs. Após isso, pressionamos "Enter". Com isso, a máscara de rede será automaticamente preenchida, tratando-se de um endereço de IP da classe C. Vamos fechar essa janela e realizar o mesmo processo nos demais PCs.

Clicaremos com o botão direito no PC da gerência, acessaremos "Desktop > IP Configuration" e alteraremos o último dígito do IP de "1" para "2" e pressionaremos "Enter" para finalizar. Atribuiremos o número "3" ao último dígito do IP do PC do pesquisador B.

Por fim, clicando com o botão direito no PC da Coordenação, substituiremos o último dígito do seu IP para "4", que fica "193.65.0.4". Após pressionar "Enter", tudo parece em ordem.

Podemos alterar o modo de funcionamento do nosso Packet para o modo simulação. Neste módulo, temos uma visualização de todos os protocolos que estão sendo utilizados pela nossa rede.

Agora que nossa rede local está configurada, que tal fazermos um teste de conectividade?

Realizando testes de conectividade
No curso anterior, utilizamos o Packet no modo Real-Time. Neste modo, não tínhamos uma visualização do que ocorria internamente na nossa rede. Podemos testar agora e operar no modo simulação, realizando nosso tradicional teste de conectividade usando o comando PING no prompt de comando dos nossos PCs.

Para isso, iremos à barra azul inferior da tela do Cisco, no canto direito da tela, e mudaremos para o modo de simulação, clicando no botão "Simulation". Veremos que será aberta uma janela acima dele, exibindo uma série de eventos, para os quais podemos aplicar filtros.

Vamos voltar aos ambientes e clicar no computador do pesquisador A. Na janela de mesmo nome, selecionaremos "Desktop > Command Prompt" para abrir o prompt de comando. Nele, digitaremos um PING para o PC da Coordenação do Laboratório B por meio do comando abaixo, mas não pressionaremos "Enter" ainda.

ping 193.165.0.4
COPIAR CÓDIGO
Na aba de Simulação, vamos clicar no botão com uma seta para a direita e colocar no modo Real-Time. Com isso, veremos uma carta vermelha sair do "Switch_B" e aterrissar no "Pesquisador_B", atravessando a linha preta que os conecta.

Voltando à janela do prompt de comando, pressionaremos "Enter" no comando PING. Vamos expandir a tela de simulação, arrastando sua aresta lateral esquerda em direção ao centro da tela. Em seu interior, veremos que há uma tabela com uma série de protocolos ARP.

No corpo do nosso programa, veremos uma série de mensagens sendo encaminhadas a partir do switch e atravessando as linhas que o conectam aos PCs da nossa rede, que são visíveis na simulação.

Algumas mensagens recebem um 'x'. O que isso significa?

Voltando à janela de Simulação e clicando em uma das mensagens que chegaram no pesquisador B, veremos uma nova janela na qual clicaremos na seção "Layer2" e veremos em seu interior uma série de mensagens com 'FFF'.

Isso é uma característica de uma mensagem de Broadcast, ou seja, como este PC não sabe onde está o dispositivo para o qual ele está enviando esse pacote do PING, ele está disparando a mensagem para todos na rede questionando: "Você é o dispositivo de IP 193.65.0.4?" Já que o "Pesquisador_B" não possui esse endereço de IP, ele responderá: "Não sou eu."

Se dermos “Play” na janela de Simulação, observamos a existência de uma série de mensagens do protocolo ARP (protocolo característico de uma comunicação Broadcast) sendo enviadas na nossa rede. Isso está causando um pouco de congestionamento. Vamos imaginar o que ocorrerá quando tivermos 600 PCs na nossa rede.

Uma vez que o dispositivo "Pesquisador A" reconhece a localização do PC do coordenador, ele envia este protocolo ICMP, que fica por trás do comando PING utilizado no prompt de comando.

Se pausarmos a simulação clicando no ícone de pausa em sua janela ou mudar para o tempo real por meio de um clique no botão "Realtime" na barra inferior azul, veremos no prompt de comando do "Pesquisador_A" o que aconteceu após darmos o comando PING para o PC "Coordenação".

Observaremos que os quatro pacotes foram enviados com sucesso e as respostas dentro do protocolo ICMP também foram recebidas com sucesso.

Pinging 193.165.0.4 with 32 bytes of data:
Reply from 193.165.0.4: bytes=32_time=23ms TTL=128

Reply from 193.165.0.4: bytes=32 time<lms TTL=128 Reply from 193.165.0.4: bytes=32 time<lms TTL-128

Reply from 193.165.0.4: bytes=32 time<lms TTL-128

Ping statistics for 193.165.0.4:

Packets: Sent = 4, Received = 4, Lost = 0 (0% loss), Approximate round trip times in milli-seconds: Minimum Oms, Maximum 23ms, Average = 5ms

Contudo, detectamos um problema: temos apenas quatro PCs na nossa rede, mas há um certo congestionamento, ou seja, muitas mensagens de Broadcast. Esse problema piorará quando tivermos os 600 computadores conectados.

Conseguiremos melhorar esse tráfego na rede? Conseguiremos otimizá-lo? Veremos na sequência

https://cdn1.gnarususercontent.com.br/1/1319057/2416cb81-636f-4081-b8fb-7a6ef478636e.png

https://cdn1.gnarususercontent.com.br/1/1319057/fa6a35f5-405c-4aab-8190-fc6b065590a7.png

@@03
Para saber mais: diferenças entre LAN, MAN e WAN

Durante o processo de construção e dimensionamento de recursos para a conexão de diferentes dispositivos, é comum estabelecermos uma rede que seja capaz de conectar, de forma adequada, dispositivos distintos de acordo com um conjunto de regras estabelecidas pelas pessoas que utilizaram o espaço.
No vídeo anterior falamos um pouco da LAN, que é uma Rede de Área Local (ou do inglês, Local Area Network). De modo geral, utilizamos as LANs quando desejamos conectar dispositivos muito próximos geograficamente, permitindo que os dispositivos se comuniquem entre si e compartilhem recursos.

Para exemplificar os tipos de redes existentes, vamos pensar em um Laboratório de Fabricação Digital (conhecido também como FabLab). Imagine que você está dimensionando os recursos de acesso e conexão para um FabLab pequeno com vários computadores, uma impressora 3D e um roteador Wi-Fi.

Todos esses dispositivos estão conectados através de uma LAN. Os computadores podem compartilhar entre si os arquivos de projeto e enviar trabalhos para a mesma impressora 3D. Além disso, os dispositivos também podem acessar a internet através do mesmo roteador.

No entanto, quando queremos conectar infraestruturas geograficamente mais distantes, talvez uma LAN não seja o tipo de rede mais adequada. Por exemplo, se você desejar conectar diversos FabLabs espalhados pela cidade, que possuam equipes e equipamentos distintos, podendo ser utilizados para o desenvolvimento de projetos de forma colaborativa?

Considerando que estes FabLabs estão situados em uma cidade e são gerenciados pela mesma organização, é possível garantir que cada um deles tenha sua própria LAN, mas todos conectados através de uma MAN.

Isso possibilita que um membro de um FabLab compartilhe arquivos de projeto ou use recursos de outro FabLab na mesma cidade.

As MANs são Redes de Área Metropolitana (ou do inglês, Metropolitan Area Network) e conectam várias LANs em uma rede de área geográfica maior. Frequentemente vemos este tipo de abordagem na estruturação de redes para uma cidade ou um campus universitário de grande porte. São tipos de redes geralmente gerenciados por uma única entidade responsável.

Por fim, no caso dessas instituições contarem com FabLabs espalhados por cidades distintas, ou em regiões geograficamente mais dispersas (em outros países), é sugerida a estruturação de uma WAN (Rede de Área Ampla, ou do inglês, Wide Area Network).

No caso dos FabLabs, podemos imaginar que uma mesma entidade tem FabLabs em várias cidades ou até mesmo países distintos. Cada um tem sua própria LAN e todos numa mesma cidade podem estar conectados por uma mesma MAN.

Porém, todos eles estão conectados através de uma WAN . Assim, membros em qualquer localidade podem compartilhar recursos e se comunicar como se estivessem no mesmo local.

@@04
Construindo redes locais virtuais (VLANS)

Estamos construindo a rede para o Instituto Inovae e nos deparamos com um problema. Havia um tráfego muito intenso, um congestionamento de pacotes na nossa rede, embora tivesse poucos computadores.
Além disso, temos um outro requisito que é importante lembrar: o serviço de telefonia. Algumas empresas, com muitos colaboradores, ainda fazem o uso de um telefone fixo, como costumávamos dizer há um tempo atrás.

Este telefone permite utilizar a mesma infraestrutura de rede — ou seja, não precisamos ter um cabeamento específico para os telefones. Podemos usar o conector da internet mesmo para fazer a conexão entre os colaboradores, inclusive entre os telefones da rede da empresa com telefones externos.

Porém, para que tenhamos esse sistema de telefonia, precisamos estabelecer uma priorização de tráfego de voz sobre o tráfego de dado, porque se não priorizarmos esse tráfego, pode ser que uma mensagem, um dado de voz da conexão com outro telefone demore a chegar no destino.

E não queremos que a nossa comunicação de voz não seja em tempo real. Não é verdade? Esse é um requisito básico para qualquer videochamada e para qualquer tipo de chamada de voz.

Então, precisamos resolver dois problemas:

Reduzir o tráfego da nossa rede
Priorizar o tráfego de voz sobre o tráfego de dados
Será que conseguimos resolver esses dois problemas usando uma única solução? A resposta é sim, é possível. E para isso, podemos utilizar o conceito de Redes Locais Virtuais, ou melhor dizendo, as VLANs (Virtual Local Area Network).

Vamos usar esse conceito, que se parece, por analogia, com o conceito de máquina virtual. Quando temos, por exemplo, um Windows rodando na nossa máquina e muitas vezes queremos testar uma aplicação que nós construímos para um ambiente Linux, instalamos uma máquina virtual para rodarmos em cima dela esse sistema operacional.

As VLANs funcionam de um modo bastante similar. Vamos criar redes locais virtuais que vão operar sobre uma infraestrutura única de rede, no nosso caso, nossos switches.

E como fazemos para configurar as nossas VLANs? Se estivéssemos no mundo real, muitas vezes precisaríamos pegar um computador, um cabo console e conectar no switch para configurar cada switch por vez, ou usar até alguma técnica mais moderna que conseguiria acessar switches remotamente sem fazer a conexão direta.

No nosso caso, no ambiente de simulação, podemos clicar com o botão direito, por exemplo, sobre o nosso switch da esquerda, para abrir a janela CLI, na qual faremos a configuração.

Como começamos? Sempre começamos no modo com menos privilégios, onde conseguimos resolver alguns problemas simples e temos que ir para o modo que nos permita fazer algumas configurações avançadas no nosso dispositivo.

Na linha do prompt da janela CLI, começamos com o comando enable, para avançarmos em termos de privilégio.

enable
COPIAR CÓDIGO
No enable, o que podemos ver? Vamos dar o comando aqui show vlan brief. Esse comando nos permitirá analisar todas as configurações de LANs virtuais existentes nesse switch.

show vlan brief
COPIAR CÓDIGO
Ao darmos esse comando, o que observamos como resultado? Uma lista com VLANs.

1 default                              active            Fa0/3,
Fa0/4, Fa0/5, Fa0/6
                                                         Fa0/7,
Fa0/8, Fa0/9, Fa0/10
                                                         Fa0/11,
Fa0/12, Fa0/13, Fa0/14
                                                         Fa0/15,
Fa0/16, Fa0/17, Fa0/18
                                                         Fa0/19,
Fa0/20, Fa0/21, Fa0/22
                                                         Fa0/23,
Fa0/24
1002 fddi-default                       active
1003 token-ring-default                 active
1004 fddinet-default                    active
1005 trnet-default                      active
COPIAR CÓDIGO
Primeiro observamos que as VLANs são identificadas por um número, que vai de 1 até 1005. A VLAN 1 é a VLAN padrão, então se conectamos um computador, conectamos outros switches. Essa rede vai operar na VLAN 1 por padrão.

As VLANs entre 1002 e 1005 são VLANs reservadas para tecnologias antigas, para que tenhamos uma retrocompatibilidade. São pouco usadas, mas servem para que tenhamos essa compatibilidade entre tecnologias diferentes.

Se observarmos, todas essas interfaces que temos no nosso switch estão, por padrão, configuradas na VLAN 1. E agora surge a pergunta, como criamos uma VLAN?

Vamos acessar a última linha do prompt e vamos aumentar um pouco nos termos de privilégio com o comando configure terminal.

configure terminal
COPIAR CÓDIGO
Nos direcionaremos para VLAN, mas não temos certeza qual comando devemos rodar, então digitamos vlan ?.

vlan ?
COPIAR CÓDIGO
Quando digitamos isso, o que aparece? Precisaremos inserir uma ID, um número entre 1 e 1005, para identificar essas VLANs, com exceção desses números que são reservados.

Então, por exemplo, podemos colocar uma vlan 10.

vlan 10
COPIAR CÓDIGO
Com isso, o prompt acessará o local config-vlan. Podemos usar em seguida o comando name para nomear essa VLAN. Vamos nomeá-la como pesquisa pois ela era do segmento da pesquisa.

name pesquisa
COPIAR CÓDIGO
Daremos um "Enter". Podemos executar um exit.

exit
COPIAR CÓDIGO
Voltamos para o local config. Vamos criar outra VLAN para o segmento administrativo e adicionaremos essa VLAN com ID 20.

vlan 20
COPIAR CÓDIGO
Agora vamos inserir um nome para essa VLAN com name administrativo e pressionaremos "Enter".

name administrativo
COPIAR CÓDIGO
Por fim, executaremos o exit.

exit
COPIAR CÓDIGO
Qual seria o próximo passo? Se executarmos no prompt um "Ctrl+Z" e em seguida rodar o comando show VLAN brief, veremos se as nossas VLANs estão ativas.

10     pesquisa                       active
20     administrativo                 active
1002   fddi-default                   active
1003   token-ring-default             active
1004   fddinet-default                active
1005   trnet-default                  active
COPIAR CÓDIGO
Elas estão ativas, mas o que não temos? Nenhuma dessas interfaces, tanto da pesquisa quanto da administração, estão vinculadas a essa VLAN. Como faremos isso?

Precisaremos entrar nessa interface. E para isso, qual comando utilizamos? É o comando configure terminal.

configure terminal
COPIAR CÓDIGO
Em seguida, vamos digitar interface e o nome dela. No caso desse computador da pesquisa, passamos o mouse por cima dele na tela principal da aplicação e vemos que seu nome é "FastEthernet 0/1".

interface Fa 0/1
COPIAR CÓDIGO
Observe que usaremos uma sigla, FA, que é um acrônimo dessa conexão, mas poderíamos escrever por extenso.

Após o "Enter", entraremos nessa interface. Vamos usar comando switchport mode access para modificar a configuração dessa porta, dessa interface, para o modo de acesso. Este modo é utilizado quando estamos conectando um dispositivo de rede, por exemplo, com um dispositivo final, como é o caso de um PC.

switchport mode access
COPIAR CÓDIGO
Vamos pressionar "Enter". E agora precisamos vincular essa porta. Para isso, usaremos o mesmo comando switchport access seguido da VLAN que vincularemos. No caso da pesquisa A, seria a VLAN 10, a VLAN de pesquisa.

switchport access vlan 10
COPIAR CÓDIGO
Está feita a configuração da VLAN, vinculamos a VLAN à interface do computador de pesquisa A. Vamos rodar o exit.

exit
COPIAR CÓDIGO
Agora, temos que fazer o mesmo processo para o PC da gerência. Porém, vamos vinculá-lo com a VLAN administrativa, a VLAN 20.

Para isso, vamos entrar na interface FastEthernet 0/2 com o comando abaixo.

interface fa 0/2
COPIAR CÓDIGO
Entramos na interface. Se pressionarmos a seta para cima do teclado no prompt, poderemos acessar e usar os comandos anteriores. Vamos pressionar essa seta até encontrar o comando switchport mode access.

switchport mode access
COPIAR CÓDIGO
Vamos dar "Enter", usar o comando switchport access vlan 10, mudar o seu número para 20 e pressionarEnter.

switchport access vlan 20
COPIAR CÓDIGO
Rodaremos um exit e faremos um "Ctrl+Z". Em seguida, rodaremos um show vlan brief.

show vlan brief
COPIAR CÓDIGO
Observe que agora temos as VLANs ativas e com duas interfaces, uma em cada VLAN vinculadas.

10     pesquisa                       active         Fa0/1
20     administrativo                 active         Fa0/2
1002   fddi-default                   active
1003   token-ring-default             active
1004   fddinet-default                active
1005   trnet-default                  active
COPIAR CÓDIGO
Acabamos de fazer a configuração da VLAN 10 e da VLAN 20, respectivamente, "Pesquisa" e "Administração", para o switch A pertencente ao laboratório A.

Como exercício, vocês devem replicar esse mesmo processo para o switch B que está no Laboratório B.

Neste vídeo, já realizamos o processo do Laboratório B e portanto, partiremos para o teste de conectividade entre o PC do pesquisador A e o PC do pesquisador B que estão na mesma VLAN 10, correspondente à pesquisa.

Testando a conectividade
Então vamos clicar no PC do pesquisador A e realizar o nosso famoso ping no terminal dele, para o endereço 193.165.0.3 que corresponde ao PC do pesquisador B.

ping 193.165.0.3
COPIAR CÓDIGO
Vamos esperar para ver qual o resultado desse nosso ping.

Pinging 193.165.0.3 with 32 bytes of data:


Request timed out.
Request timed out.
Request timed out.
COPIAR CÓDIGO
O resultado não parece muito promissor. O que pode estar ocorrendo?

Nós configuramos as VLANs nos respectivos switches, porém existe um problema.

Configuramos todas as portas necessárias: a interface que está conectada ao computador do pesquisador A, ao computador da gerência, do pesquisador B e da coordenação.

Contudo, a interface que conecta os dois switches não foi configurada. Precisamos configurar essa interface de tal forma que ela transmita todas as mensagens e pacotes de dados entre as diferentes VLANs que estão configuradas nos respectivos switches, tanto no A como no B.

Como fazemos isso? Clicaremos no switch A (à esquerda) para abrir a janela do prompt CLI. Em seu interior, rodaremos um exit.

exit
COPIAR CÓDIGO
Vamos pressionar "Ctrl+Z" e executar a opção configure terminal.

configure terminal
COPIAR CÓDIGO
Vamos entrar na interface FastEthernet 0/3, que é a interface de conexão entre esses dois switches.

interface Fa 0/3
COPIAR CÓDIGO
E o que vamos fazer agora? Vamos utilizar o mesmo comando switchport mode, mudando apenas o modo. Ao invés de ser o modo acesso (access), que é o modo entre um dispositivo de rede e um dispositivo final, nós vamos para o modo trunk.

Este é o modo que faz com que essa interface transmita todos os dados e faça a comunicação entre dispositivos que estão conectados em uma mesma VLAN.

switchport mode trunk
COPIAR CÓDIGO
Após pressionar "Enter", mudamos o modo de funcionamento dessa porta, podemos realizar um exit.

Se agora pressionarmos "Ctrl+Z" e rodar um show interfaces trunk, vamos observar que agora a interface FastEthernet 0/3 (Fa0/3) está funcionando no modo trunk, ou seja, ela vai transmitir todas as VLANs que estiverem no meu dispositivo.

show interfaces trunk
COPIAR CÓDIGO
Retorno do console:

Port            Mode         Encapsulation       Status
Native vlan
Fa0/3           on           802.1q              trunking      1

Port            Vlans allowed on trunk.
Fa0/3           1-1005

Port            Vlans allowed and active in management domain
Fa0/3           1,10,20

Port            Vlans in spanning tree forwarding state and
not pruned
Fa0/3           none
COPIAR CÓDIGO
Precisamos repetir o mesmo processo para o switch B. Então, vamos clicar nele, acessar o terminal CLI, rodar o configure terminal, seguido de interface Fa 0/3, e por fim switchport mode trunk.

Após essas etapas, faremos um exit.

Agora, o que podemos fazer para testar? Vamos fechar a janela do terminal CLI, pressionando o botão "x" no canto superior direito.

Veremos que a interface FastEthernet 0-3 do switch A já está ativada, como podemos ver na seta verde que se encontra à direita dele, por cima da linha pontilhada.

Em breve a interface FastEthernet do switch B vai ficar no mesmo modo. Se passarmos o mouse por cima do switch B, podemos observar na janela modal exibida que a interface FastEthernet 0/3 já não está mais dedicada a nenhuma VLAN específica mas sim no modo genérico, ou seja, ela transmite todas as VLANs.

Port	Link	VLAN	IP Address	MAC Address
FastEthernet0/1	Up	10	--	0060.7087.0D01
FastEthernet0/2	Up	20	--	0060.7087.0D02
FastEthernet0/3	Up	--	--	0060.7087.0D03
…	…	…	…	…
Então, o que podemos fazer agora? Vamos fazer o teste que acabou de dar errado. Vamos clicar no PC do pesquisador A, na guia "Desktop" da janela exibida e acessar o terminal.

Em seu interior, faremos um ping do pesquisador A para o IP do pesquisador B, 193.165.0.3.

ping 193.165.0.3
COPIAR CÓDIGO
Vamos ver se agora vamos obter êxito nesse ping.

Pinging 193.165.0.3 with 32 bytes of data:

Reply from 193.165.0.3: bytes-32 time-5ms TTL-128
Reply from 193.165.0.3: bytes-32 time<lms TTL-128
Reply from 193.165.0.3: bytes=32 time<lms TTL=128
Reply from 193.165.0.3: bytes=32 time<lms TTL-128

Ping statistics for 193.165.0.3:
         Packets: Sent = 4, Received 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
       Minimum Oms, Maximum = 5ms, Average = 1ms
COPIAR CÓDIGO
Veremos que agora deu certo.

E se fizermos um ping desse mesmo computador para o computador da coordenação, conseguiremos fazer essa comunicação? Eles estão em VLANs diferentes, 193.165.0.4. Vamos testar.

ping 193.165.0.4
COPIAR CÓDIGO
Veremos que não funcionou.

Pinging 193.165.0.4 with 32 bytes of data:


Request timed out.
Request timed out.
COPIAR CÓDIGO
Precisamos fazer com que essas duas VLANs se comuniquem. As VLANs operam como sub-redes, ou seja, elas funcionam independentemente, uma não enxerga a outra durante a operação.

Precisamos fazer um roteamento entre elas para que uma mensagem saindo de um dispositivo que está em uma VLAN alcance outro dispositivo que está em outra VLAN. E é isso que vamos fazer na sequência.

@@05
Redes locais virtuais

As VLANs, ou Virtual Local Area Network, consistem em segmentações de uma rede de forma virtual. Imagine que você deseja aprimorar o sistema de segurança da rede em uma sala de aula de uma universidade onde os estudantes estão realizando uma prova.
Usando VLANS, qual seria a estratégia mais adequada para a criação da rede?

Criar uma VLAN separada para cada estudante.
 
Criar uma VLAN separada para cada estudantes pode gerar um excesso de infraestrutura, além de ser impraticável, pois resultaria em um grande número de VLANs para gerenciar.
Alternativa correta
Criar uma VLAN separada para cada tipo de dispositivo na sala.
 
Criar uma VLAN separada para cada tipo de dispositivo na sala não seria útil neste cenário específico, pois não é a tipologia do dispositivo que estamos tentando isolar, mas sim grupos de estudantes realizando a mesma prova.
Alternativa correta
Criar uma única VLAN para todos os estudantes.
 
Uma única VLAN para todos os estudantes não melhoraria a segurança. Se um estudante conseguir comprometer a rede, todos os outros na mesma VLAN seriam afetados.
Alternativa correta
Criar uma VLAN separada para cada grupo de estudantes realizando a mesma prova.
 
Criar uma VLAN separada para cada grupo de estudantes realizando a mesma prova aumentaria a segurança. Isso garantiria que cada grupo só pudesse acessar os recursos de rede relevantes para a sua prova específica, minimizando a chance de comprometer a integridade da prova. Além disso, reduziria o risco de vazamento de informações entre diferentes grupos de estudantes.
Alternativa correta
Não usar VLANs, pois elas não melhoram a segurança da rede.

@@06
Para saber mais: Protocolo DTP x Modo de operação das portas do switch

Os switches são equipamentos de rede essenciais que permitem a comunicação e a conexão de diferentes dispositivos em uma mesma rede. Para garantir a utilização adequada de switches, especialmente em redes VLAN (Virtual Local Area Network), é importante garantir que a rede seja eficiente, e ao mesmo tempo segura. Para auxiliar neste processo podemos utilizar o Protocolo DTP (Dynamic Trunking Protocol) e atuar nos modos de operação das portas de um switch!
Por exemplo, vamos considerar o ambiente de uma universidade. A universidade possui diversos departamentos e laboratórios, cada um com suas necessidades específicas de rede. Usando VLANs, seria possível isolar a rede de cada departamento e laboratório, garantindo que o tráfego de dados de cada um seja segmentado de forma adequada. Isso é especialmente útil para laboratórios de pesquisa que podem ter dados sensíveis a serem protegidos.

Contudo, todos os departamentos ainda precisam acessar recursos compartilhados, como por exemplo, o uso de serviços de impressão. O protocolo DTP e a correta configuração dos modos de operação das portas dos switches podem nos auxiliar nesta tarefa!

Você pode configurar os links entre os switches como troncos utilizando o DTP, permitindo que várias VLANs se comuniquem através de um único link físico. No entanto, para manter a segurança, as portas podem ser configuradas para "operação de acesso", de modo que apenas a VLAN designada para essa porta possa utilizá-la.

Portanto, utilizando switches, VLANs e o protocolo DTP, é possível criar uma rede eficiente e segura numa universidade, onde cada departamento tem acesso aos recursos necessários, mas seu tráfego de dados permanece isolado dos demais.

O DTP é um protocolo proprietário da Cisco usado para negociar o encapsulamento e a formação de links de tronco entre switches da Cisco. Troncos são links que carregam o tráfego de várias VLANs entre switches. Normalmente, o DTP é usado quando a rede precisa ser flexível e se adaptar a mudanças, como a remoção ou adição de VLANs.

Já o modo de operação das portas de um switch é uma configuração fundamental que determina como a porta irá funcionar, especialmente em relação às VLANs. As portas podem ser configuradas como access (acesso), que carregam o tráfego de apenas uma VLAN, ou como trunk (tronco), que carregam o tráfego de várias VLANs. Esses modos são importantes para controlar a distribuição do tráfego de rede e isolar adequadamente as VLANs para segurança.

O Protocolo DTP é um protocolo de gerenciamento de camada 2 que opera em switches Cisco. Ele permite a um switch negociar automaticamente a formação de um link tronco com um switch adjacente (próximo).

Por outro lado, o modo de operação das portas de um switch define como as portas interagem com a VLAN e o tráfego. As portas configuradas como access atribuem uma VLAN específica a uma porta e todo o tráfego que entra ou sai daquela porta pertence a essa VLAN. As portas configuradas como trunk podem carregar tráfego de várias VLANs simultaneamente, usando etiquetas de VLAN para distinguir o tráfego entre as VLANs .

Você pode se aprofundar ainda mais sobre esses assuntos! Confira os documentos oficiais da Cisco:

Para conhecer mais sobre o uso do Protocolo DTP confira esse Dynamic Trunking Protocol (DTP) - Cisco.

Para se aprofundar nos conceitos a respeito do uso do Protocolo DTP confira esse link - Configuring VLAN Trunks - Cisco.

Vou deixar também essa referência sobre o tema com a publicação de um trabalho acadêmico em um congresso:

STEIN, MARCUS VINÍCIUS SALING; MOREIRA, João Padilha. SEGURANÇA EM CAMADAS DE REDES 2 e 3. SEMINÁRIO DE TECNOLOGIA GESTÃO E EDUCAÇÃO, v. 3, n. 2, 2021.

https://study-ccna.com/dynamic-trunking-protocol-dtp-cisco/

https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst2960cx_3650cx/software/release/15-2_3_e/configuration/guide/b_1523e_consolidated_2960cx_3560cx_cg/b_consolidated_152ex_2960-X_cg_chapter_0111110.pdf

@@07
Conectando VLANS

Construímos nossas VLANs: uma para o segmento administrativo e outra para o segmento da pesquisa. No entanto, enfrentamos um problema: não conseguimos realizar a comunicação entre PCs que estão em VLANs diferentes.
Uma das soluções é realizar o roteamento entre essas VLANs. Para isso, precisaremos de um dispositivo conhecido, o roteador.

Voltando ao Cisco Packet Tracer, acessaremos a barra de botões inferior e clicaremos no botão no canto direito, denominado "Network Devices" (Dispositivos de Rede). Abaixo dele, clicaremos no botão "Routers" (Roteadores) e à direita, selecionaremos um roteador. Pode ser o 1841.

Voltando à tela dos ambientes, clicaremos acima da linha pontilhada que liga os dois switches para posicionar o roteador ali. Ele possui o nome "1841 Router".

Vamos conectar esse roteador no switch A usando um cabo direto. Trata-se de dispositivos de redes diferentes, portanto possuem placas de rede diferentes. Neste caso, podemos utilizar um cabo deste tipo.

Para isso, acessaremos novamente a barra de botões inferior e clicaremos no quarto botão a partir da esquerda, denominado "Connections". À sua direita, selecionaremos o "Copper Straight-Through" (Cabo direto).

Na tela principal, clicaremos no roteador e selecionaremos a opção "FastEthernet0/0". Vamos mover o cursor até o switch A e clicar nele, selecionando a opção "FastEthernet0/4". Com isso, posicionamos uma linha preta entre ambos, que representa o novo cabo.

Por padrão, o roteador possui sua interface desabilitada. Para habilitá-la, faremos um processo conhecido, clicando com o botão direito no roteador, acessando a aba "CLI" na janela que será exibida, e entrando no prompt.

Em seu interior, veremos uma pergunta padrão questionando se queremos configurar no modo diálogo. Vamos respondê-la com um no e um "Enter".

Vamos escalar os privilégios como feito nos switches, rodando em sequência os comandos enable e configure terminal.

enable
COPIAR CÓDIGO
configure terminal
COPIAR CÓDIGO
Vamos entrar na interface conectada no switch, neste caso, a FastEthernet 0/0.

interface Fa 0/0
COPIAR CÓDIGO
Vamos pedir um no shutdown, ou seja, pediremos para que essa porta não seja desativada.

no shutdown
COPIAR CÓDIGO
Na tela principal, o ficou verde. Com isso, esta porta está funcionando.

Vamos pensar em outra questão: teremos mais de 600 computadores conectados nessa rede. A atribuição estática da forma que estamos fazendo não será eficaz.

Teremos que configurar uma atribuição dinâmica com o DHCP. Para isso, rodaremos um exit para voltar ao módulo "config". Em seguida, rodaremos o comando ip dhcp pool e vamos configurar o primeiro pool para a VLAN 10.

ip dhcp pool vlan10
COPIAR CÓDIGO
Com isso, acessaremos o módulo "dhcp-config". Configuraremos com o comando network e estabeleceremos um endereço de rede para a VLAN 10, que será 192.168.10.0. À direita, devemos acrescentar a máscara de rede. Como se trata de um endereço da classe C, temos os três primeiros octetos com "255" e o último com "0", formando 255.255.255-0.

network 192.168.10.0 255.255.255-0
COPIAR CÓDIGO
Após o "Enter", faremos o mesmo processo, acessando o código ip dhcp pool vlan10 com a seta para cima do teclado para facilitar. Basta trocar a vlan10 por vlan20.

ip dhcp pool vlan20
COPIAR CÓDIGO
Pressionaremos "Enter" e usaremos o comando network 192.168.10.0 255.255.255-0 mudando o terceiro octeto de 10 para 20 e pressionando "Enter" novamente.

network 192.168.20.0 255.255.255-0
COPIAR CÓDIGO
Faremos um exit. Com isso, configuramos os pools DHCP, um para cada VLAN que temos na rede.

Vamos realizar uma análise: será que a única interface com a qual estamos conectando o roteador no switch A é capaz de fornecer os dois pools DHCP para as duas VLANs diferentes? A resposta é não.

Para isso, teremos que usar um conceito diferente, o de subinterface. É como se fracionássemos uma única interface em interfaces diferentes, uma para cada VLAN.

Como fazemos a configuração da subinterface? Devemos criá-la.

Ainda no prompt CLI, no módulo atual ("config"), rodaremos o comando interface Fa 0/0, onde Fa é a abreviação de FastEthernet. Em vez de 0/0 escreveremos 0/0.1. É como se estivéssemos criando uma subinterface a partir da interface física.

interface Fa 0/0.1
COPIAR CÓDIGO
Após o "Enter", veremos que a subinterface foi criada e que entramos no módulo "config-subif".

%LINK-5-CHANGED: Interface FastEthernet0/0.1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/0.1, changed state to up
COPIAR CÓDIGO
Digitaremos o comando encapsulation dot1Q 10, que vincula ou encapsula essa subinterface na VLAN 10.

encapsulation dot1Q 10
COPIAR CÓDIGO
Após o "Enter", temos que atribuir um endereço IP para essa subinterface. Para isso, rodaremos o comando ip address junto ao endereço IP 192.168.10.1, o primeiro dessa VLAN.

Além disso, ele pedirá a máscara de rede padrão da classe C: 255.255.255-0.

ip address 192.168.10.1 255.255.255-0
COPIAR CÓDIGO
Pressionaremos "Enter" e teremos feito um comando bem-sucedido. Vamos rodar um exit para retornar ao módulo "config".

Agora faremos o mesmo processo, criando dessa vez uma subinterface dedicada à VLAN 20, do setor administrativo. Em vez de 0/0.1 escreveremos 0/0.2

interface Fa 0/0.2
COPIAR CÓDIGO
Vamos encapsulá-la acessando o comando encapsulation dot1Q 10 com a seta do nosso teclado e alterando de 10 para 20.

encapsulation dot1Q 20
COPIAR CÓDIGO
Por fim, utilizaremos o mesmo comando ip address, atribuindo desta vez o IP 192.168.20.1 primeiro endereço de rede do IP que corresponde à VLAN 20.

ip address 192.168.20.1 255.255.255-0
COPIAR CÓDIGO
Configuramos a segunda subinterface. Vamos rodar um exit para voltar ao módulo "config".

Quando configuramos sub-redes, precisamos indicar qual o portão de saída delas. Vamos realizar esse mesmo processo aqui.

Vamos entrar no pool "dhcp-config" executando o comando ip dhcp pool vlan10.

ip dhcp pool vlan10
COPIAR CÓDIGO
Nele, utilizaremos o comando default-router, indicando junto dele quem será esse roteador padrão. Para a VLAN 10, será a própria subinterface 1 que criamos para ela.

Neste caso, não é necessário informar a máscara de rede.

default-router 192.168.10.1
COPIAR CÓDIGO
Após pressionarmos "Enter", faremos um exit para retornar ao módulo "config". Vamos entrar agora no DHCP da VLAN 20 por meio do comando abaixo.

ip dhcp pool vlan20
COPIAR CÓDIGO
Faremos o mesmo processo nele, rodando o default-router com o IP da subinterface 192.168.20.1.

default-router 192.168.20.1
COPIAR CÓDIGO
Após a execução com "Enter", faremos um exit.

Podemos fechar a janela do roteador e voltar à tela principal para fazer um teste de conectividade e verificar se essas VLANs diferentes possuem comunicação.

Vamos clicar no computador do pesquisador A para abrir a sua janela.

Precisamos lembrar que todos os nossos computadores estão configurados para a locação de IP de modo estático. Temos que realizar uma requisição de DHCP em cada um deles, acessando a aba "Desktop" a opção "IP Configuration".

Na seção "Ip Configuration" devemos selecionar o botão rádio da opção "DHCP" para ativá-la no lugar da opção "Static". Com isso, a mensagem "Requesting IP Address" (Requisitando Endereço IP) aparecerá à esquerda, seguida da mensagem "DHCP request successful" (Requisição DHCP bem-sucedida).

Abaixo dos botões "DHCP" e "Static", veremos a seção "Default Gateway" com o nosso IP "192.168.10.1". Podemos fechar a janela do computador do pesquisador A e fazer o mesmo processo selecionando "DHCP" nos demais coomputadores da rede.

O último a ser configurado será o computador do pesquisador B. Em sua janela, na guia "Desktop" e abaixo dos botões "DHCP" e "Static", veremos a seção "IPv4 Address", a qual exibe o IP que esse computador recolheu na rede: "192.168.20.3".

Vamos utilizar esse endereço para realizar um teste de conectividade. Devemos lembrar que o computador da coordenação está no VLAN do setor administrativo.

Vamos clicar no computador do pesquisador A para abrir novamente a sua janela. Na guia "Desktop", na opção "Command Prompt" que abre o prompt, faremos um ping para 192.168.20.3.

ping 192.168.20.3
COPIAR CÓDIGO
Vamos verificar se temos conectividade entre computadores e VLANs diferentes. O primeiro não deu certo, mas a partir do segundo funcionou. Ou seja, conseguimos resolver nosso problema.

Pinging 192.168.20.3 with 32 bytes of data:

Request timed out.
Reply from 192.168.20.3: bytes=32 time<lms TTL=127
Reply from 192.168.20.3: bytes=32 time<lms TTL=127
Reply from 192.168.20.3: bytes=32 time<lms TTL=127

Ping statistics for 192.168.20.3:
    Packets: Sent = 4, Received 3, Lost = 1 (25% loss),
Approximate round trip times in milli-seconds:
    Minimum = Oms, Maximum = Oms, Average = Oms
COPIAR CÓDIGO
Vamos fechar essa janela e observar o seguinte: vimos anteriormente que quando temos uma conexão entre dispositivos de redes diferentes, precisamos configurar essa interface para funcionar no modo trunk, permitindo que todas as VLANs passem.

Contudo, não fizemos isso aqui no roteador, pois os dispositivos da Cisco possuem o protocolo DTP (Dynamic Trunking Protocol) pertencente ao proprietário desse fabricante de dispositivos de rede. Ele configura automaticamente as portas para funcionarem no modo trunk quando não atribuímos a elas o modo access.

No caso anterior, desabilitamos esse modo para verificar como devemos configurar os dispositivos de rede que por ventura estivéssemos configurando.

Resta uma questão: será que é possível criar um tipo de redundância para manter a conectividade entre esses dispositivos de uma rede, caso algum link ou cabo de conexão deles caia? Vamos verificar na sequência.

@@08
Roteamento/subinterfaces

Uma instituição de ensino superior está realizando um congresso. Por isso, é importante gerenciar o roteamento e as sub-interfaces para que os dispositivos de todas as pessoas convidadas externas tenham acesso à web.
Qual seria a maneira ideal para gerenciar o roteamento e as sub-interfaces atendendo as demandas do congresso?

Configurar uma única subinterface para todos os convidados e rotear todos os dispositivos através dela.
 
Alternativa correta
Configurar uma subinterface separada para cada convidado.
 
Alternativa correta
Configurar uma subinterface para cada tipo de dispositivo que os convidados possam trazer.
 
Alternativa correta
Configurar uma subinterface para todos os convidados e implementar um roteamento dinâmico.
 
Configurar uma subinterface para todos os convidados e implementar um roteamento dinâmico oferece a melhor solução. Uma única subinterface simplifica a gestão da rede, enquanto o roteamento dinâmico permite que ela acomode automaticamente as mudanças no tráfego, melhorando a eficiência e o desempenho.
Alternativa correta
Configurar uma subinterface para cada convidado, mas rotear todos os dispositivos através de uma única subinterface.

@@09
Portas trunk

Portas trunk são conexões entre sistemas de telecomunicações que permitem a transmissão simultânea de várias chamadas telefônicas ou canais de comunicação de dados. É necessário configurar as portas trunk na biblioteca de uma instituição de ensino superior para permitir o acesso adequado à rede para professores e estudantes.
Como as portas devem ser configuradas?

Devemos configurar uma única porta trunk e usar VLANs para separar o tráfego de rede.
 
Configurar uma única porta trunk e usar VLANs para separar o tráfego de rede é a melhor opção. Isso permitiria a separação adequada do tráfego de rede para professores, alunos e convidados, garantindo que cada tipo de usuário tenha o acesso adequado. Ao mesmo tempo, simplifica o gerenciamento da rede e faz uso eficiente dos recursos de um switch.
Alternativa correta
Devemos configurar uma única porta trunk para todos os usuários.
 
Alternativa correta
Não devemos usar portas trunk, pois elas não são úteis para separar o tráfego de rede.
 
Alternativa correta
Devemos configurar uma porta trunk separada para cada tipo de usuário.
 
Alternativa correta
Devemos configurar uma porta trunk para cada usuário individual.

@@10
Faça como eu fiz: criando e configurando VLANS

Vamos iniciar nosso projeto inserindo dois computadores no Laboratório A e outros dois computadores no Laboratório B.
Na sequência, insira dois Switches (modelo 2950-24) - um que ficará na sala de finanças e outro que ficará na sala de vendas.

Por fim, realize a conexão dos Switches com os computadores, usando um cabo direto e a conexão entre os Switches usando um cabo crossover.

Devemos agora configurar as vlans em cada um dos switches. Iremos adotar a Vlan 10 para o segmento de pesquisa do Instituto Inovae e a Vlan 20 para o segmento administrativo. Para isso, vamos realizar as seguintes etapas de configuração e análise nos switches inseridos nos laboratórios A e B:

Clique no Switch e, em seguida, clique na aba CLI;
Entre no modo privilegiado digitando enable;
Acesse as opções de configuração digitando configure terminal;
Vamos criar a vlan de pesquisa digitando vlan 10 e, na sequência, name pesquisa;
Uma vez que a Vlan 10 foi criada, devemos sair da configuração da vlan digitando o comando exit;
Vamos criar a vlan do segmento administrativo digitando vlan 20 e, na sequência, name administrativo;
Podemos observar se a configuração das vlans foi realizada corretamente. Vamos digitar o comando exit para sairmos da configuração da vlan e o comando “crtl + z” para retornar ao menu anterior. Na sequência, vamos inserir o comando show vlan brief e analisar o resultado apresentado.
Observação: Agora, além das vlans nativas e reservadas, temos as vlans pesquisa e administrativo configuradas no switch;

Será que está tudo certo?

Ainda precisamos alterar as interfaces conectadas aos computadores para trabalharem nas respectivas vlans.

Para isso, vamos retornar ao modo de configuração com o comando configure terminal e entrar em cada interface com o comando interface Fa 0/2;

Observação: Note que usamos o mesmo comando para configurar as interfaces, mudando apenas o número da interface. Estamos iniciando pela interface Fa 0/2 por livre escolha. Poderíamos ter iniciado pela interface Fa 0/3. O termo “Fa” é uma abreviação para Fast ethernet, bem mais simples de digitar, não é mesmo!?

Ao entrarmos na interface desejada, digitamos o comando switchport mode access para especificar que essa interface irá operar em modo de acesso, fazendo a conexão do switch com um dispositivo final.

Na sequência, vinculamos a interface a sua respectiva vlan de trabalho com o comando switchport access vlan 10.

Observação: Vamos repetir essas etapas para computador conectado, no entanto a vinculação da interface com a vlan varia em função do computador que estamos configurando. Os computadores usados por pesquisadores estarão na vlan 10 da pesquisa, enquanto os computadores utilizados por coordenadores e técnicos administrativos estarão na vlan 20 do segmento administrativo.

Após configurarmos as interfaces de cada computador nos dois switches, é hora de realizar um teste de conectividade utilizando o comando ping no prompt de comando de cada computador.

Mas, atenção: antes, não se esqueça de atribuir um endereço IP para cada computador conectado na rede.

Basta clicar em cada PC, aba Desktop e, por fim, na opção IP Configuration para inserir um IP de modo estático. No exemplo, inserimos um endereço do tipo 193.165.0.X, em que X no último octeto aponta o endereço individual de cada PC (193.165.0.1, 193.165.0.2, 193.165.0.3 e 193.165.0.4).

Opinião do instrutor

Não foi necessário configurar a interface que conecta os dois switches para operar no modo trunk, pois os dispositivos da Cisco já vem com a configuração do protocolo DTP. Caso contrário, seria necessário entrar na interface e digitar o comando switchport mode trunk.
No teste de conectividade, você deve ter reparado que há conexão apenas entre os computadores conectados na mesma vlan. Isso se deve ao fato de que as vlans operam como “redes diferentes”. Dessa forma, para realizarmos a conexão entre computadores conectados em diferentes vlans, precisamos de roteamento.

@@11
Faça como eu fiz: conectando VLANS

Para realizarmos a conexão entre as Vlans precisaremos de roteamento. É importante notar que há Switches capazes de realizar o roteamento, sendo conhecidos como Switches camada 3 justamente por combinarem as funcionalidades de switch e roteador (atuando nas camadas 2 e 3 do modelo OSI).
No projeto do Instituto Inovae, estamos usando switches camada 2 que só atuam como comutadores de rede. Sendo assim, precisaremos inserir um roteador.

Nossa tarefa aqui será dividida em algumas partes para facilitar a organização da implementação.

Parte 1 - Inserindo o roteador na rede

Vamos inserir o roteador modelo Cisco 1841, selecionando o equipamento no menu, arrastando e soltando na área de trabalho;

Na sequência, conecte o roteador com o Switch de um dos laboratórios usando cabo direto;

Clique no roteador e vá até a aba CLI;

Caso apareça uma mensagem perguntando se queremos habilitar o modo diálogo, digitamos no;

Posteriormente, devemos entrar na parte privilegiada, digitamos enable e, em seguida, digitamos configure terminal para acessar o modo de configuração;

Entre na interface do roteador que foi conectada com Switch (por exemplo: interface FastEthernet 0/0), com o comando interface Fa 0/0;

As portas dos roteadores empresariais da Cisco vem desabilitadas por padrão, devemos habilitá-las, então digitamos: no shutdown.

Parte 2 - Configurando o protocolo DHCP

A interface ficou verde, a porta está habilitada! Teremos muitos computadores na nossa rede, não é mesmo!? É inviável pensar em uma atribuição de endereços de modo estático. O roteador deve fornecer de modo automático usando o DHCP. Como temos duas vlans, precisamos criar dois tipos de endereços IP.

Vamos criar dois pool dhcp para entregar endereços para essas duas vlans. Confira a sequência:

Vamos clicar no roteador e na aba CLI;

Acesse o modo de configuração usando o comando configure terminal e digite o comando ip dhcp pool vlan 10 para criar um pool dhcp;

Agora, vamos configurar o pool dhcp que acabamos de criar com o comando network 192.168.10.0 255.255.255.0. Estamos informando a rede na qual a vlan 10 estará inserida. Note que estamos usando um endereço IP da classe C;

Digite o comando exit e crie um pool dhcp para a vlan 20;

Para isso, use o comando ip dhcp pool vlan 20 e especifique a rede na qual a vlan 20 estará inserida com network 192.168.20.0 255.255.255.0.

Parte 3 - Configurando subinterfaces

Acabamos de configurar o funcionamento do DHCP em nossa rede e surge uma questão: será que uma única interface (Fa 0/0) consegue entregar dois tipos de endereços IP diferentes?

A resposta é não, sendo assim vamos precisar dividir essa interface, usando o conceito de subinterfaces. A solução que adotamos consiste na criação de uma subinterface dedicada para a vlan da pesquisa e outra para a vlan do administrativo.

Acesse o modo de configuração do roteador com o comando configure terminal e digite o comando **interface Fa 0/0.1” para criação da primeira subinterface;

Vamos configurar a subinterface criada com o comando encapsulation dot1Q 10 e, na sequência, digite o comando ip address 192.168.10.1 255.255.255.0 para designar seu endereço IP;

Agora, digite o comando exit e, em seguida, o comando interface Fa 0/0.2 para criar outra subinterface;

Configure a subinterface com o comando encapsulation dot1Q 20 e, na sequência, digite o comando ip address 192.168.20.1 255.255.255.0 para designar seu endereço IP;

Mais uma vez, digite o comando exit para sair da configuração da subinterface;

Para concluirmos o processo de configuração, precisamos definir o default gateway de cada vlan. O default gateway opera como o “portão de saída” de cada rede, as subinterfaces que acabamos de configurar irão cumprir esse papel para cada vlan.

No modo de configuração, digite o comando ip dhcp pool vlan 10 e, em seguida, designe o default gateway com o comando default router 192.168.10.1;

Vamos repetir o processo para a subinterface 2 com o comando ip dhcp pool vlan 20 e, na sequência, default router 192.168.20.1;

Finalizando as configurações de conexão entre as vlans, vamos clicar em cada PC e na opção IP Configuration mudar a atribuição de IP de estática para dinâmica. Observe que nas requisições DHCP para cada máquina, o default gateway é preenchido automaticamente;

Teste a conectividade entre os computadores usando o comando ping no prompt de comando de cada PC.

Finalmente conseguimos realizar a conexão entre computadores conectados em diferentes vlans. Conseguimos enviar dados entre os diferentes PCs que inserimos nos Laboratórios A e B!
Observe que não foi necessário configurar a interface do switch conectada ao roteador para operar no modo trunk devido ao protocolo DTP da Cisco. No entanto, em outros dispositivos de rede, eventualmente pode ser preciso a configuração desse modo.

@@12
O que aprendemos?

Nessa aula, você aprendeu:
O que são lans virtuais e as principais vantagens de seu uso em um projeto de redes;
Como criar uma vlan e configurar o seu funcionamento usando dispositivos de rede como switches e roteadores;
Como conectar e operar vlans diferentes criadas para segmentação de uma rede em setores conforme demandas definidas nos requisitos do projeto.