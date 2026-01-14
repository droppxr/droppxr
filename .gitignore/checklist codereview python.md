# 📋 Checklist de Code Review: Python

## 1. Commits e Estrutura (Princípios Atômicos)
- [ ] **Atomicidade:** O commit trata de apenas um assunto/funcionalidade?
- [ ] **Mensagem:** A mensagem do commit é clara e descreve "o quê" e "por quê"? (Ex: `feat:`, `fix:`)
- [ ] **Arquivos:** Não há arquivos desnecessários incluídos (logs, `.pyc`, `.env`, pastas de IDE)?

## 2. Padrões de Código (PEP 8 & Estilo)
- [ ] **Nomenclatura:** `snake_case` para funções/variáveis e `PascalCase` para classes?
- [ ] **Type Hints:** Os argumentos e retornos das funções possuem tipagem definida?
- [ ] **Imports:** Estão organizados no topo e sem itens não utilizados?
- [ ] **F-Strings:** Está usando f-strings para formatação de texto em vez de `%` ou `.format()`?

## 3. Qualidade e Pythonismos
- [ ] **Context Managers:** Usou `with` para manipulação de arquivos, sockets ou conexões?
- [ ] **Comprehensions:** Loops simples foram substituídos por List/Dict Comprehensions?
- [ ] **Valores Padrão Mutáveis:** Evitou o uso de `list=[]` ou `dict={}` como argumentos de função? (O correto é usar `None`).
- [ ] **DRY (Don't Repeat Yourself):** O código evita repetições desnecessárias?

## 4. Segurança e Robustez
- [ ] **Tratamento de Erros:** As exceções são específicas (ex: `ValueError`) e não um `except Exception` genérico?
- [ ] **Logs:** Usou o módulo `logging` em vez de `print()` para mensagens de sistema?
- [ ] **Segurança:** Chaves de API, senhas ou tokens estão fora do código fonte (usando `.env`)?

## 5. Testes e Documentação
- [ ] **Testes:** Foram adicionados ou atualizados testes unitários para a nova lógica?
- [ ] **Docstrings:** Funções complexas possuem explicação clara do comportamento?
- [ ] **Tamanho:** As funções e classes estão pequenas e com responsabilidade única?
