# ✈️🏨 Plataforma de Reservas de Viagens e Hotéis – Modelagem UML

**Tema escolhido:** Plataforma de Reservas de Viagens e Hotéis
**Artefatos:** Diagrama de Casos de Uso e Diagrama de Componentes

---

## 👥 Integrantes e divisão

| Integrante | Matrícula | Responsabilidade | Pasta |
|------------|-----------|------------------|-------|
| Gabriel Borges Garcia | 202201691 | Requisitos, atores, casos de uso, componentes e interfaces (modelagem do sistema); revisão e montagem do PDF final | [`modelagem-do-sistema.md`](modelagem-do-sistema.md) e [`entrega/`](entrega/) |
| [Integrante 2] | [Matrícula] | Desenhar o **Diagrama de Casos de Uso** | [`casos-de-uso/`](casos-de-uso/) |
| [Integrante 3] | [Matrícula] | Escrever a **especificação textual** de cada caso de uso | [`casos-de-uso/`](casos-de-uso/) |
| [Integrante 4] | [Matrícula] | Desenhar o **Diagrama de Componentes** | [`componentes/`](componentes/) |
| [Integrante 5] | [Matrícula] | Escrever o **dicionário de componentes** e a **tabela de símbolos** | [`componentes/`](componentes/) |

> ⚠️ **Antes de começar, leiam [`modelagem-do-sistema.md`](modelagem-do-sistema.md).** Todos os nomes (atores, casos de uso, componentes, interfaces) já estão definidos lá. Não inventem nomes novos: se precisar mudar algo, falem com o Gabriel para atualizar o documento primeiro.

---

## 🛠️ Ferramenta de modelagem

**[A definir pelo grupo]** – sugestão: **PlantUML** (igual ao projeto 1) ou **Draw.io**.
Os dois diagramas devem usar **a mesma ferramenta**, porque a tabela de símbolos é uma só. Os arquivos-fonte (`.puml`, `.drawio`/`.xml`, `.asta` ou `.mdj`) **são entregáveis** e precisam estar nas pastas.

---

## 📁 Estrutura

```
projeto-2/
├── README.md                  ← este arquivo
├── modelagem-do-sistema.md    ← LEIA PRIMEIRO (Gabriel)
├── casos-de-uso/              ← Integrantes 2 e 3
├── componentes/               ← Integrantes 4 e 5
└── entrega/                   ← PDF e .zip (Gabriel)
```

Cada pasta tem um `README.md` explicando o que colocar nela.

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
