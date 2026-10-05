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

| # | Artefato | Descrição | Arquivo |
|---|----------|-----------|---------|
| 1 | **Diagrama de Atividades** | Fluxo principal do empréstimo à devolução, com decisões, fluxos alternativos (livro indisponível, multa) e raias por ator | [`diagramas/atividades`](diagramas/atividades) |
| 2 | **Diagrama de Sequência** | Interação entre atores e sistema no cenário **“Realizar Empréstimo”** | [`diagramas/sequencia`](diagramas/sequencia) |
| 3 | **Diagrama de Classes (macro)** | Classes principais, atributos, métodos, visibilidade, herança (`Usuario` → `Aluno`/`Professor`) e multiplicidades | [`diagramas/classes`](diagramas/classes) |

### Diagrama de Atividades
![Diagrama de Atividades](diagramas/atividades/diagrama-atividades.png)

### Diagrama de Sequência
![Diagrama de Sequência](diagramas/sequencia/diagrama-sequencia.png)

### Diagrama de Classes
![Diagrama de Classes](diagramas/classes/diagrama-classes.png)

---

## 📁 Estrutura do repositório

```
.
├── README.md
├── docs/
│   ├── capa.pdf
│   ├── descricao-da-aplicacao.md
│   ├── consideracoes-finais.md
│   └── trabalho-completo.pdf      # versão entregue no Turing
└── diagramas/
    ├── atividades/
    │   ├── diagrama-atividades.png
    │   └── diagrama-atividades.[drawio|puml|mdj]
    ├── sequencia/
    │   ├── diagrama-sequencia.png
    │   └── diagrama-sequencia.[drawio|puml|mdj]
    └── classes/
        ├── diagrama-classes.png
        └── diagrama-classes.[drawio|puml|mdj]
```

> Os arquivos-fonte (`.drawio`, `.puml`, `.mdj`) ficam versionados junto das imagens para permitir edição futura.

---

## 🛠️ Ferramentas utilizadas

- [Draw.io (diagrams.net)](https://app.diagrams.net/)
- [PlantUML](https://plantuml.com/)
- [StarUML](https://staruml.io/)

*(Mantenha apenas as que o grupo realmente usou.)*

### Como visualizar/editar os diagramas

- **Draw.io:** abra [app.diagrams.net](https://app.diagrams.net/) → *Arquivo → Abrir de → Dispositivo* → selecione o `.drawio`.
- **PlantUML:** use a extensão do VS Code *PlantUML* ou o [servidor online](https://www.plantuml.com/plantuml) para renderizar o `.puml`.
- **StarUML:** abra o arquivo `.mdj` diretamente no programa.

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
