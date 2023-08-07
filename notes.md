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

#### 07/08/2023

@01-Configurando subredes de modo eficiente

@@01
Redundância de links com STP

Ficamos com uma pergunta: o que aconteceria, por exemplo, se alguém tropeçasse acidentalmente em um desses links de conexão entre um switch e outro, ou entre um switch e um roteador?
Simplesmente ficaríamos sem rede, perderíamos todo o acesso de um determinado setor ou laboratório à internet ou a outros setores da empresa. Uma forma de resolvermos esse tipo de situação é inserir redundância na rede.

Redundância de links com STP
Para fazer isso, poderíamos adicionar um terceiro switch C, fazer a conexão desse switch C com o roteador, e realizar uma conexão entre os três switches da nossa rede.

Vamos testar isso?

No exemplo que estamos construindo, vamos selecionar um switch semelhante aos demais que selecionamos, o modelo 2950-24. Faremos a desconexão entre o roteador e o Switch_A, e em seguida criaremos uma nova do tipo "Copper Cross-Over" entre o Switch_A e esse novo switch, usando a porta FastEthernet0/4 no primeiro e FastEthernet0/2 no segundo.

Depois, faremos uma conexão do Switch_B com o novo switch usando as portas FastEthernet0/4 e FastEthernet0/4 respectivamente.

Por fim, faremos uma conexão do mesmo tipo entre o novo switch, partindo da porta FastEthernet0/1 com a porta FastEthernet0/0 do roteador.

Além disso, vamos renomear o novo switch para Switch_C.

Agora precisamos repetir todo o processo de configuração do switch, de tal forma que nossas VLANs estejam configuradas corretamente. Vamos começar com o comando enable em uma primeira linha, seguido de configure terminal na próxima.

enable
COPIAR CÓDIGO
configure terminal
COPIAR CÓDIGO
Em seguida, usamos o comando vlan 10, e na sequência, o name pesquisa. Uma vez configurado, digitamos o comando exit, seguido de vlan 20 na próxima linha. Depois configuramos com name administrativo, e finalizamos com o comando exit.

vlan 10
COPIAR CÓDIGO
name pesquisa
COPIAR CÓDIGO
exit
COPIAR CÓDIGO
vlan 20
COPIAR CÓDIGO
name administrativo
COPIAR CÓDIGO
exit
COPIAR CÓDIGO
Já sabemos que não precisamos configurar as portas trunk porque, nos equipamentos da Cisco, temos o protocolo DTP (Dynamic Trunking Protocol - Protocolo de Troncalização Dinâmica).

Vamos fazer um teste para conferir se tudo na nossa rede funciona corretamente e se não quebramos nenhuma configuração: faremos um ping do Pesquisador_A para o Pesquisador-B. Usaremos o endereço de IP de Pesquisador-B, que é 192.168.10.3.

ping 192.168.10.3
COPIAR CÓDIGO
Tudo deverá funcionar corretamente. Também podemos fazer um ping para o computador da coordenação, que é 192.168.20.3.

ping 192.168.20.3
COPIAR CÓDIGO
Funciona corretamente da mesma forma. Porém, há um detalhe: a conexão que parte da porta do Switch_A está laranja. Será que isso representa algum tipo de problema na nossa rede ou está tudo funcionando normalmente? Não há nada de errado com essa marcação. Na verdade, acabamos de criar uma malha na nossa rede.

O que aconteceria se um ping vindo de uma rede externa chegasse nessa malha? Geralmente, o ping tem um TTL (Time To Leave - Tempo Para Sair). O TTL contabiliza por quantos dispositivos de rede o pacote passou. Porém, o único dispositivo de rede que tem a capacidade de decrementar o TTL são os roteadores.

Os switches não possuem essa habilidade de decrementar uma mensagem. Dessa forma, se uma mensagem chega no switch, ela circulará causando congestionamento.

Para solucionar esse tipo de problema, temos um protocolo específico que é o STP (Spanning Tree Protocol). É esse o protocolo que está atuando na nossa malha e desativando a porta Switch_A, para impedir a formação do ciclo onde uma mensagem ficaria eternamente circulando entre os dispositivos de rede.

Mas como funciona o protocolo STP?

Ele funciona elegendo um switch da malha que vai atuar como principal, e para fazer essa seleção do principal (ou switch root), é necessário ter uma troca de mensagens entre os switches da rede. No contexto de uma rede, sempre que falamos em troca de mensagens, temos um protocolo rodando por trás. Nesse caso, o protocolo BPDU (Bridge Protocol Data Unit).

Para ilustrar o conceito do protocolo BPDU, preparamos o esquema abaixo:

Esquema STP triangular formado por três switches: Switch ADM no topo, Switch MKT na ponta esquerda, e Switch RH na ponta direita. Ao lado dos switches, estão os endereços "MAC 22.22.22.22.22.22", "MAC 33.33.33.33.33.33", e "MAC 11.11.11.11.11.11". Em cada linha de conexão há a inscrição "1 Gps". À direita do esquema, há um retângulo intitulado "BDPU - Bridge Protocol Data Unit", contendo dois retângulos menores dispostos lado a lado, intitulados "Prioridade 32.768" e "Endereço MAC", da esquerda para a direita.

Esse protocolo é acionado quando formamos uma ponte na rede. Essa mensagem tem dois campos, um campo de prioridade e um campo de endereço MAC.

Endereço MAC é o endereço físico que todos os dispositivos que têm uma placa de rede possuem, atribuído por padrão pelo respectivo fabricante.

Nesse protocolo, os dispositivos vão trocar mensagem e a seleção do root será baseada em quem tiver a menor prioridade. No STP, a lógica é "quanto menor, melhor". O switch que tiver a menor prioridade será eleito como root ou switch principal.

Perceba que, no esquema, colocamos o valor de 32.768 na prioridade, e isso não é por acaso. Esse é o valor padrão que vem no switch como prioridade. Se ninguém o alterou, essa é a prioridade padrão, e se todos têm a mesma prioridade, a seleção do switch root será feita por meio da observação do endereço MAC. Como todos os dispositivos possuem endereço MAC diferente, o switch eleito como root será aquele que tiver o menor endereço MAC.

No nosso caso, se observarmos que os switches de ADM, do RH e do MKT têm a mesma prioridade padrão, o switch root, hipoteticamente, seria o Switch RH com o endereço MAC 11.11.11.11.

Mas, nesse caso, ele não é o switch principal, porque temos uma porta desabilitada e esse é um detalhe importante do switch root: ele tem o privilégio de ser o switch principal da rede, ou seja, ele tem a conexão e acaba concentrando todo o tráfego que chega para determinada rede.

