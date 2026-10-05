# 📚 Sistema de Biblioteca Universitária – Modelagem UML

> Trabalho de modelagem UML da disciplina **[NOME DA DISCIPLINA]** – Universidade Federal de Goiás (UFG) – [SEMESTRE/ANO]

**Tema escolhido:** Tema 2 – Sistema de Biblioteca Universitária

---

## 👥 Integrantes

| Nome | Matrícula | GitHub |
|------|-----------|--------|
| Carlos Antônio Rodrigues Soares | [Matrícula] | [@usuario](https://github.com/usuario) |
| Gabriel Borges Garcia | [Matrícula] | [@usuario](https://github.com/usuario) |
| Heitor Gonçalves Costa | [Matrícula] | [@usuario](https://github.com/usuario) |
| Luís Henrique Oliveira de Jesus | [Matrícula] | [@usuario](https://github.com/usuario) |
| Rafael [Sobrenome] | [Matrícula] | [@usuario](https://github.com/usuario) |

**Professor:** [Diogo Oliveira Santos](http://www.docente.ufg.br/diogogyn100)

---

## 🎯 Objetivo

Aplicar os conceitos de modelagem orientada a objetos com UML a partir da descrição de uma aplicação real. Não há implementação de código: o foco está na **correção dos diagramas, na clareza visual e na coerência entre eles**.

## 📝 Sobre a aplicação

O sistema gerencia o funcionamento de uma biblioteca universitária. **Alunos e professores** podem consultar o acervo, reservar livros, realizar e renovar empréstimos e devolver obras. **Bibliotecários** gerenciam o acervo (livros e exemplares), acompanham os empréstimos e aplicam multas em caso de atraso. O cálculo e o registro das multas são feitos pelo **Sistema de Multas**.

**Atores:** Aluno, Professor, Bibliotecário e Sistema de Multas.

**Fluxo principal:**
Usuário consulta livro → verifica disponibilidade → realiza empréstimo → sistema registra prazo → usuário devolve → bibliotecário verifica atraso → aplica multa (se houver).

**Fluxos alternativos considerados:**
- Livro sem exemplares disponíveis → usuário realiza uma reserva.
- Usuário com multa pendente ou limite de empréstimos atingido → empréstimo negado.
- Renovação de empréstimo (negada se houver reserva de outro usuário para o livro).

**Principais classes:** `Usuario`, `Aluno`, `Professor`, `Bibliotecario`, `Livro`, `Exemplar`, `Emprestimo`, `Reserva`, `Multa`.

A descrição completa (mínimo de 1 página) está em [`docs/descricao-da-aplicacao.md`](docs/descricao-da-aplicacao.md).

---

## 🧩 Artefatos produzidos

Todos os diagramas são escritos em **PlantUML** (código-fonte em `.puml`).

| # | Artefato | Descrição | Código-fonte |
|---|----------|-----------|--------------|
| 1 | **Diagrama de Atividades** | Fluxo principal do empréstimo à devolução, com decisões, fluxos alternativos (livro indisponível, multa) e raias por ator | [`atividades.puml`](diagramas/atividades/atividades.puml) |
| 2 | **Diagrama de Sequência** | Interação entre atores e sistema no cenário **“Realizar Empréstimo”** | [`sequencia.puml`](diagramas/sequencia/sequencia.puml) |
| 3 | **Diagrama de Classes (macro)** | Classes principais, atributos, métodos, visibilidade, herança e multiplicidades | [`classes.puml`](diagramas/classes/classes.puml) |

<!-- Descomente cada imagem depois de gerar o PNG correspondente.

### Diagrama de Atividades
![Diagrama de Atividades](diagramas/atividades/atividades.png)

### Diagrama de Sequência
![Diagrama de Sequência](diagramas/sequencia/sequencia.png)

### Diagrama de Classes
![Diagrama de Classes](diagramas/classes/classes.png)
-->

---

## 📁 Estrutura do repositório

```
.
├── README.md
├── .gitignore
├── docs/
│   ├── descricao-da-aplicacao.md
│   ├── consideracoes-finais.md
│   └── (capa e PDF final entregue no Turing)
└── diagramas/
    ├── atividades/
    │   ├── atividades.puml
    │   └── atividades.png
    ├── sequencia/
    │   ├── sequencia.puml
    │   └── sequencia.png
    └── classes/
        ├── classes.puml
        └── classes.png
```

---

## 🛠️ Como gerar as imagens (PlantUML)

**Opção 1 – VS Code:** instale a extensão *PlantUML*, abra o `.puml` e use `Alt + D` para visualizar. Para exportar, clique com o botão direito → *Export Current Diagram*.

**Opção 2 – Online:** cole o código em [plantuml.com/plantuml](https://www.plantuml.com/plantuml) e baixe o PNG.

**Opção 3 – Linha de comando** (requer Java e o `plantuml.jar`):

```bash
java -jar plantuml.jar -tpng diagramas/**/*.puml
```

---

## 💭 Considerações finais

[Resumo de 1 parágrafo: principais decisões de modelagem, dificuldades encontradas e aprendizados do grupo. O texto completo está em [`docs/consideracoes-finais.md`](docs/consideracoes-finais.md).]

---

## 📌 Entrega e apresentação

- Entrega realizada pela plataforma **Turing**, com todos os membros do grupo listados na descrição da atividade.
- Apresentação **obrigatória** para obtenção da nota (presença mínima de 75% dos integrantes).

---

## 📄 Licença

Projeto acadêmico, sem fins comerciais.
