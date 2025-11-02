# User Stories – Desafio Beedoo – Módulo Cursos

## US-01 – Cadastrar curso
**Como** coordenador de treinamentos  
**Quero** cadastrar um novo curso com nome, descrição, período, instrutor, tipo, vagas e imagem  
**Para** disponibilizá-lo para os alunos no catálogo  

**Critérios de Aceite**
- Todos os campos obrigatórios com validação e mensagens por campo  
- Datas: fim > início e início >= hoje  
- Limites: nome ≤ 100, descrição ≤ 255, instrutor ≤ 80  
- URL da imagem deve ser http(s) válido  
- Exibir confirmação de sucesso e redirecionar para “Listar Cursos”  
- Prevenir duplo envio (botão desabilitado durante submit)  

**Definition of Done (DoD)**
- Validações front + back implementadas  
- Testes manuais e planilha atualizados  
- Sem erros no console  
- Acessibilidade básica: foco visível, alt em imagens, contraste ok  

---

## US-02 – Listar cursos
**Como** aluno interessado  
**Quero** visualizar os cursos disponíveis em cartões com informações resumidas  
**Para** decidir em quais cursos me inscrever  

**Critérios de Aceite**
- Exibir nome, período, tipo e ações  
- Truncar textos longos (ellipsis) sem quebrar layout  
- Estado vazio: mensagem “Nenhum curso cadastrado”  
- Tratamento de erro de rede/API com mensagem amigável  
- Navegação por teclado com foco visível  

**DoD**
- Sem overflow visual em viewport desktop/mobile  
- Axe sem falhas críticas  
- Logs de erro tratados na UI  

---

## US-03 – Excluir curso
**Como** administrador  
**Quero** excluir um curso da listagem com confirmação  
**Para** manter o catálogo atualizado  

**Critérios de Aceite**
- Ação de excluir com confirmação (“Deseja remover?”)  
- Ao confirmar, remover card da lista e exibir toast “Excluído com sucesso”  
- Tratar falhas (ex.: 404/500) com mensagem “Não foi possível excluir”  
- Acessível via teclado e com `aria-label` descritivo  

**DoD**
- Requisição HTTP validada (rota existente)  
- Sem erros no console após exclusão  
- Caso de teste automatizado/manual cobrindo sucesso e falhas  

---

## US-04 – Validação de Formulário
**Como** usuário do sistema  
**Quero** ser notificado quando eu tentar cadastrar um curso com dados inválidos ou em branco  
**Para** evitar erros e garantir que as informações salvas estejam corretas  

**Critérios de Aceite**
- Campos obrigatórios devem exibir mensagens de erro individuais  
- Bloquear envio se algum campo estiver vazio  
- Validar formato de data e URL antes do envio  
- Mostrar mensagens de erro próximas ao campo incorreto  
- Impedir cadastro com data de início anterior à atual  
- Limitar caracteres de texto em todos os campos  
- Garantir feedback visual e textual em todos os erros  

**DoD**
- Validações em front e back testadas manualmente  
- Mensagens de erro claras e específicas por campo  
- Todos os casos de exceção incluídos na planilha de testes  
- Prints e logs de erros documentados nas evidências  

---

## US-05 – Acessibilidade e Feedback Visual
**Como** usuário com diferentes necessidades  
**Quero** que o sistema seja acessível e apresente feedback visual e textual nas ações  
**Para** compreender claramente o que acontece em cada interação  

**Critérios de Aceite**
- Todos os botões e imagens devem possuir `aria-label` e `alt` descritivo  
- Cores e contrastes devem seguir WCAG 2.1 (razão ≥ 4.5:1)  
- Permitir zoom e navegação apenas com teclado  
- Exibir feedback visual e sonoro ao cadastrar ou excluir cursos  
- Nenhum alerta deve depender apenas de cor  
- Garantir pontuação mínima de 80 em Lighthouse (Acessibilidade)  

**DoD**
- Testes de acessibilidade realizados com Axe DevTools e Lighthouse  
- Falhas críticas de contraste e navegação corrigidas  
- Logs de console sem erros de ARIA  
- Resultados documentados na aba “A11y_Performance” da planilha  

---

 **Resumo de Cobertura**
| Tipo de Caso | Cobertura | Relacionado à US |
|---------------|------------|------------------|
| Cadastro e validação de campos | 7 casos | US-01 e US-04 |
| Listagem e estado vazio | 4 casos | US-02 |
| Exclusão e erros de API | 3 casos | US-03 |
| Acessibilidade e performance | 4 casos | US-05 |
| Vulnerabilidades e exceções | 2 casos | US-04 e US-05 |
| **Total de Casos** | **20** | **5 User Stories** |

---

 **Metodologia**
- Técnicas utilizadas: Partição de Equivalência, Valor Limite, Teste Exploratórios e Heurísticas VADER  
- Foco em qualidade visual, acessibilidade e usabilidade  
- Evidências documentadas com prints e logs nos diretórios correspondentes  