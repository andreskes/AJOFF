# Escopo MVP — Jogo VR (Meta Quest 2 Standalone)

## Objetivo da primeira versão
Entregar uma build jogável e verificável em **Meta Quest 2 standalone** que permita validar o loop principal de combate em VR dentro de **uma única ronda** e **um mapa de teste**, sem tentar cobrir todas as funcionalidades futuras do projeto.

## Princípios do MVP
- Priorizar um **slice vertical jogável** em vez de amplitude de features.
- Definir critérios de aceitação **mensuráveis e testáveis**.
- Validar primeiro o loop: **movimentação -> combate -> receber dano -> morrer/vencer/perder ronda**.
- Deixar fora do MVP sistemas avançados como progressão, multiplayer, múltiplos mapas, múltiplas armas, meta-game, inventory complexo, IA sofisticada e otimizações não críticas.

## Escopo incluído
A primeira versão deve incluir apenas os itens abaixo:
1. Movimento VR: andar, correr e virar.
2. Arma principal com disparo, recarga e munição.
3. Dano, vida e morte.
4. Inimigos dummy ou bots simples.
5. Ronda única num mapa de teste.
6. HUD VR mínima.
7. Suporte Meta Quest 2 standalone.

## Itens explicitamente fora do escopo
- Multiplayer.
- Matchmaking ou backend online.
- Mais de um mapa jogável.
- Mais de uma ronda por partida.
- Sistema de progressão, níveis, perks ou economia.
- Arsenal secundário, granadas ou melee avançado.
- IA avançada com navegação complexa, cobertura, flanqueamento ou coordenação de esquadrão.
- Customização de avatar, settings extensos ou acessibilidade avançada.
- Port para outras plataformas como objetivo de release inicial.

---

## 1) Movimento VR

### Descrição
O jogador deve conseguir se deslocar de forma confiável no ambiente em VR usando controles padrão do Meta Quest 2.

### Incluído
- Andar em velocidade padrão.
- Correr com input dedicado ou ação equivalente claramente documentada.
- Virar usando snap turn ou smooth turn.

### Critérios de aceitação
- O jogador consegue se mover para frente, trás e lateralmente por **pelo menos 30 segundos contínuos** sem perder controle do avatar.
- A velocidade de andar e correr é distinta, com corrida sendo **visivelmente mais rápida** e configurada com multiplicador mínimo de **1,5x** sobre a caminhada.
- O sistema de virar responde de forma consistente em **100% das tentativas durante um teste manual de 20 ativações consecutivas**.
- Se usar snap turn, cada giro deve ocorrer em incrementos fixos documentados, por exemplo **30° ou 45° por ativação**.
- Se usar smooth turn, deve existir uma velocidade configurável/documentada em graus por segundo no documento técnico do projeto ou no inspector da cena principal.
- O jogador deve conseguir atravessar o mapa de teste de um ponto inicial até um ponto final marcado em **menos de 20 segundos correndo**.

### Evidência esperada
- Teste manual no headset.
- Vídeo curto ou checklist interno confirmando locomoção, corrida e giro.

---

## 2) Arma principal com disparo, recarga e munição

### Descrição
O MVP deve ter uma arma principal utilizável do início ao fim da ronda.

### Incluído
- Uma única arma principal funcional.
- Disparo com feedback mínimo visual, sonoro ou ambos.
- Munição no pente.
- Reserva de munição.
- Recarga manual simplificada ou por botão, desde que consistente.

### Critérios de aceitação
- O jogador inicia a ronda com **1 arma principal equipada**.
- A arma dispara ao acionar o input correto em **100% das 20 tentativas consecutivas**, exceto quando o pente estiver vazio.
- Cada disparo consome **1 unidade de munição** do pente.
- O pente deve ter capacidade fixa documentada, por exemplo **30 tiros**, e não pode exceder esse valor após recarga.
- Quando o pente chega a **0**, a arma não dispara até que uma recarga válida seja concluída.
- A recarga deve completar em no máximo **3 segundos** após ser iniciada, salvo se a intenção for deliberadamente maior e isso estiver documentado.
- A HUD deve mostrar, no mínimo, **munição no pente** e **munição de reserva** em tempo real.
- Após eliminar todos os inimigos da ronda, deve ser possível terminar a partida usando apenas essa arma principal.

### Evidência esperada
- Teste manual com contagem de tiros até esvaziar o pente.
- Confirmação visual de atualização de munição e recarga.

---

## 3) Dano, vida e morte

### Descrição
O MVP deve suportar o ciclo completo de causar dano, receber dano e encerrar a ronda por morte do jogador ou dos inimigos.

### Incluído
- Vida do jogador.
- Dano aplicado por arma do jogador.
- Dano recebido de inimigos ou fonte controlada do mapa.
- Estado de morte do jogador.

### Critérios de aceitação
- O jogador começa a ronda com **100 pontos de vida** ou outro valor fixo claramente documentado.
- Cada inimigo deve receber dano do disparo da arma principal e eventualmente morrer.
- O jogador deve receber dano de forma observável ao entrar no alcance/ataque do inimigo ou trigger de teste.
- A HUD deve refletir a vida restante em tempo real, ou no máximo com atraso visual menor que **0,5 segundo**.
- Ao chegar a **0 de vida**, o jogador entra em estado de morte e não consegue continuar atirando ou se movendo normalmente.
- A morte do jogador deve levar a um estado de fim de ronda, reinício ou tela de derrota em **até 5 segundos**.
- Pelo menos **1 teste completo de vitória** e **1 teste completo de derrota** devem ser executáveis na mesma build.

### Evidência esperada
- Teste manual documentando perda de vida, morte e transição de estado.

---

