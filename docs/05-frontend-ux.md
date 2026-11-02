# Frontend e UX

## Identidade
Nome NutriTrack, paleta verde-esmeralda com acentos em laranja para alertas. Tema claro e escuro (preferência do sistema + alternância manual persistida). Tipografia limpa, cantos arredondados, sombras suaves, microanimações discretas.

## Navegação
- Barra lateral recolhível no desktop; barra inferior com ações principais no mobile.
- Itens: Início, Peso, Refeições, Perfil e metas, Notificações (com contador), Administração (ADMIN), Pacientes (NUTRITIONIST/ADMIN).
- Itens aparecem conforme permissões.

## Telas
1. Login: limpo, com mostrar/ocultar senha e erro claro.
2. Troca de senha obrigatória: indicador de força da senha e checklist de requisitos.
3. Onboarding do MEMBER (assistente em passos): dados pessoais, medidas, nível de atividade, meta e data; mostrar prévia das metas calculadas e aviso se a meta for irrealista com sugestão de data.
4. Início (dashboard):
   - Cartões no topo: Peso perdido (destaque grande, com ícone e animação de contagem), Peso atual, IMC (com selo colorido da classificação), Meta (barra de progresso e dias restantes), Sequência de dias.
   - Gráfico de evolução de peso e IMC (Chart.js): linha do peso real, média móvel tracejada, linha horizontal da meta, linha de projeção, alternância de período (7d, 30d, 90d, tudo), comparação com o período anterior (sobreposição translúcida), tooltip com IMC e variação em relação ao registro anterior.
   - Consumo do dia: anéis de progresso ou barras para calorias, carboidratos, proteínas, gorduras, açúcares, sódio, fibras, água; cores verde, amarelo e vermelho conforme status; texto "restam X" ou "excedeu X". Reinicia automaticamente a cada dia (o frontend reconsulta ao virar o dia e ao voltar o foco da aba).
   - Atalhos rápidos: registrar peso de hoje, adicionar refeição, +200 ml e +500 ml de água.
   - Alertas ativos em destaque e últimas conquistas.
5. Peso: formulário rápido (data padrão hoje), histórico em tabela editável, gráfico completo, exportar CSV.
6. Refeições: seletor de dia (anterior, próximo, calendário), lista agrupada por tipo, totais do dia, adicionar com busca de alimentos (autocomplete), porção ajustável, entrada manual, copiar de ontem, favoritas e recentes.
7. Perfil e metas: edição do perfil e visualização das metas diárias com explicação de como foram calculadas.
8. Notificações: lista, marcar como lida, marcar todas.
9. Administração: tabela de usuários (busca, filtro por papel, ativo/inativo), diálogo de criação com seletor de tipo de usuário que **mostra, ao selecionar, a lista do que o papel pode acessar** (a partir de GET /roles), ações de editar, desativar e redefinir senha.
10. Pacientes: lista dos vinculados e visão somente leitura do dashboard.

## Feedback
- Snackbar para sucesso e erro; diálogo de alerta ou toast destacado quando um limite for excedido ao salvar refeição ou água (usar `dailyStatus` da resposta).
- Skeletons, estados vazios ilustrados, confirmação antes de excluir.
- Formulários com validação inline em pt-BR.

## Qualidade
Responsivo (360px a 1920px), acessível (AA), rotas lazy, bundle enxuto, sem dependências de UI além de Angular Material, Chart.js (ng2-charts) e, opcionalmente, um pequeno plugin de anotação para linhas de referência.
