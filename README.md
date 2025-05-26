🎮 Jogo2dpi_2.0 Um jogo 2D em Java com temática espacial, desenvolvido como projeto acadêmico. O jogador controla uma nave que deve derrotar inimigos, desviar de tiros e enfrentar um chefe final. O jogo utiliza a biblioteca Swing para renderização gráfica e manipulação de eventos.

✨ Funcionalidades 👾 Inimigos com diferentes padrões de ataque (Enemy1, Enemy2, BossHugo)

🚀 Jogador controlável com movimento e disparo de projéteis

💥 Tiros especiais e colisões com efeitos visuais

🧠 Lógica de vitória e derrota com reinício do jogo

🎨 Interface gráfica simples feita com Java Swing

📦 Estrutura de Classes Jogador.java: controla o movimento e o ataque da nave principal

Descrição Completa do Projeto
1. O que o projeto faz
O projeto "NaveX" é um jogo 2D de naves desenvolvido em Java, onde o jogador controla uma nave espacial que deve derrotar inimigos e um chefe final Karlac. O jogo possui elementos clássicos de jogos arcade, como movimentação lateral, disparos de projéteis, inimigos com comportamento automático e sistema de vitória ou derrota com base no desempenho do jogador.
2. Linguagem usada
Java (Java SE)
Recursos Tecnológicos Utilizados
IDE Utilizada: Eclipse
Sistema: qualquer sistema com JDK instalado
usamos as Bibliotecas padrão Java:
java.util.List, java.util.ArrayList,javax.swing.ImageIcon, java.awt.Image, java.awt.event.*
Banco de Dados: Não usamos, mas no futuro pensamos em aplicar funcionalidades de score, de configurações.
Dependências externas: Nenhuma, porem funciona com o uso em conjunto com o eclipse.
Como Jogar
O jogador controla a nave com: ←→↑↓
Setas esquerda/direita para mover, cima baixo para subir ou descer. (Q) para atirar ou E para soltar o especial, Enter para reiniciar a partida caso você perca ou ganhe.
O objetivo é derrotar os inimigos Aliens e meteoros da paixão (Enemy1, Enemy2) e o chefe Karlac (BossHugo) evitando os tiros inimigos (TiroEnemy1, TiroBoss1, TiroBoss2).

O jogo termina com vitória ao eliminar o chefe ou com derrota caso o jogador perca toda a vida.
Estrutura do Projeto (Principais Classes Java)
Space.java: classe principal do jogo; configura o mundo, controla instâncias e lógica de início/fim.
Jogador.java: representa a nave do jogador e sua lógica de movimentação e ataque.
Enemy1.java, Enemy2.java: inimigos com movimentação automática e tiros simples.
BossHugo.java: chefe final do jogo, com ataques múltiplos e padrão de movimentação.
Tiro.java: tiro padrão do jogador.
TiroEnemy1.java, TiroBoss1.java, TiroBoss2.java: tiros dos inimigos.
Especial.java: projétil especial do jogador ativado com E.
Container.Java: arquivo que carrega a tela do jogo.
Recursos Graficos
As imagens utilizadas (nave, fundo, inimigos, tiros) estão na pasta images/, dentro do diretório src/.
As imagens são carregadas via ImageIcon.
JFrame: janela principal do jogo.
JPanel: usado como canvas onde o jogo é desenhado.
Graphics / Graphics2D: utilizados para desenhar imagens, texto, objetos e efeitos visuais.



Karlac
![image](https://github.com/user-attachments/assets/b6d16cff-8514-46ec-8303-611ec893275d)
 
![image](https://github.com/user-attachments/assets/ef50fd4d-4177-423b-9fa8-8fa34a6ce0ed)
![image](https://github.com/user-attachments/assets/aff06c7b-3b82-45b9-8e7b-639eec51de0c)

 

Nave espacial:
  
![image](https://github.com/user-attachments/assets/d6907f09-9379-4427-a121-a0282910d3b4)
  
![image](https://github.com/user-attachments/assets/580edf2e-aa70-4315-a006-4acb870620e5)
 

Abstração
Cada arquivo Java define uma classe que abstrai um elemento do jogo:
Container.Java: representa o “mundinho” onde tudo acontece (é um JPanel que desenha o fundo, o jogador, inimigos e projéteis).
Jogador: modelo da nave controlada pelo usuário (posicão, vida, controle de tiros e especiais).
Space: é o construtor da fase, adicionando tudo o que precisa existir.
Enemy1, Enemy2, BossHugo: abstrações de inimigos, cada um com sua imagem, posição, tamanho, visibilidade e lógica de tiro.

Tiro, TiroEnemy1, TiroBoss1, TiroBoss2, Especial: representam projéteis normais/enemy/boss/especial, com seus próprios atributos e comportamento de movimentação.

Abstração: você foca apenas no que é essencial para cada tipo (imagem, posição, movimento, colisão), escondendo detalhes internos. (Private);
Encapsulamento
Os campos são private : protegem o estado interno.
Os métodos get…() (e nos casos de Jogador, métodos set…() e de controle) expõem somente o que é necessário.

Encapsulamento: impede acesso direto às variáveis, forçando o uso de métodos de controle e evitando estados inconsistentes.
Ex: private static int VELOCIDADE = 4 ;
public static int getVELOCIDADE() {
		return VELOCIDADE;
	}

Herança e Interfaces.
public class Space extends JPanel implements ActionListener
Você herda toda a infraestrutura de um painel Swing para desenhar (paintComponent(Graphics g)), usar repaint(), etc.
Space implements ActionListener, KeyListener
Usa interfaces do Swing para reagir a eventos de tecla e ao Timer que gera o game loop.
Herança: reaproveita o comportamento do JPanel.

Polimorfismo (via Lógicas Semelhantes)
Embora você não tenha uma hierarquia de inimigos (por exemplo, abstract class Inimigo), há polimorfismo de fato na forma como trata eventos:
O Swing chama sempre actionPerformed(ActionEvent e) em Space, mas internamente ele itera sobre várias listas de objetos e chama, para cada um, métodos como atualizarPosicao() ou checarVisibilidade().
Cada tipo de tiro (Tiro, TiroEnemy1, TiroBoss1, Especial) tem seu próprio método de mover, mas o Space os trata de forma parecida (movimenta, desenha, remove se não visível).
Polimorfismo: “mesma chamada, comportamento diferente” — imposto pela forma como cada classe implementa seu movimento e colisão.
Melhorias
Eu posso começar fazendo melhorias simples que deixam o jogo mais atraente sem muito esforço. Por exemplo, adicionar um contador de pontos no canto da tela para eu acompanhar meu desempenho em tempo real; incluir uma barra de vida para mim e para o chefe, assim fica claro quanto falta para cada um; trocar o fundo do cenário a cada fase, mudando a cor ou a imagem para variar o visual; criar uma tela inicial que diz “Pressione Enter para começar” e uma tela de pausa acionada por um botão que interrompe o game loop e exibe “PAUSADO”; adicionar um pequeno efeito de explosão sempre que um inimigo for destruído; e implementar um breve período de invencibilidade da minha nave (com um piscar rápido) logo após eu levar um tiro. Essas atualizações são fáceis de codar e já melhoram bastante a experiência de jogo.

Nenhuma biblioteca externa necessária (apenas Java padrão) porem tem que ser executado pelo eclipse
![image](https://github.com/user-attachments/assets/501a50ff-3c87-4098-876c-ae2a2b76a101)