Todas as portas do switch root são designadas, portas pelas quais temos um tráfego de dados de entrada e de saída, tanto da rede quanto desse switch para outros switches que estão interligados com ele.

Se temos um switch que tem as portas designadas e com todas as suas portas no modo ativo, como será a determinação da porta que vai ficar inativa?

Os demais switches vão fazer um cálculo, ou seja, vão analisar qual porta vão utilizar para fazer a conexão com o switch root. Como eles fazem isso? Analisando a velocidade de cada link. Eles têm uma tabela de conversão entre a velocidade de conexão e o custo dessa conexão.

Em geral, quanto maior a velocidade de conexão, menor o custo, e segundo o STP, a lógica é "quanto menor, melhor". Se for menor o custo, a porta será eleita como a porta de acesso ao switch root.

No esquema exibido acima, colocamos o valor como 1 Gps, que é uma velocidade de conexão. Então, verificaríamos essa conversão na tabela de custo e seria eleita a porta de acesso ao root, que se chama porta root.

Por fim, a porta que tiver o maior custo, como, por exemplo, a Switch RH, acaba sendo desativada. Porém, se alguém, por exemplo, tropeçar no link entre Switch ADM e Switch RH, automaticamente o STP vai acionar a porta esquerda do Switch RH, que está inativa por enquanto e marcada em laranja no esquema.

Isso irá manter a conectividade e a interligação entre esses dispositivos de rede, que têm outros PCs e outros computadores interligados.

Com isso, nós não perdemos a conexão se um dos links cair.

Agora, se voltarmos ao nosso projeto da rede do Instituto Inovae, agora que já entendemos bem como funciona o STP, como verificar quem é o root da rede?

Podemos clicar, por exemplo, no Switch_B e acessar a aba do CLI. Vamos usar o comando show spanning-tree vlan 10 após habilitarmos o CLI com o comando enable.

enable
COPIAR CÓDIGO
show spanning-tree vlan 10
COPIAR CÓDIGO
Com esse comando, teremos toda uma análise, um relatório de quais portas são portas designadas, e podemos identificar primeiro a prioridade desse switch.

VLAN 0010
  Spanning tree enabled protocol ieee
  Root ID    Priority    32778
             Address     0005.5E44.45D1
             Ths bridge is the root
COPIAR CÓDIGO
Observe que a prioridade não é exatamente 32.768, mas sim 32.778. Por que há essa diferença? Isso ocorre porque o sistema está somando o valor padrão com 10, que é o valor que estipulamos para a VLAN.

Além disso, é exibida a mensagem "This bridge is the root", ou seja, "esta ponte é a raiz". Isso significa que o Switch_B, que possui as duas portas designadas, é o switch raiz da nossa rede.

Agora surge a pergunta: como o switch raiz acaba concentrando todo o tráfego da rede, será que se um switch de menor porte eventualmente se tornar o switch raiz — de acordo com o padrão do STP —, conseguiremos alterar essa configuração para indicar outro switch em nossa rede como switch raiz? A resposta é que sim, é possível!

Para isso, basta inserir o comando Priority 0 em determinado switch. Se algum switch que não tem uma boa capacidade para gerenciar o tráfego acaba sendo selecionado como switch raiz, nós podemos alterar isso. Basta acessar a aba CLI do switch e indicar qual switch desejamos selecionar como raiz, atribuindo Priority 0 àquele switch para a VLAN correspondente.

Conclusão
Surge uma nova pergunta: se teremos mais de 600 dispositivos na nossa rede, haverá endereço IP para todos? Para responder a essa questão, será necessário analisar a disponibilidade de endereços. Faremos isso na sequência!

@@02
Para saber mais: importância do STP

Em redes de computadores, especialmente aquelas que usam redes cabeadas no padrão ethernet, uma situação muito conhecida durante a implementação de redundâncias é loop de uma rede. Este loop pode causar problemas de desempenho e eventualmente, paralisar a rede por completo.
Por exemplo: Imagine que somos responsáveis por configurar uma rede típica de um laboratório de pesquisa. Em um laboratório pode haver vários switches conectados para garantir que uma variedade de dispositivos, incluindo computadores de pesquisa, servidores de dados e instrumentação científica, estejam devidamente configurados em uma mesma rede. Agora, imagine que, para fornecer redundância e garantir que a rede esteja sempre disponível, seja necessário conectar os switches alocados no laboratório seguindo uma topologia de anel. Isto é, cada switch está conectado a dois outros switches, formando um loop.

Vamos supor que um pacote de dados é enviado de um computador em um canto do laboratório para um servidor do outro lado. Nesta situação, os switches começam a encaminhar pacotes através da rede. No entanto, devido à topologia em anel, os pacotes podem continuar a ser encaminhado em um loop infinito entre os switches.

Para evitar esse problema, o Spanning Tree Protocol (STP) foi desenvolvido e é frequentemente utilizado em redes que recorrem a topologia de malha ou em redes com links redundantes, pois ajuda a evitar os loops e garante a disponibilidade da rede.

Loops de rede ocorrem quando existem múltiplos caminhos entre dois pontos da rede, o que pode ocasionar um volume muito intenso de tráfego (muitas vezes infinito), paralisando a rede.

O STP cria uma topologia de árvore abrangente, desabilitando os links redundantes. Ele elege um switch como raiz da árvore e calcula o caminho mais curto para cada parte da rede a partir desse switch raiz. Os links redundantes são colocados em um estado de bloqueio e só são ativados se o link ativo falhar. Dessa forma, o STP previne loops ao mesmo tempo em que fornece uma certa medida de redundância.

Para se aprofundar nos conceitos a respeito do uso do STP acesse Understanding Spanning−Tree Protocol Topology Changes - Cisco.

Para mais informações a respeito do processo de configuração do STP, acesse Spanning Tree Protocol (STP) Configuration - Grandmetric.

http://www.hit.bme.hu/~jakab/edu/litr/Ethernet/STP-conv.pdf

https://www.grandmetric.com/knowledge-base/design_and_configure/spanning-tree-protocol-stp-configuration/


@@03
Faça como eu fiz: criando redundância na rede

Vamos criar uma redundância em nossos links inserindo um terceiro Switch. Uma interface desse terceiro Switch será conectada ao roteador e outras duas interfaces serão conectadas a interfaces dos outros dois Switches já implementados.
Esse novo Switch deverá transportar dados da Vlan 10 e da Vlan 20.

O primeiro passo será criar essas Vlans no novo Switch, uma vez que elas não possuem tais Vlans configuradas. Para isso, vamos seguir a sequência:

