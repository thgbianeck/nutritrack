# Visão e escopo

NutriTrack ajuda pessoas a atingir uma meta de peso: registram peso diário e refeições, e o sistema calcula IMC, metas diárias de nutrientes e avisa quando um limite é excedido.

## Perfis de usuário
- ADMIN: gerencia usuários e vê a matriz de permissões; também usa o app normalmente.
- NUTRITIONIST: acompanha, somente leitura, os usuários MEMBER vinculados a ele.
- MEMBER: gerencia apenas os próprios dados.

## Funcionalidades principais
1. Autenticação com administrador inicial pré-cadastrado e troca de senha obrigatória no primeiro acesso.
2. Gestão de usuários (ADMIN): criar, editar, ativar/desativar, redefinir senha, escolher o tipo (papel) vendo o que cada papel pode acessar.
3. Perfil do usuário: nome, sexo, data de nascimento (idade calculada), altura, peso atual, nível de atividade, meta de peso, data da meta.
4. Registro diário de peso com gráfico de evolução (peso e IMC), linha de meta, média móvel e comparação com períodos anteriores.
5. IMC com classificação por cor.
6. Registro de refeições com calorias, carboidratos, proteínas, gorduras (totais e saturadas), açúcares, fibras e sódio.
7. Registro de água.
8. Metas diárias calculadas automaticamente (calorias, carboidratos, proteínas, gorduras, açúcares, fibras, sódio, água).
9. Alertas quando algum item atingir 80% (atenção) ou exceder 100% (limite excedido) da meta diária.
10. Página inicial (dashboard): peso perdido até agora, gráfico de evolução, consumo do dia versus metas (reinicia a cada dia), alertas, sequência de dias registrando.

## Extras úteis (incluídos no escopo)
- Catálogo de alimentos pré-carregado (cerca de 60 alimentos comuns no Brasil com valores por porção) e alimentos personalizados do usuário.
- Copiar refeições de ontem; refeições favoritas/recentes para registro rápido.
- Projeção de data para atingir a meta no ritmo atual e aviso se a meta for irrealista (perda superior a 1% do peso corporal por semana).
- Relatório semanal (médias, melhor dia, dias dentro da meta) e exportação CSV do histórico de peso.
- Central de notificações com contador.
- Conquistas simples (primeiro registro, 7 dias seguidos, primeiro quilo perdido, etc.).
- Modo claro/escuro, layout responsivo, onboarding guiado no primeiro acesso do MEMBER.

## Fora de escopo
Integrações externas (wearables, OCR de rótulos), pagamentos, multi-idioma (somente pt-BR), app mobile nativo.
