# 📋 Checklist de Code Review: Python

## 1. Lógica e Funcionalidade
- [ ] **Propósito:** O código resolve o problema proposto sem efeitos colaterais óbvios?
- [ ] **DRY (Don't Repeat Yourself):** A lógica evita repetições? Se um bloco de código aparece 3x, ele deve virar uma função ou classe reutilizável.
- [ ] **Responsabilidade:** As funções e classes fazem apenas uma coisa ou estão grandes demais?

## 2. Padrões e Estilo (PEP 8)
- [ ] **PEP 8:** O código segue as normas de estilo (espaçamentos, nomes `snake_case`, limites de linha e organização de imports)?
- [ ] **Legibilidade:** O código é fácil de entender para quem não o escreveu?
- [ ] **Type Hints:** Os argumentos e retornos estão tipados para facilitar a manutenção?

## 3. Robustez e Segurança
- [ ] **Tratamento de Erros:** As exceções tratadas são específicas (ex: `KeyError`) em vez de um `except Exception` genérico?
- [ ] **Dados Sensíveis:** Chaves de API, tokens e senhas estão protegidos (ex: em arquivos `.env`)?
- [ ] **Recursos:** Arquivos e conexões são abertos via Context Managers (`with`)?

## 4. Testes e Validação
- [ ] **Testes:** Foram criados ou atualizados testes que cobrem essa nova lógica?
- [ ] **Logs/Prints:** Prints de debug foram removidos e substituídos por `logging` quando necessário?

## 5. Estrutura do PR
- [ ] **Atomicidade:** O PR foca em apenas um assunto ou está misturando muitas alterações?
- [ ] **Limpeza:** Foram removidos arquivos temporários, pastas de IDE ou códigos comentados?

---

EXEMPLO DE COMENTARIO
> _Poderia quebrar as alterações em commits atômicos? Commitar cada funcionalidade separadamente facilita o code review e permite reverter mudanças específicas com mais segurança caso algo quebre na main._