Clicamos nesse novo Switch e selecionamos a aba CLI.

Entramos no modo privilegiado, digitando: enable e, posteriormente, entramos na parte de configurações com o comando configure terminal.

Criamos a vlan de pesquisa, digitando vlan 10 e, em seguida, name pesquisa. Na sequência, vamos criar também a vlan do administrativo com os comandos vlan 20 e name administrativo.

Posteriormente, deveríamos selecionar as interfaces para realizar a mudança do modo de operação para o encaminhamento dessas Vlans. Como estamos trabalhando com dispositivos da Cisco, não será necessário definir o modo de operação como trunk, permitindo o encaminhamento simultâneo das vlans que acabamos de configurar no Switch. O protocolo DTP está ativo por default e se encarrega de garantir esse modo de operação.

Opinião do instrutor

Uma vez que configuramos a Vlan 10 de pesquisa e a Vlan 20 do administrativo no novo Switch, tudo deverá estar funcionando como antes, mas agora temos uma redundância e caso algum desses links caia, teremos um outro de backup que irá assumir.

@@04
Análise de endereços IP

Temos mais de 600 computadores em nossa rede e uma das questões é: teremos endereços IP suficientes para alocar todas essas máquinas?
Análise de endereços IP
Para verificar isso, vamos referenciar o nosso projeto. Ao clicar com o botão direito sobre o roteador, é possível acessar as configurações em execução com o comando enable e depois show running-config.

enable
COPIAR CÓDIGO
show running-config
COPIAR CÓDIGO
Podemos observar que estamos utilizando um endereço de rede típico da classe C, que começa com o primeiro octeto entre 192 e 223. Vamos analisar quantos dispositivos essa classe de endereços IP nos permite endereçar.

Conforme vimos no primeiro curso de redes, os endereços da classe C se iniciam com 192 até 223 no primeiro octeto e possuem uma máscara de rede padrão de 255.255.255.0. Mas o que significa esse 0 no último octeto? Ele indica que este octeto é dedicado à identificação dos hosts, ou seja, dos dispositivos e máquinas que utilizamos na rede. Os demais octetos são utilizados para identificar a própria rede.

Observando o endereço que utilizado para a VLAN 10, temos o endereço de rede 192.168.10.0 e o endereço de broadcast 192.168.10.255. O endereço de broadcast é aquele que usamos para nos comunicar com todos os dispositivos na nossa rede.

Quantos endereços IP temos disponíveis?

Analisando o último octeto, temos 256 possibilidades de endereços IP, porém, há dois endereços dedicados e reservados: um para o broadcast e outro para a identificação da rede. Podemos considerá-los como limites inferior e superior dos endereços IP disponíveis. Portanto, só temos 254 endereços disponíveis para identificar nossos dispositivos.

Isso traz um problema: precisamos comportar 600 máquinas. Poderíamos pensar em alocar 400 máquinas na VLAN 10 da pesquisa e 400 na VLAN administrativa, por exemplo, de modo a atender a demanda dessas duas VLANs.

Nesse caso, a classe C não nos atenderia e precisaríamos analisar a próxima: a classe B.

Os endereços da classe B começam com o primeiro octeto de 128 a 191, com uma máscara de rede padrão de 255.255.0.0, ou seja, temos dois octetos para identificar os hosts em nossa rede.

Quantos endereços IP teremos disponíveis se utilizarmos a classe B?

Desde o início, utilizamos o termo octeto para nos referir ao endereço IP, composto do primeiro, segundo, terceiro e quarto octeto que constituem um endereço IP para uma máquina, rede ou broadcast. No entanto, temos utilizado sequências de no máximo três dígitos para representar os números em cada octeto. Assim, por que usamos o termo octeto?

Na verdade, usamos a base decimal na identificação dos endereços, pois é a base com a qual estamos mais acostumados no dia a dia, seja para contabilizar nosso rendimento, seja para contar itens que utilizamos frequentemente. Porém, no mundo da computação, a principal linguagem utilizada para representação dos dados é a binária.

Desse modo, a máscara de rede padrão da classe B, 255.255.0.0, na forma binária, é constituída por uma sequência de 1 e 0. Nota-se que 255 é o limite, ou seja, o maior número possível dentro de um octeto. Isso ocorre porque este é o maior número decimal que pode ser representado com oito bits em binário, por uma sequência de 1.

Como obter o valor de um número representado em binário?

Teremos uma atividade no decorrer do curso que permitirá um melhor entendimento, mas podemos adiantar que o valor representado por uma determinada sequência de algarismos em uma base depende da posição em que cada algarismo está na base.

Por exemplo: se convertermos o número 255 para uma soma de potências de 10, será 2 vezes 10 elevado a 2, mais 5 vezes 10 elevado a 1, mais 5 vezes 10 elevado a 0. Se fizermos essa soma, obteremos exatamente o valor 255 representado.

Se fizermos esse cálculo para um binário, começaremos com 1 vezes 2 elevado a 0, mais 1 vezes 2 elevado a 1, e assim sucessivamente, até obter o valor final 255 em uma sequência de 8 bits 1.

Agora que o termo octeto faz sentido para nós, vamos descobrir quantos endereços IP podemos conseguir com um endereço da classe B.

Conforme mencionado anteriormente e bastante estudado no curso 1, em uma máscara de rede, quando temos o número 0 em determinado octeto, indica que esse octeto é dedicado à identificação do host, isto é, das máquinas que podemos conectar na rede.

Analisando a máscara padrão da classe B (255.255.0.0), temos dois octetos destinados à identificação. Preenchemos esses octetos com 0 e os demais com 1, que é o equivalente em binário. Para descobrirmos quantos dispositivos podemos identificar usando o endereço da classe B, basta contarmos a quantidade de zeros na máscara de rede, ou seja, a quantidade de bits destinados à identificação.

Neste caso, temos 16 bits: 11111111.11111111.00000000.00000000.

Vamos fazer um cálculo rápido: 2 elevado a 16 menos 2. A subtração por 2 corresponde aos dois endereços reservados, o endereço de rede e o endereço de broadcast, ou limite inferior e superior do endereçamento. Obteremos 65.534 endereços IPs disponíveis usando a classe B.

Conclusão
Isso atende bem à nossa demanda. Podemos usar, por exemplo, o endereço 172.16.0.0 para identificar nossa rede. Mas será eficiente usar esse endereço para identificar 400 máquinas, tendo mais de 65 mil endereços disponíveis?

Será que não podemos refinar um pouco para termos uma quantidade de endereços IP disponíveis mais próxima da nossa demanda e uma alocação eficiente?

