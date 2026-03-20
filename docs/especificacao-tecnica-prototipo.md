# Especificação Técnica Curta — Protótipo VR

## 1. Escopo do protótipo
Protótipo VR single-player focado em combate em arena curta, validando conforto, gunplay, IA básica e performance no Meta Quest 2. O objetivo é provar o loop principal: movimentação, combate, objetivo simples e reinício rápido.

## 2. Player VR
- **Locomotion:** smooth locomotion no analógico esquerdo com velocidade alvo de 1.8 a 2.2 m/s.
- **Altura:** suporte a modo `standing` e `seated`, com calibração inicial da altura do jogador e offset manual opcional.
- **Agarrar:** grip contextual para pegar armas, magazines e objetos interativos em alcance curto.
- **Recoil:** recoil físico leve na mão dominante, com deslocamento visual curto para não quebrar conforto.
- **Comfort settings:** snap turn por padrão, smooth turn opcional, vignette opcional durante movimento e ajuste de sensibilidade.

## 3. Input — Meta Quest 2
- **Thumbstick esquerdo:** locomoção.
- **Thumbstick direito:** snap turn ou smooth turn.
- **Trigger:** disparo / uso principal.
- **Grip:** agarrar ou segurar arma com uma ou duas mãos.
- **A / X:** interação secundária, confirmar UI ou soltar magazine da arma se aplicável.
- **B / Y:** recarregar ou ação contextual secundária.
- **Menu:** pause / restart.

## 4. Weapons
- **Hitscan vs projectile:**
  - pistola e rifle usam hitscan para resposta imediata;
  - granada ou tiro especial opcional usa projectile simples com gravidade.
- **Recarga:** manual simplificada; botão de reload no protótipo, com opção futura de recarga física completa.
- **Recoil:** cada arma tem curva curta de kick vertical e pequena variação horizontal.
- **Spread:** spread baixo em repouso, aumenta em tiro contínuo e movimento.
- **Ammo reserve:** munição por carregador + reserva total por arma.

## 5. Combat
- **HP:** jogador e inimigos usam HP direto; referência inicial de 100 HP para o jogador e 50 a 100 HP para inimigos comuns.
- **Headshots:** multiplicador de dano de 2x em colisão na hitbox da cabeça.
- **Armor opcional:** camada opcional de armor absorve dano antes do HP, sem regeneração automática no protótipo.

## 6. AI
- **Patrulha:** inimigos seguem waypoints simples em loop quando fora de combate.
- **Perseguição:** ao detectar o jogador por visão ou dano recebido, avançam para a última posição conhecida.
- **Cobertura simples:** se existir ponto de cover próximo, a IA tenta ocupar esse ponto por alguns segundos antes de reposicionar.
- **Ataque:** IA alterna entre disparo curto e reposicionamento, evitando comportamento estático contínuo.

## 7. Match flow
- **Spawn:** jogador inicia em área segura com arma inicial equipada.
- **Objetivo:** eliminar todos os inimigos da arena ou completar uma meta curta de sobrevivência / ativação.
- **Vitória:** quando objetivo é concluído, mostrar tela simples com tempo, dano recebido e opção de restart.
- **Derrota:** ao chegar em 0 HP, mostrar tela de fail e restart rápido.
- **Restart:** reinício completo da arena em até poucos segundos, resetando player, IA, munição e objetivo.

## 8. UX VR
- **Snap turn:** padrão em incrementos de 30° ou 45°.
- **Vignette opcional:** ativa apenas em locomoção e smooth turn, com intensidade ajustável.
- **Seated / standing:** seleção disponível no início ou menu de pausa, reaplicando offset de altura.
- **UI:** HUD mínimo no mundo ou preso ao pulso, evitando overlays fixos excessivos.

## 9. Performance — Meta Quest 2
- **Target FPS:** 72 FPS estáveis como meta mínima do protótipo.
- **Limite de draw calls:** alvo de até ~100 draw calls visíveis por frame em combate, priorizando batching e meshes combinadas.
- **Baked lighting:** iluminação principal baked; evitar luzes dinâmicas caras e sombras em tempo real fora do estritamente necessário.
- **LODs:** objetos médios e grandes com ao menos 2 a 3 níveis de LOD.
- **Occlusion:** usar occlusion culling em arenas fechadas / semi-fechadas para reduzir custo de render.
- **Outros cuidados:** materiais simples, poucos transparents, física limitada e inimigos simultâneos controlados.

## 10. Critérios mínimos de aceite
- Jogador consegue se mover, virar, atirar, recarregar e reiniciar sem sair da experiência.
- Pelo menos uma arma hitscan funcional e uma IA capaz de patrulhar, perseguir e atirar.
- Loop completo de vitória e derrota implementado.
- Build jogável no Meta Quest 2 mantendo conforto básico e performance alvo na arena do protótipo.