## 4) Inimigos dummy ou bots simples

### Descrição
O jogo deve incluir alvos que permitam validar combate sem depender de IA complexa.

### Incluído
- Dummies estáticos, inimigos que avançam em linha reta, ou bots com comportamento simples.
- Hit reaction básica opcional.
- Morte/inativação ao receber dano suficiente.

### Critérios de aceitação
- A ronda deve conter **pelo menos 3 inimigos**.
- Cada inimigo deve poder ser eliminado individualmente.
- Se forem dummies estáticos, eles devem permanecer visíveis e acessíveis sem bloquear a conclusão da ronda.
- Se forem bots simples, cada bot deve executar **ao menos 1 comportamento previsível**: patrulhar, perseguir, aproximar-se ou atacar.
- O tempo para eliminar todos os inimigos numa execução bem-sucedida deve ser de **até 5 minutos**.
- Não pode existir inimigo invulnerável ou preso fora da área jogável em uma execução padrão da ronda.

### Evidência esperada
- Teste manual eliminando todos os inimigos em uma partida completa.

---

## 5) Ronda única num mapa de teste

### Descrição
O MVP deve ser estruturado como uma única experiência curta e repetível.

### Incluído
- Um mapa de teste funcional.
- Um ponto de spawn do jogador.
- Um fluxo claro de início, combate e fim.
- Condição de vitória e de derrota.

### Critérios de aceitação
- A build inicia diretamente no mapa de teste ou chega nele em **no máximo 2 interações** a partir do menu inicial.
- A ronda possui **1 condição de vitória** claramente definida: eliminar todos os inimigos, sobreviver por tempo X ou equivalente documentado.
- A ronda possui **1 condição de derrota** claramente definida: vida do jogador chegar a 0.
- Após vitória ou derrota, deve existir opção de **reiniciar a ronda em até 10 segundos**.
- Uma execução completa da ronda deve durar idealmente entre **2 e 10 minutos** para um testador novo.
- O mapa deve conter geometria suficiente para validar cobertura, deslocamento e linha de visão básica.

### Evidência esperada
- Execução completa do loop início -> combate -> fim -> reinício.

---

## 6) HUD VR mínima

### Descrição
A interface deve expor apenas o necessário para o jogador entender o estado da partida.

### Incluído
- Vida.
- Munição atual.
- Munição reserva.
- Estado básico de ronda, se necessário.

### Critérios de aceitação
- A HUD deve permanecer legível em headset durante toda a ronda.
- Os elementos mínimos exibidos são: **vida**, **munição no pente** e **munição reserva**.
- As informações da HUD devem atualizar em tempo real após disparo, recarga e recebimento de dano.
- A HUD não pode obstruir permanentemente o centro da visão do jogador.
- O testador deve conseguir identificar o estado de vida e munição em **menos de 3 segundos** ao olhar para a interface.

### Evidência esperada
- Teste manual em Meta Quest 2 com verificação de legibilidade.

---

## 7) Suporte Meta Quest 2 standalone

### Descrição
A primeira versão deve rodar no dispositivo-alvo principal sem depender de PC VR.

### Incluído
- Build executável no Meta Quest 2 standalone.
- Mapeamento de controles funcional no hardware-alvo.
- Performance suficiente para teste interno do loop principal.

### Critérios de aceitação
- O projeto deve gerar uma build instalável e executável no **Meta Quest 2 standalone**.
- Toda funcionalidade do escopo incluído deve poder ser testada **sem cabo Link e sem depender de PC renderizando o jogo**.
- Os inputs necessários para jogar a ronda completa devem funcionar no headset-alvo.
- A build deve completar **3 execuções consecutivas da ronda** sem crash bloqueante.
- Durante teste interno, a experiência deve ser considerada jogável, sem travamentos críticos que impeçam locomoção, combate ou conclusão da ronda.
- Quaisquer limitações conhecidas de performance, conforto ou tracking devem ser registradas em uma seção de riscos antes da validação externa.

### Evidência esperada
- Instalação e execução em hardware real.
- Checklist interno de smoke test no dispositivo.

---

## Definição de pronto do MVP
O MVP será considerado pronto quando todos os itens abaixo forem verdadeiros:
- Todos os **7 itens de escopo incluído** estiverem implementados.
- Todos os critérios de aceitação deste documento tiverem sido validados por teste manual interno.
- A build rodar no **Meta Quest 2 standalone**.
- Um testador conseguir completar ao menos **1 ronda com vitória** e reproduzir ao menos **1 cenário de derrota**.
- Não existirem bugs críticos de severidade alta que impeçam iniciar, jogar ou reiniciar a ronda.

## Checklist de validação sugerido
- [ ] Entrar na build no Meta Quest 2 standalone.
- [ ] Andar, correr e virar funcionam no headset.
- [ ] Arma principal dispara, gasta munição e recarrega.
- [ ] HUD mostra vida, pente e reserva.
- [ ] Jogador recebe dano.
- [ ] Jogador pode morrer e a ronda termina corretamente.
- [ ] Todos os inimigos podem ser eliminados.
- [ ] Vitória e derrota podem ser reproduzidas.
- [ ] Ronda reinicia sem bloquear a próxima execução.
- [ ] Três execuções consecutivas ocorrem sem crash bloqueante.

## Riscos e observações
- VR exige iteração de conforto; portanto, snap turn pode ser preferível ao smooth turn na primeira versão.
- Se houver limitação de tempo, priorizar **dummies estáticos** antes de bots móveis, desde que o loop completo permaneça validável.
- A qualidade visual deve ser subordinada à estabilidade e clareza do loop principal.
- Quaisquer features extras devem entrar apenas após o aceite formal deste MVP.