Na sequência, abordaremos como obter um endereço IP mais otimizado!

@@05
Distribuição eficiente de endereços IP

Estamos com uma questão: como distribuir endereços IP de forma mais eficiente, para não desperdiçar uma série de endereços e sem deixar de atender a nossa demanda?
Sabemos que precisamos de, no máximo, 400 endereços IP para cada uma das VLANs que configuramos e, na classe B, teremos mais de 65 mil endereços disponíveis.

Classe B
Endereços IP: 128-191 no primeiro octeto Máscara de rede: 255.255.0.0

172.16.10.1

Endereço de rede: 172.16.0.0

Endereço de broadcast: 172.16.255.255

Se pensarmos, por exemplo, no caso do provedor de serviços de rede, ele recebe uma quantidade limitada de endereços IP e não faz sentido desperdiçá-los, porque cada endereço representa um custo. Cada endereço é disponibilizado por uma agência reguladora de telecomunicações e deve ser utilizado, não pode ficar ocioso ou atendendo uma demanda irreal.

Dessa forma, é muito importante nos atentarmos a como fazer uma distribuição eficiente de endereços IP. Se observarmos no contexto do primeiro curso, nós estudamos algumas classes e, em cada classe, tínhamos uma máscara padrão. De acordo com a máscara padrão de rede de cada uma das classes, podíamos calcular a quantidade de endereços IP disponíveis.

Padrão Classful
Classe de endereçamento	Intervalo do primeiro octeto	Máscara de rede	Endereços disponíveis (hosts)
A	1-126	255.0.0.0	16.777.214
B	127-191	255.255.0.0	65.534
C	192-223	255.255.255.0	254
Em suma, na classe A, tínhamos mais de 16 milhões de endereços IP, na classe B mais de 65 mil e na classe C apenas 254. Esse padrão surgiu nos idos de 1990, quando a demanda por endereços IP ainda era muito pequena em comparação com hoje, onde temos um número crescente de dispositivos na rede. Esse é o padrão classful.

Entretanto, uma maneira de distribuir esses endereços IP de forma eficiente seria alterar a máscara de rede. Ao invés de simplesmente usarmos a máscara de rede padrão de cada uma das classes, podemos alterá-la segundo a nossa demanda de endereços IP. Como fazemos isso?

O primeiro passo consiste em converter a nossa demanda, conforme o número de máquinas que queremos conectar na rede, para um número binário. Vamos pegar um exemplo de 400 máquinas que queremos atender em cada uma das VLANs, e fazer essa conversão para binário.

Demanda de endereços IP: 400
Conversão para base binária: 110010000 (9 bits)

Classe B

** Endereço: 172.16.0.0**

Máscara de rede: 255.255.0.0

11111111.11111111.00000000.00000000

Para isso, podemos utilizar a calculadora do computador, por exemplo, no modo programador, e realizar a conversão da base decimal para binária, hexadecimal ou octal. Se fizermos essa conversão, obteremos um número de 9 bits, representados por uma sequência de zeros e uns.

Lembrando que os bits à esquerda podem ser desconsiderados.
Então, você provavelmente encontrará uma sequência de bits que tem alguns zeros à frente ao fazer essa conversão na calculadora do seu computador, mas deve pegar apenas a sequência iniciada pelo 1, já que o zero à esquerda será zero vezes 2 elevado a qualquer número (uma potência), e isso não representa nenhum valor quando fazemos o somatório das potências.

Fizemos a conversão da demanda de endereços IP que temos em cada uma das nossas VLANs. E, o que faremos com esse número binário? Agora, temos que alterar a máscara de rede padrão que temos na classe B.

Vamos preencher essa máscara com zeros, usando apenas o número de bits necessários para representar a nossa demanda por endereços IP. No nosso caso - 400 convertido para a base binária - só precisamos de 9 bits para representar esse número. Então, vamos começar da direita para a esquerda, preenchendo com 9 zeros, começando pelo último octeto.

Para a nossa máscara de rede, vamos precisar de 8 bits do último octeto e apenas de 1 bit do terceiro octeto. E o que faremos com os demais bits? Preencheremos todos com 1.

Classe B
Endereço: 172.16.0.0

Máscara de rede ajustada

11111111.11111111.11111110.0 0 0 0 0 0 0 0

Agora, vamos fazer a conversão dessa máscara de rede que está em binário para decimal. Nesse processo de conversão, obteremos uma nova máscara de rede, que chamamos de máscara de rede ajustada à nossa demanda.

Classe B
Endereço: 172.16.0.0

Máscara de rede ajustada

11111111.11111111.11111110.0 0 0 0 0 0 0 0

255.255.254.0

Então, uma sequência "255.255.254.0". Esse "254" pode causar estranheza, mas nada mais é do que a conversão da sequência que está no terceiro octeto.

Se fizermos a conta de quantos endereços IP nós temos disponíveis com essa nova máscara de rede, o cálculo será 2 elevado ao número de bits que possuímos nessa máscara de rede disponível para o endereçamento dos hosts (hospedeiros).

No nosso caso, nós temos 9. Então, 2 elevado a 9 menos 2, referente aos dois endereços reservados, e obtemos o número 510.

IPS disponíveis . 2^9 - 2 = 510
Nesse caso, podemos endereçar até 510 dispositivos, hosts, usando essa máscara de rede ajustada.

Disto, surge a pergunta: como definir qual será o endereço de rede e qual o endereço broadcast de cada uma dessas sub-redes criadas ao particionarmos o endereço da classe B - da máscara de rede padrão - para uma máscara de rede ajustada para as nossas VLANs?

Além disso, é importante ressaltar que existe uma forma alternativa de representar essa máscara de rede ajustada. Podemos usar o padrão conhecido como CDIR (Classless Inter-Domain Routing).

Endereço de rede: 172.16.0.0
Máscara de rede: 255.255.254.0

Classless Inter-Domain Routing (CIDR) 172.16.0.0/23

O CIDR consiste em primeiro representar o endereço IP que usaremos para a nossa rede, que é "172.16.0.0/23". Em seguida, colocamos o número de bits 1 na máscara de rede ajustada que criamos. No nosso caso, foram 23 bits 1 contra apenas 9 bits 0. Aqui temos esse padrão alternativo de representação da máscara de rede ajustada.

@@06
Para saber mais: definindo endereços IP

