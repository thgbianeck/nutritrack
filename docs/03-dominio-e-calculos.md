# Domínio e cálculos

## IMC
IMC = peso(kg) / (altura(m))². Arredondar a 1 casa decimal.
Classificação (cor): menor que 18,5 Abaixo do peso (azul); 18,5 a 24,9 Peso normal (verde); 25,0 a 29,9 Sobrepeso (amarelo); 30,0 a 34,9 Obesidade grau I (laranja); 35,0 a 39,9 Obesidade grau II (vermelho); 40,0 ou mais Obesidade grau III (vermelho escuro).

## Idade
Calculada a partir da data de nascimento na data de referência. Idade mínima 14, máxima 100.

## Taxa metabólica basal (Mifflin-St Jeor)
Homem: 10 x peso + 6,25 x altura(cm) - 5 x idade + 5
Mulher: 10 x peso + 6,25 x altura(cm) - 5 x idade - 161

## Gasto energético total (TDEE) = TMB x fator de atividade
SEDENTARY 1,2; LIGHT 1,375; MODERATE 1,55; HIGH 1,725; ATHLETE 1,9.

## Meta calórica diária
1. diferenca_kg = peso_atual - peso_meta (positivo = perder; negativo = ganhar).
2. dias = dias entre hoje e a data-meta (mínimo 1).
3. ajuste_diario = diferenca_kg x 7700 / dias (kcal por dia).
4. Limite de segurança do ajuste: perda no máximo 1000 kcal/dia e no máximo 1% do peso por semana; ganho no máximo 500 kcal/dia.
5. calorias_meta = TDEE - ajuste_diario (perda) ou TDEE + |ajuste| (ganho), respeitando o piso: mulher 1200 kcal, homem 1500 kcal.
6. Se o limite de segurança ou o piso interferiu, marcar `goalRealistic=false` e devolver `suggestedGoalDate` (data mais próxima que respeita o limite).
7. Se peso atual = peso meta, calorias_meta = TDEE (manutenção).

## Macronutrientes e demais metas (base: calorias_meta)
- Proteínas (g): 1,6 x peso_meta(kg), mínimo 10% e máximo 35% das calorias; 4 kcal/g.
- Gorduras totais (g): 27% das calorias / 9.
- Gorduras saturadas (g): máximo de 10% das calorias / 9.
- Carboidratos (g): calorias restantes após proteínas e gorduras / 4 (mínimo de 100 g).
- Açúcares (g) (limite): máximo de 10% das calorias / 4. Tratar como teto.
- Fibras (g): 14 x (calorias / 1000), mínimo de 25 g (meta mínima a atingir, não teto).
- Sódio (mg): teto de 2300.
- Água (ml): 35 x peso_atual(kg), arredondado para múltiplos de 50.
Arredondar gramas a inteiros e calorias a múltiplos de 10.

## Classificação do consumo por nutriente
Tetos (calorias, carboidratos, gorduras, gorduras saturadas, açúcares, sódio): percentual = consumido / meta.
- menor que 80%: OK
- 80% a 100%: WARNING
- maior que 100%: EXCEEDED
Metas mínimas (fibras, água, proteínas): nunca geram EXCEEDED; apenas indicam progresso. Proteínas só geram aviso se passarem de 200% (EXCEEDED_PROTEIN_HIGH não necessário, tratar como WARNING).

## Regras de peso
- Peso inicial = primeiro registro do usuário.
- Peso perdido = inicial - atual (pode ser negativo em caso de ganho).
- Média móvel de 7 dias para o gráfico.
- Ritmo atual (kg/semana) = regressão linear simples dos últimos 28 dias (mínimo 3 registros). Projeção da data da meta = hoje + (peso atual - peso meta) / ritmo, se o ritmo apontar na direção da meta; senão, "sem projeção".
- Sequência (streak) = dias consecutivos, até hoje ou ontem, com ao menos um registro de peso OU refeição.

## Refeição
Totais = soma dos itens. Item de catálogo: nutrientes = valor por porção x (quantidade / porção base). Valores nunca negativos.

## Conquistas
FIRST_WEIGHT, FIRST_MEAL, STREAK_7, STREAK_30, FIRST_KG_LOST, HALFWAY_TO_GOAL, GOAL_REACHED, WATER_GOAL_7_DAYS.

## Invariantes
Data de meta no futuro; peso-meta entre 20 e 400; altura entre 100 e 250 cm; um registro de peso por dia por usuário; ADMIN último ativo não removível.
