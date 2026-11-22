# ✈️🏨 Plataforma de Reservas de Viagens e Hotéis – Modelagem UML

**Tema escolhido:** Plataforma de Reservas de Viagens e Hotéis
**Artefatos:** Diagrama de Casos de Uso e Diagrama de Componentes

---

## 👥 Integrantes e divisão

| Integrante | Matrícula | Responsabilidade | Pasta |
|------------|-----------|------------------|-------|
| Gabriel Borges Garcia | 202201691 | Requisitos, atores, casos de uso, componentes e interfaces (modelagem do sistema); revisão e montagem do PDF final | [`docs/`](docs/) e [`entrega/`](entrega/) |
| [Integrante 2] | [Matrícula] | Desenhar o **Diagrama de Casos de Uso** | [`casos-de-uso/diagrama/`](casos-de-uso/diagrama/) |
| [Integrante 3] | [Matrícula] | Escrever a **especificação textual** de cada caso de uso | [`casos-de-uso/especificacoes/`](casos-de-uso/especificacoes/) |
| [Integrante 4] | [Matrícula] | Desenhar o **Diagrama de Componentes** | [`componentes/diagrama/`](componentes/diagrama/) |
| [Integrante 5] | [Matrícula] | Escrever o **dicionário de componentes** e a **tabela de símbolos** | [`componentes/dicionario/`](componentes/dicionario/) |

> ⚠️ **Antes de começar, leiam [`docs/modelagem-do-sistema.md`](docs/modelagem-do-sistema.md).** Todos os nomes (atores, casos de uso, componentes, interfaces) já estão definidos lá. Não inventem nomes novos: se precisar mudar algo, falem com o Gabriel para atualizar o documento primeiro.

---

## 🛠️ Ferramenta de modelagem

**[A definir pelo grupo]** – sugestão: **PlantUML** (igual ao projeto 1) ou **Draw.io**.
Os dois diagramas devem usar **a mesma ferramenta**, porque a tabela de símbolos é uma só. Os arquivos-fonte (`.puml`, `.drawio`/`.xml`, `.asta` ou `.mdj`) **são entregáveis** e precisam estar nas pastas.

---

## 📁 Estrutura

```
projeto-2/
├── README.md
├── docs/
│   └── modelagem-do-sistema.md      ← fonte única (Gabriel)
├── casos-de-uso/
│   ├── diagrama/                    ← arquivo-fonte + imagem (Integrante 2)
│   └── especificacoes/              ← especificações UC01–UC14 (Integrante 3)
├── componentes/
│   ├── diagrama/                    ← arquivo-fonte + imagem (Integrante 4)
│   └── dicionario/                  ← dicionário + tabela de símbolos (Integrante 5)
└── entrega/                         ← PDF final e .zip (Gabriel)
```

---

## ✅ Checklist do enunciado

**Casos de uso**
- [ ] Fronteira do sistema com o nome do sistema
- [ ] Atores principais e secundários
- [ ] Associações ator ↔ caso de uso
- [ ] Generalização de atores (Visitante → Cliente; Parceiro → Hotel Parceiro / Companhia Aérea Parceira)
- [ ] `<<include>>` e `<<extend>>`
- [ ] Especificação de cada caso de uso: nome, atores, pré-condições, fluxo principal, fluxos alternativos/exceção

**Componentes**
- [ ] Componentes agrupados em pacotes (Frontend, Backend, Dados, Serviços Externos)
- [ ] Interfaces fornecidas (pirulito) e requeridas (soquete)
- [ ] Dependências com setas tracejadas
- [ ] Portas (recomendado)
- [ ] Dicionário de componentes justificando dependências e interfaces

**Entrega**
- [ ] PDF: capa (nomes, matrículas, tema), visão geral, seção de casos de uso, seção de componentes, tabela de símbolos e ferramenta usada
- [ ] Arquivos-fonte da ferramenta
- [ ] `.zip` nomeado `Tema_NomeDoGrupo.zip`
- [ ] **Todos os integrantes enviam** o trabalho no ambiente virtual (senão, penalidade individual)