Os endereços IP são fundamentais para o funcionamento de qualquer rede de computadores, seja na Internet ou em redes privadas. Eles são usados para identificar e localizar dispositivos em uma rede. Na definição de um endereço IP, é necessário considerar vários fatores, como a estrutura da rede, o número de dispositivos na rede, e se o endereço é para uso privado ou público.
Os endereços IP (Internet Protocol) consistem em um conjunto único de números que identificam dispositivos em uma rede de computadores. Comumente, empregamos neste processo dois tipos de endereços de IP: o IPv4 e o IPv6.

O IPv4 é um endereço de 32 bits, normalmente exibido como quatro números inteiros que variam entre 0 e 255, e que são separados por pontos (por exemplo, 192.168.1.1). No entanto, devido à escassez de endereços IPv4, o IPv6 foi introduzido, utilizando 128 bits para descrição de um endereço de IP.

Para definir um endereço IP, você deve considerar a rede e a sub-rede em que o dispositivo se encontra. O endereço IP é dividido em duas partes: (i) o identificador de rede e (ii) o identificador de host. A quantidade de espaço reservado para cada um varia dependendo da classe do endereço (A, B ou C para IPv4) e da máscara de sub-rede usada.

Vamos considerar duas classes principais de endereços IPv4: Classe A e Classe B. Para um endereço de Classe A, o primeiro octeto é usado para identificar a rede e os três restantes para o identificar o host. Por exemplo, em um endereço 10.0.0.1, "10" é o identificador de rede e "0.0.1" é o identificador de host. Em um endereço de Classe B, os dois primeiros octetos são usados para o identificar a rede e os dois restantes para identificar o host. Por exemplo, em um endereço 172.16.0.1, "172.16" é o identificador de rede e "0.1" é o identificador de host.

Ainda, quando você precisa expressar um endereço IPv4 em um espaço de endereço IPv6, é comum realizar um processo definido como "endereço IPv4-mapeado em IPv6". Isso envolve colocar o endereço IPv4 no final do endereço IPv6.

Por exemplo, o endereço IPv4 "172.16.0.1" pode ser representado em um endereço IPv6 como "0:0:0:0:0:FFFF:AC10:0001". Os quatro zeros na frente representam a parte "padrão" do endereço IPv6, enquanto "FFFF" é usado para indicar que os próximos 32 bits são um endereço IPv4. Os últimos dois grupos de dígitos são a representação hexadecimal do endereço IPv4 (AC10:0001 é a representação hexadecimal de 172.16.0.1).

@@07
Calculando um endereço de IP

Hoje ainda se fala em classes de endereço IP. divididas em cinco principais: Classe A, Classe B, Classe C, Classe D e Classe E. Cada uma tem um intervalo específico de endereços IP disponíveis. Considere uma instituição de ensino superior com 2500 alunos, 120 professores e convidados externos.
Qual é a classe de endereço IP mais adequada para ser usada na rede da instituição?

Classe E
 
Alternativa correta
Classe C
 
Alternativa correta
Classe B
 
A Classe B, com endereços de 128.0.0.0 a 191.255.0.0, suporta até 65,534 hosts em cada rede (2^16 - 2 = 65,534). Essa quantidade pode acomodar confortavelmente o número de alunos (2500), professores (120) e ainda teria espaço para convidados externos e crescimento futuro.
Alternativa correta
Classe A
 
Alternativa correta
Classe D

@@08
Configurando as sub-redes

Definimos uma nova máscara de rede conforme a nossa demanda de endereços IP, no entanto, havia uma dúvida no ar:
Qual seria o endereço de identificação de cada uma dessas sub-redes criadas a partir do particionamento do conjunto de mais de 65 mil endereços IP em 510, um para cada sub-rede, e qual seria o seu respectivo endereço de broadcast?
É o que definiremos agora.

Primeiro, temos que fazer alguns pequenos cálculos que logo farão sentido. Vamos pegar a máscara de rede, não no formato decimal que obtivemos, mas no formato binário mesmo.

Lembram da máscara de rede que obtivemos, que era "255.255.254.0"? Pegaremos sua respectiva representação em binário e identificaremos em qual octeto ocorre a transição dos bits 1 para os bits 0.

Endereço de rede: 172.16.0.0
Máscara de rede: 255.255.254.0

Passo 1 - Representação binária da máscara de rede

11111111.11111111.11111110.0 0 0 0 0 0 0 0

Passo 2 - Verificar o octeto em que ocorre a transição de bit 1 para 0

11111111.11111111.11111110.0 0 0 0 0 0 0 0

3° octeto

Isso ocorre no terceiro octeto, sempre partindo da esquerda para a direita.

Na sequência, vamos identificar qual é a posição do último bit 1 dentro desse terceiro octeto da esquerda para a direita.

Passo 3 - Identificar a posição de ocorrência do último bit 1
11111111.11111111.11111110.0 0 0 0 0 0 0 0

Ordenamento: 128 - 64 - 32 - 16 - 8 - 4 - 2 - 1

Posição: 2

Observando a nossa máscara de rede ajustada, temos o último bit 1 na posição 2. Qual posição é essa? Quando fazemos o cálculo de que quantidade decimal está sendo representada por uma sequência de bits em binário, cada bit possui um determinado valor na soma de potência. Então, basicamente, esse valor representa a posição ocupada pelo bit 1.

Dentro dos nossos octetos, temos uma lógica que começa com 1, vai para 2, que é 1 vezes 2 elevado a 0, mais 1 vezes 2 elevado a 1, e assim sucessivamente. Assim, temos uma sequência de 1, 2, 4, 8, 16, 32, 64, até chegar no último bit 1, que será equivalente à posição 128.

Identificamos onde ocorre essa transição, qual a posição ocupada por esse último bit dentro desse octeto da transição, mas para que utilizamos isso? Justamente, para fazer a identificação do endereço da sub-rede.

IP de Rede: 172.16.0.0
IP Broadcast: 172.16.255.255

IP sub-rede 1:

IP broadcast sub-rede 1:

IP sub-rede 2:

IP broadcast sub-rede 2:

IP sub-rede 3:

IP broadcast sub-rede 3:

IP sub-rede n:

IP broadcast sub-rede n:

No caso do endereço da sub-rede dentro da classe B, escolhemos o endereço "172.16.0.0". Podemos alocar este endereço como o da sub-rede 1.

IP de Rede: 172.16.0.0
IP Broadcast: 172.16.255.255

IP sub-rede 1: 172.16.0.0

IP broadcast sub-rede 1:

IP sub-rede 2:

IP broadcast sub-rede 2:

IP sub-rede 3:

IP broadcast sub-rede 3:

IP sub-rede n:

IP broadcast sub-rede n:

Agora você deve estar se perguntando como identificar a "sub-rede 2", a "sub-rede 3", e a "sub-rede n" nessa nova máscara de rede ajustada?

