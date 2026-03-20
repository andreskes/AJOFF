# AJOFF

Base mínima de projeto Unity criada em `/workspace/AJOFF` para iniciar um protótipo jogável inspirado em CS2 com VR para Meta Quest 2.

## Estado da tarefa

O repositório já está em um modo com escrita habilitada, então a tarefa pode seguir em modo de implementação.

## Configuração recomendada para reabrir a implementação

- **Versão exata do Unity:** `2022.3.21f1` (LTS, estável e amplamente usada com Quest 2).
- **Pipeline gráfica pretendida:** **URP**.
- **XR stack:** **OpenXR + XR Interaction Toolkit**.
- **Plataforma-alvo inicial:** Meta Quest 2 (Android).

## Ordem de prioridade sugerida

1. **Singleplayer test map** — validar locomoção, escala, interação, performance e conforto em VR.
2. **Armas** — tiro, recuo, recarga, feedback tátil/visual, raycast ou projétil.
3. **Bots** — alvos simples/NPCs para loop de combate e testes de cobertura.
4. **Menu** — fluxo VR para iniciar partida, reiniciar mapa e ajustar conforto.
5. **Networking** — deixar por último para não travar a prototipagem inicial.

## Estrutura mínima criada

- `Assets/`
- `Packages/manifest.json`
- `ProjectSettings/`
