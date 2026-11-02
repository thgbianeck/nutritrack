---
name: nutrition-calc
description: Regras de cálculo de IMC, TMB, TDEE, metas diárias de calorias e macronutrientes, água, projeção de meta e classificação de limites do NutriTrack. Use ao implementar ou testar qualquer cálculo nutricional ou de peso.
---
# Cálculos nutricionais

Fonte única da verdade: `docs/03-dominio-e-calculos.md`. Leia-o integralmente antes de implementar.

Checklist:
- Implementar apenas em serviços de domínio puros (sem Spring).
- Cada fórmula com teste unitário parametrizado, incluindo limites: piso calórico, perda máxima semanal, ganho, manutenção, meta irrealista, arredondamentos.
- Metas tipo teto (calorias, carboidratos, gorduras, saturadas, açúcares, sódio) geram WARNING a 80% e EXCEEDED acima de 100%. Metas mínimas (fibras, água, proteínas) nunca geram EXCEEDED.
- Não altere uma fórmula sem atualizar o documento e os testes.