Basicamente, vamos somar a posição do último bit 1, que é 2, no octeto em que ocorre a transição, que no nosso caso é o terceiro octeto.

Então, para identificar o próximo endereço de sub-rede, vamos somar 2 no terceiro octeto. Logo, o próximo endereço de sub-rede será "172.16.2.0".

IP de Rede: 172.16.0.0
IP Broadcast: 172.16.255.255

IP sub-rede 1: 172.16.0.0

IP broadcast sub-rede 1:

IP sub-rede 2: 172.16.2.0

IP broadcast sub-rede 2:

IP sub-rede 3:

IP broadcast sub-rede 3:

IP sub-rede n:

IP broadcast sub-rede n:

E o próximo endereço de sub-rede após este? Será "172.16.4.0".

IP de Rede: 172.16.0.0
IP Broadcast: 172.16.255.255

IP sub-rede 1:172.16.0.0

IP broadcast sub-rede 1:

IP sub-rede 2:172.16.2.0

IP broadcast sub-rede 2:

IP sub-rede 3: 172.16.4.0

IP broadcast sub-rede 3:

IP sub-rede n:

IP broadcast sub-rede n:

Se tivéssemos listado aqui a sub-rede 4, seria "172.16.6.0". Isso ocorre sucessivamente até chegarmos na sub-rede N, que é a última sub-rede dentro dessa máscara de rede ajustada, que é "172.16.254.0". Simples, não é?

Mas, como definimos o endereço de broadcast? No endereço de rede e no endereço de broadcast, que são endereços reservados dentro das classes, há um limite inferior e um limite superior ao conjunto de endereços IP que conseguimos usar para classificar e identificar dispositivos na rede.

O endereço de rede atua como limite inferior e o endereço de broadcast como limite superior. Se pegarmos, por exemplo, o IP de broadcast da sub-rede 1, qual seria esse endereço?

Neste conceito de limites, o endereço de broadcast será o endereço imediatamente anterior ao endereço da sub-rede 2 e o broadcast da sub-rede 2 será exatamente o endereço IP imediatamente anterior ao da sub-rede 3, e assim sucessivamente. Além disso, o endereço de broadcast da sub-rede-n será "172.16.255.255".

IP de Rede: 172.16.0.0
IP Broadcast: 172.16.255.255

IP sub-rede 1: 172.16.0.0

IP broadcast sub-rede 1:

IP sub-rede 2: 172.16.2.0

IP broadcast sub-rede 2:

IP sub-rede 3: 172.16.4.0

IP broadcast sub-rede 3:

IP sub-rede n: 172.16.254.0

IP broadcast sub-rede n:

Então, tendo, por exemplo, o endereço IP da sub-rede basta subtrair 1 para chegar ao IP de broadcast da sub-rede 1. Fazendo esta subtração - que não é uma subtração numérica convencional, sempre usamos a base binária - o resultado é o endereço "172.16.1.255". Este será o broadcast da sub-rede 1.

Se a mesma lógica for seguida, subtraindo 1 do endereço da sub-rede 3, obteremos o broadcast da sub-rede 2, que será "172.16.3.255", e assim sucessivamente. O valor "172.16.5.255" será o endereço de broadcast da sub-rede 3, e o último endereço, conforme comentado anteriormente, que é o "172.16.255.255", será o broadcast da sub-rede n, a última na nossa máscara de rede ajustada.

IP de Rede: 172.16.0.0
IP Broadcast: 172.16.255.255

IP sub-rede 1: 172.16.0.0

IP broadcast sub-rede 1: 172.16.1.255

IP sub-rede 2: 172.16.2.0

IP broadcast sub-rede 2: 172.16.3.255

IP sub-rede 3: 172.16.4.0

IP broadcast sub-rede 3: 172.16.5.255

IP sub-rede n: 172.16.254.0

IP broadcast sub-rede n: 172.16.255.255

Agora que já sabemos como calcular e obter o endereço de broadcast e o endereço de cada uma das sub-redes após ajustarmos a máscara para uma alocação mais eficiente dos endereços IP, vamos configurar este endereço de sub-rede em nosso projeto para o Instituto Inovae.

Considerando que temos duas VLANs, podemos pegar, por exemplo, o endereço da sub-rede 1 e alocar para a VLAN 10, a VLAN de pesquisa, e alocar o endereço da sub-rede 2 para a VLAN administrativa.

Cada uma delas, conforme comentado anteriormente, deveria ter no mínimo 400 endereços IP disponíveis para cada uma das VLANs, prevendo a demanda de 600 máquinas em todo o instituto.

Então, como realizamos essa configuração? Utilizamos nosso roteador no Cisco Packet Tracer, nosso ambiente de teste. Clicamos com o botão direito, vamos à aba CLI. Por padrão, ele iniciará no modo sem muitos privilégios. Passaremos o comando enable, seguido de configure terminal.

Router>enable
Router#configure terminal
Enter configuration commands, one per line. End with
CNTL/Z.
Router(config) #
COPIAR CÓDIGO
Após isso, vamos acessar o pool DHCP da VLAN 10.

Router>enable
Router#configure terminal
Enter configuration commands, one per line. End with
CNTL/Z.
Router(config) #ip dhcp pool vlan10
COPIAR CÓDIGO
Em seguida, vamos inserir o comando network 172.16.0.0, pois este é o endereço da sub-rede 1 que foi usado para a VLAN 10.

Router>enable
Router#configure terminal
Enter configuration commands, one per line. End with
CNTL/Z.
Router(config) #ip dhcp pool vlan10
Router(dhcp-config) #network 172.16.0.0
COPIAR CÓDIGO
Também temos que informar a nova máscara de rede ajustada, que tem o padrão "255.255.254.0".

Router>enable
Router#configure terminal
Enter configuration commands, one per line. End with
CNTL/Z.
Router(config) #ip dhcp pool vlan10
Router(dhcp-config) #network 172.16.0.0 255.255.254.0
COPIAR CÓDIGO
Está faltando um detalhe: precisamos configurar o comando default-router. Geralmente, utilizamos o primeiro endereço IP disponível, que é "172.16.0.1".

Router>enable
Router#configure terminal
Enter configuration commands, one per line. End with
CNTL/Z.
Router(config) #ip dhcp pool vlan10
Router(dhcp-config) #network 172.16.0.0 255.255.254.0
Router(dhcp-config) #default-router 172.16.0.1
COPIAR CÓDIGO
Após a configuração da VLAN 10, precisamos repetir os mesmos comandos para a VLAN 20. Entraremos no ip dhcp pool vlan20 e usaremos o comando network 172.16.2.0, que é o endereço da subrede 2. Adicionaremos nossa máscara de rede ajustada, "255.254.0", seguida do comando default-router. Em vez de usar 1"72.16.0", usamos "172.16.2.1".

