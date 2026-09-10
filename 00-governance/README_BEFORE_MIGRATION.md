# Executar App Blueprint

Blueprint canônico de produto, engenharia, dados e arquitetura agentic para o aplicativo EXECUTAR.

Este repositório funciona como **Documentation Control Plane**: requisitos, decisões, contratos, segurança, testes, evals e operação são versionados e rastreáveis antes e durante a implementação.

## Ordem de leitura para agentes

1. `AGENTS.md`
2. `MASTER_INDEX.md`
3. Documento do domínio afetado
4. Requisitos e critérios de aceite relacionados
5. ADRs, contratos e schemas aplicáveis
6. Código e testes existentes
7. Implementação
8. Validações
9. Atualização da documentação afetada

## Estados

`draft` → `review` → `approved` → `implemented` → `tested` → `verified` → `released`

Os estados não são equivalentes. Um documento existente não deve ser tratado como implementado ou verificado sem evidência correspondente.

## Estrutura

A estrutura completa está registrada em `MASTER_INDEX.md` e distribuída sob `docs/`, `src/`, `supabase/`, `evals/`, `tests/` e `.github/`.