Router>enable
Router#configure terminal
Enter configuration commands, one per line. End with
CNTL/Z.
Router(config) #ip dhcp pool vlan10
Router(dhcp-config) #network 172.16.0.0 255.255.254.0
Router(dhcp-config) #default-router 172.16.0.17
Router(dhcp-config) #exit
Router(configr) #ip dhcp pool vlan20
Router(dhcp-config) #network 172.16.2.0 255.255.254.0
Router(dhcp-config) #default-router 172.16.2.1
COPIAR CÓDIGO
Depois da configuração das VLANs, o próximo passo é configurar as subinterfaces, ou seja, fazer a atribuição de endereços para cada uma delas.

Já realizamos as atribuições utilizando os novos endereços de sub-rede para cada uma das VLANs que criamos. O que falta fazer? Precisamos atribuir esses novos endereços às nossas sub-interfaces, uma para cada uma das VLANs.

Vamos começar pela sub-interface 1. Já estamos aqui no modo de configuração, então acessaremos interface fast ethernet 0/0.1.

Router>enable
Router#configure terminal
Enter configuration commands, one per line. End with
CNTL/Z.
Router(config) #ip dhcp pool vlan10
Router(dhcp-config) #network 172.16.0.0 255.255.254.0
Router(dhcp-config) #default-router 172.16.0.17
Router(dhcp-config) #exit
Router(config) #ip dhcp pool vlan20
Router(dhcp-config) #network 172.16.2.0 255.255.254.0
Router(dhcp-config) #default-router 172.16.2.1
Router(dhcp-config) #exit
Router(config) #interface Fa 0/0.1
COPIAR CÓDIGO
Qual comando utilizamos agora? O ip address, e vamos entrar com o novo endereço dessa sub-interface, que é "172.16.0.1" e também com a máscara de rede ajustada, "255.255.254.0". Agora podemos dar um exit.

// código omitido. 

Router(config) #interface Fa 0/0.1
Router(config-subif) # ip address 172.16.0.1 255.255.254.0 
Router(dhcp-config) #exit
COPIAR CÓDIGO
Vamos repetir o mesmo processo para a sub-interface 2. Para isso, utilizamos o comando Fa 0/0.2. Também usaremos o mesmo comando, ip address, mas precisamos alterar o endereço para "172.16.2.1", não por acaso o mesmo endereço do default router (roteador padrão), como já sabemos.

// código omitido. 

Router(config) #interface Fa 0/0.1
Router(config-subif) # ip address 172.16.0.1 255.255.254.0 
Router(dhcp-config) #exit
Router(config) #interface Fa 0/0.2
Router(config-subif) # ip address 172.16.2.1 255.255.254.0
COPIAR CÓDIGO
Com tudo configurado no nosso roteador, o que precisamos fazer para encerrar e ter toda a nossa rede funcionando dentro dessa nova configuração, é realizar novas requisições de DHCP para cada um dos PCs que temos e, na sequência, o teste de conectividade para conferir se está tudo funcionando corretamente.

Agora vamos fazer essas novas requisições de DHCP, clicando em cada um dos PCs, lá no "Desktop > IP configuration", mudamos o DHCP para "static" (estático) e depois para o modo DHCP.

Perceba que esse processo de requisição obteve êxito, o PC do pesquisador pegou o endereço da VLAN da pesquisa dentro do endereço que havíamos configurado, tudo certinho. Também pegou o default gateway (gateway padrão). Está tudo certo! Vamos replicar o processo rapidamente.

Finalizamos as requisições de DHCP. Vamos pegar o último endereço que é "172.16.2.3", da coordenação do Laboratório B, e vamos fazer um teste de conectividade com o PC do pesquisador A.

Então vamos acessar o "Command Prompt" (prompt de comando), passar ping 172.16.2.3, e conferir se obteremos um ping de sucesso. O primeiro não foi, mas o segundo foi, então, ótimo, nossa rede está funcionando!

Agora, qual vai ser o nosso próximo passo? Precisaremos incluir um servidor de acesso restrito, ou seja, um servidor com algumas informações apenas para gerentes e coordenadores. Como faremos isso? É o que vamos analisar em seguida!

@@09
Configurando as sub-redes

Um FabLab dentro de uma instituição de ensino superior precisa acomodar estudantes, professores e pessoas convidadas da comunidade com acesso à rede, ou seja, é necessário configurar um conjunto de sub-redes
Qual seria a forma ideal para essa configuração?

Configurar duas sub-redes, uma para membros internos (estudantes, professores, pessoas técnicas) e outra para convidadas da comunidade.
 
Configurar duas sub-redes, uma para membros internos e outra para pessoas convidadas da comunidade fornece a segmentação necessária do tráfego de rede, ao mesmo tempo que mantém a gestão da rede manejável. Esta abordagem permite controle de acesso diferenciado e aumenta a segurança da rede, separando o tráfego interno do tráfego de convidados.
Alternativa correta
Configurar uma única sub-rede para todas as pessoas usuárias.
 
Alternativa correta
Não usar sub-redes, pois elas não ajudam na segmentação do tráfego de rede.
 
Alternativa correta
Configurar uma sub-rede separada para cada tipo de usuário.
 
Alternativa correta
Configurar uma sub-rede para cada usuário individual.

10
Faça como eu fiz: alocando endereços IP de modo eficiente

Ao usarmos um endereço IP da classe B para endereçamento de 400 máquinas alocadas em uma rede, teremos um grande volume de endereços que estarão reservados para uso. Porém, não serão efetivamente empregados na rede.
Para evitar a ineficiência dessa forma de uso conhecida como padrão Classful, podemos ajustar a máscara de rede em função da demanda específica de uma subrede de modo que tenhamos uma alocação eficiente de endereços.

O processo de alocação eficiente começa com a definição da máscara de rede. O primeiro passo consiste no cálculo da nossa demanda de endereços, ou seja, quantos dispositivos estão inseridos em nossa rede (notebooks, desktops, smartphones, smartvs, etc).

Uma vez definida nossa demanda, vamos converter esse número da base decimal - 400 endereços - para sua representação equivalente na base binária: 110010000 endereços (verifique essa conversão usando a calculadora do seu PC no modo programador!). Observe que precisamos de 9 bits para representar a nossa demanda por endereços na base binária. Com esse dado, vamos analisar a máscara de rede. Confira na sequência:

Demanda de endereços IP → 400

Conversão para base binária → 110010000 (9 bits)

Classe B

Endereço → 172.16.0.0

Máscara de rede (base decimal) → 255.255.0.0

Máscara de rede (base binária) → 1 1 1 1 1 1 1 1 . 1 1 1 1 1 1 1 1 . 0 0 0 0 0 0 0 0 . 0 0 0 0 0 0 0 0

Vamos precisar somente dos 9 últimos bits da máscara de rede para alocação dos 400 endereços IP dos dispositivos de cada vlan do Instituto Inovae. Sendo assim, inserimos 0 nos bits da máscara que serão usados na especificação dos endereços dos dispositivos conectados em cada vlan, enquanto isso, preenchemos os demais bits da máscara com 1. Confira:

Máscara de rede ajustada (base binária) → 1 1 1 1 1 1 1 1 . 1 1 1 1 1 1 1 1 . 1 1 1 1 1 1 1 0 . 0 0 0 0 0 0 0 0

Agora, podemos converter a máscara de rede ajustada para sua respectiva representação na base decimal. A conversão é simples, basta convertermos a sequência de bits inserida em cada octeto.

Máscara de rede ajustada (base decimal) → 255.255.254.0

Com 9 bits disponíveis para o endereçamento dos dispositivos, temos a disponibilidade de quantos endereços IP?

2^9 - 2 = 510 endereços disponíveis
O cálculo acima leva em consideração que temos 2 endereços reservados: um para identificação da rede e outro para a comunicação broadcast. Por isso, fizemos essa subtração de dois endereços do resultado 2^9.

Podemos representar a máscara de rede obtida utilizando a notação Classless Inter-Domain Routing (CDIR). Nessa notação, especificamos o endereço de rede que estamos usando (172.16.0.0) e, na sequência, inserimos uma barra para especificar o número de bits 1 na máscara de rede ajustada (23 bits 1 e 9 bits 0, no nosso caso). Dessa forma, obtemos a seguinte representação:

172.16.0.0/23
Para definição dos endereços de subredes e broadcast, precisamos analisar a máscara de rede ajustada na forma binária para obter dois parâmetros:

1 - Octeto em que ocorre transição de bits de 1 para 0. No nosso caso, a transição ocorre no terceiro octeto.

1 1 1 1 1 1 1 1 . 1 1 1 1 1 1 1 1 . 1 1 1 1 1 1 1 0 . 0 0 0 0 0 0 0 0
2 - Posição de ocorrência do último bit 1 na máscara. Como trabalhamos com sistemas de numeração posicionais, cada bit possui um certo valor referente à sua posição em uma sequência. Em uma sequência de 8 bits na base binária, temos os seguintes valores da direita para a esquerda: 128 - 64 - 32 - 16 - 8 - 4 - 2 - 1. Tais valores foram obtidos, respectivamente, a partir das seguintes potências: 2^7- 2^6 - 2^5 - 2^4 - 2^3 - 2^2 - 2^1 - 2^0.

No caso da máscara que estamos analisando, a posição referente ao último bit 1 é a de valor 2.

O que fazemos com tais parâmetros? Utilizamos para calcular os endereços de sub-rede e broadcast.

Começamos definindo o endereço da primeira sub-rede (sub-rede 1) e o endereço de broadcast da última sub rede (vamos chamar de sub-rede n), respectivamente: 172.16.0.0 e 172.16.255.255.

A partir daí, calculamos o endereço da próxima sub-rede (sub-rede 2, sub-rede 3 e assim sucessivamente) somando 2 (posição referente ao último bit 1 na máscara de rede ajustada) ao terceiro octeto (octeto de transição dos bits 1 a 0 na máscara de rede ajustada) do endereço da sub-rede anterior.

O endereço broadcast é determinado de forma mais simples, ele é o endereço IP imediatamente anterior ao endereço IP da próxima sub-rede, sendo assim ele é o “último” endereço IP de uma sub-rede (podemos entender como limite superior no endereçamento de uma sub-rede). Desse modo, podemos obtê-lo subtraindo uma unidade no endereço da próxima sub-rede. Só precisamos estar atentos que não se trata de uma subtração decimal, ou seja, é uma subtração binária.

Sendo assim, obtemos a seguinte sequência de endereços reservados:

IP sub-rede 1: 172.16.0.0
IP broadcast sub-rede 1: 172.16.1.255

IP sub-rede 2: 172.16.2.0
IP broadcast sub-rede 2: 172.16.3.255

IP sub-rede 3: 172.16.4.0
IP broadcast sub-rede 3:172.16.5.255

…

IP sub-rede n: 172.16.254.0
IP broadcast sub-rede n:172.16.255.255
COPIAR CÓDIGO
Agora que já definimos uma máscara de rede ajustada à nossa demanda, precisamos mudar os endereços que estamos utilizando em nossa rede. Vamos acessar o roteador e fazer esses ajustes:

Clique no roteador, acesse a aba CLI, digite enable e, na sequência, digite configure terminal;

Vamos entrar no pool dhcp da vlan de pesquisa com o comando ip dhcp vlan10 e mudar o endereço com o comando network 172.16.0.0 255.255.254.0;

Já vamos deixar o default gateway configurado com o comando default router 172.16.0.1;

Vamos repetir o processo para a vlan do administrativo usando os comandos ip dhcp vlan20, network 172.16.2.0 255.255.254.0 e default router 172.16.2.1 na mesma ordem;

Por fim, precisamos ajustar os endereços alocados nas subinterfaces. Vamos sair do pool dhcp das vlans, retornando ao modo geral de configuração para acessar cada subinterface e designar seu novo endereço IP. Dessa forma, vamos aplicar a seguinte sequência de comandos: interface Fa 0/0.1, ip address 172.16.0.1 255.255.254.0, exit, interface Fa 0/0.2, ip address 172.16.2.1 255.255.254.0.

Agora, basta clicar em cada PC, fazer novas requisições DHCP e realizar o teste de conectividade usando o comando ping no prompt de comando.

Opinião do instrutor

Tudo deverá estar funcionando como antes, mas agora temos uma maior capacidade de endereçamento de dispositivos em nossa rede que atende de modo eficiente a demanda do Instituto Inovae.

@@11
O que aprendemos?

Nessa aula, você aprendeu como:
Criar redundâncias para evitar perdas de conexão entre as diferentes partes de uma rede;
Utilizar o protocolo STP para evitar a formação de loops em redes;
Organizar um projeto de rede em subredes com a alocação de endereços IP de modo eficiente.