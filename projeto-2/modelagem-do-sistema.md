# Modelagem do Sistema – Plataforma de Reservas de Viagens e Hotéis

> **Responsável:** Gabriel Borges Garcia
> Este documento é a **fonte única** do projeto 2. Os diagramas e as especificações devem seguir exatamente os nomes de atores, casos de uso, componentes e interfaces definidos aqui. Se algo precisar mudar, muda aqui primeiro.

---

## 1. Visão geral do sistema

A Plataforma de Reservas de Viagens e Hotéis permite que clientes busquem passagens aéreas e quartos de hotel informando destino, datas e número de passageiros ou hóspedes. A plataforma consulta a disponibilidade em tempo real diretamente nos sistemas das empresas parceiras, permite reservar a oferta escolhida, processa o pagamento por meio de um gateway externo e emite um voucher de confirmação enviado por e-mail. Hotéis e companhias aéreas parceiras contam com um portal próprio para cadastrar e atualizar suas ofertas e tarifas. Os principais requisitos compreendidos pelo grupo são: busca com disponibilidade em tempo real, reserva com bloqueio temporário de inventário, pagamento seguro sem armazenamento de dados de cartão, emissão automática de voucher e autogestão de ofertas pelos parceiros.

---

## 2. Requisitos

### 2.1 Requisitos funcionais

| ID | Requisito |
|----|-----------|
| RF01 | O sistema deve permitir buscar passagens aéreas por origem, destino, data de ida, data de volta (opcional) e número de passageiros. |
| RF02 | O sistema deve permitir buscar quartos de hotel por destino, data de check-in, data de check-out e número de hóspedes. |
| RF03 | O sistema deve verificar a disponibilidade de cada oferta em tempo real junto ao sistema do parceiro. |
| RF04 | O sistema deve permitir filtrar e ordenar os resultados (preço, horário, avaliação, número de escalas). |
| RF05 | O sistema deve permitir o cadastro de clientes. |
| RF06 | O sistema deve exigir autenticação para reservar, consultar reservas e acessar o portal do parceiro. |
| RF07 | O sistema deve permitir realizar a reserva de uma passagem ou de um quarto. |
| RF08 | O sistema deve processar o pagamento da reserva por meio de um gateway de pagamento externo. |
| RF09 | O sistema deve permitir aplicar um cupom de desconto durante a reserva. |
| RF10 | O sistema deve emitir um voucher após a confirmação do pagamento e enviá-lo por e-mail. |
| RF11 | O sistema deve permitir que o cliente consulte suas reservas. |
| RF12 | O sistema deve permitir cancelar uma reserva, com estorno conforme a política da tarifa. |
| RF13 | O sistema deve permitir que o parceiro cadastre, edite e desative ofertas (voos ou quartos). |
| RF14 | O sistema deve permitir que o parceiro gerencie tarifas e políticas de cancelamento das suas ofertas. |

### 2.2 Requisitos não funcionais

| ID | Requisito |
|----|-----------|
| RNF01 | A verificação de disponibilidade deve consultar o parceiro no momento da busca e novamente no momento da reserva. |
| RNF02 | Dados de cartão não são armazenados pela plataforma; são enviados diretamente ao gateway de pagamento. |
| RNF03 | Toda comunicação deve usar HTTPS. |
| RNF04 | A interface do cliente deve funcionar em navegadores de computador e celular. |

### 2.3 Regras de negócio

| ID | Regra |
|----|-------|
| RN01 | O número de passageiros por reserva aérea vai de 1 a 9. |
| RN02 | A data de check-out deve ser posterior à data de check-in; a data de volta deve ser igual ou posterior à de ida. |
| RN03 | Ao iniciar o pagamento, a oferta fica bloqueada por 15 minutos para o cliente. Se o pagamento não for concluído, o bloqueio é liberado. |
| RN04 | O voucher só é emitido após o pagamento ser aprovado. |
| RN05 | O cancelamento e o valor do estorno seguem a política da tarifa definida pelo parceiro. |
| RN06 | Um cupom só pode ser usado uma vez por reserva e deve estar dentro da validade. |

---

## 3. Atores

### 3.1 Atores principais

| Ator | Descrição |
|------|-----------|
| **Visitante** | Qualquer pessoa que acessa a plataforma sem estar autenticada. Pode buscar passagens e hotéis e se cadastrar. |
| **Cliente** | Visitante cadastrado e autenticado. **Herda de Visitante** (generalização). Pode reservar, pagar, consultar e cancelar reservas. |
| **Parceiro** | Empresa parceira autenticada no portal. Ator abstrato, especializado em **Hotel Parceiro** e **Companhia Aérea Parceira** (generalização). |
| **Hotel Parceiro** | Herda de Parceiro. Gerencia ofertas de quartos e suas tarifas. |
| **Companhia Aérea Parceira** | Herda de Parceiro. Gerencia ofertas de voos e suas tarifas. |

### 3.2 Atores secundários (sistemas externos)

| Ator | Descrição |
|------|-----------|
| **Sistema de Inventário do Parceiro** | Sistema do hotel ou da companhia aérea que informa a disponibilidade real de quartos e assentos. |
| **Gateway de Pagamento** | Serviço externo que autoriza pagamentos e realiza estornos. |
| **Serviço de E-mail** | Serviço externo que entrega o voucher e as notificações ao cliente. |

---

## 4. Casos de uso

### 4.1 Lista

| ID | Caso de uso | Ator(es) | Descrição resumida |
|----|-------------|----------|--------------------|
| UC01 | **Buscar Passagens Aéreas** | Visitante | Busca voos por origem, destino, datas e número de passageiros. |
| UC02 | **Buscar Quartos de Hotel** | Visitante | Busca quartos por destino, datas e número de hóspedes. |
| UC03 | **Verificar Disponibilidade** | Sistema de Inventário do Parceiro | Consulta em tempo real se a oferta ainda tem assentos ou quartos livres. |
| UC04 | **Filtrar Resultados** | Visitante | Aplica filtros e ordenação aos resultados de uma busca. |
| UC05 | **Cadastrar Cliente** | Visitante | Cria uma conta de cliente na plataforma. |
| UC06 | **Autenticar Usuário** | Cliente, Parceiro | Valida login e senha antes de operações protegidas. |
| UC07 | **Realizar Reserva** | Cliente | Reserva a oferta escolhida, informando os dados dos passageiros ou hóspedes. |
| UC08 | **Processar Pagamento** | Gateway de Pagamento | Envia o pagamento ao gateway e recebe a aprovação ou recusa. |
| UC09 | **Aplicar Cupom de Desconto** | Cliente | Aplica um cupom válido ao valor da reserva. |
| UC10 | **Emitir Voucher** | Serviço de E-mail | Gera o voucher da reserva confirmada e o envia por e-mail. |
| UC11 | **Consultar Reservas** | Cliente | Lista as reservas do cliente e seus status. |
| UC12 | **Cancelar Reserva** | Cliente, Gateway de Pagamento | Cancela uma reserva e solicita o estorno conforme a política da tarifa. |
| UC13 | **Gerenciar Ofertas** | Parceiro | Cadastra, edita e desativa voos ou quartos. |
| UC14 | **Gerenciar Tarifas** | Parceiro | Define preços, períodos e políticas de cancelamento das ofertas. |

### 4.2 Relacionamentos entre casos de uso

| Origem | Tipo | Destino | Justificativa |
|--------|------|---------|---------------|
| Buscar Passagens Aéreas | `<<include>>` | Verificar Disponibilidade | Toda busca precisa consultar a disponibilidade real. |
| Buscar Quartos de Hotel | `<<include>>` | Verificar Disponibilidade | Idem. |
| Realizar Reserva | `<<include>>` | Autenticar Usuário | Só clientes autenticados reservam. |
| Realizar Reserva | `<<include>>` | Verificar Disponibilidade | A disponibilidade é confirmada de novo no momento da reserva (RNF01). |
| Realizar Reserva | `<<include>>` | Processar Pagamento | Não existe reserva sem pagamento. |
| Realizar Reserva | `<<include>>` | Emitir Voucher | O voucher é emitido sempre que a reserva é confirmada (RN04). |
| Consultar Reservas | `<<include>>` | Autenticar Usuário | Dados pessoais exigem login. |
| Gerenciar Ofertas | `<<include>>` | Autenticar Usuário | Acesso ao portal do parceiro. |
| Gerenciar Tarifas | `<<include>>` | Autenticar Usuário | Idem. |
| Filtrar Resultados | `<<extend>>` | Buscar Passagens Aéreas | Opcional: o visitante pode ou não filtrar. |
| Filtrar Resultados | `<<extend>>` | Buscar Quartos de Hotel | Idem. |
| Aplicar Cupom de Desconto | `<<extend>>` | Realizar Reserva | Opcional: só ocorre se o cliente tiver um cupom. |
| Cancelar Reserva | `<<extend>>` | Consultar Reservas | Opcional: a partir da lista, o cliente pode cancelar uma reserva. |

> **Lembrete de notação:** a seta de `<<include>>` aponta **do caso base para o incluído**; a seta de `<<extend>>` aponta **da extensão para o caso base**. Ambas são tracejadas.

### 4.3 Associações ator ↔ caso de uso

| Ator | Casos de uso |
|------|--------------|
| Visitante | UC01, UC02, UC04, UC05 |
| Cliente (herda os de Visitante) | UC07, UC09, UC11, UC12 |
| Parceiro (herdado por Hotel Parceiro e Companhia Aérea Parceira) | UC13, UC14 |
| Sistema de Inventário do Parceiro | UC03 |
| Gateway de Pagamento | UC08, UC12 |
| Serviço de E-mail | UC10 |

> **Fronteira do sistema:** retângulo com o nome **"Plataforma de Reservas de Viagens e Hotéis"**. Todos os casos de uso ficam dentro; todos os atores ficam fora. Atores principais à esquerda, secundários à direita.

---

## 5. Componentes (arquitetura)

### 5.1 Pacotes e componentes

| Pacote | Componente | Responsabilidade |
|--------|------------|------------------|
| **Frontend** | **InterfaceWebCliente** | Telas de busca, reserva, pagamento e "Minhas reservas" usadas por visitantes e clientes. |
| **Frontend** | **PortalDoParceiro** | Telas usadas por hotéis e companhias aéreas para gerenciar ofertas e tarifas. |
| **Backend** | **ModuloDeAutenticacao** | Cadastro de clientes, login e validação de sessão. |
| **Backend** | **MotorDeBusca** | Executa buscas de voos e quartos, aplica filtros e ordenação. |
| **Backend** | **ModuloDeDisponibilidade** | Consulta o inventário dos parceiros em tempo real e controla o bloqueio temporário (RN03). |
| **Backend** | **ModuloDeReservas** | Cria, consulta e cancela reservas; aplica cupons; orquestra pagamento e voucher. |
| **Backend** | **ModuloDePagamento** | Integra com o gateway para autorizar pagamentos e estornos. |
| **Backend** | **GeradorDeVouchers** | Gera o voucher da reserva confirmada e solicita o envio por e-mail. |
| **Backend** | **ModuloDeParceiros** | Regras de negócio das ofertas e tarifas cadastradas pelos parceiros. |
| **Dados** | **BancoDeDados** | Armazena clientes, parceiros, ofertas, tarifas, reservas e vouchers. |
| **Serviços Externos** | **GatewayDePagamento** | Serviço externo de pagamento. |
| **Serviços Externos** | **APIInventarioParceiro** | API dos sistemas dos hotéis e companhias aéreas. |
| **Serviços Externos** | **ServicoDeEmail** | Serviço externo de envio de e-mail. |

### 5.2 Interfaces fornecidas e requeridas

| Componente | Fornece (pirulito) | Requer (soquete) |
|------------|--------------------|------------------|
| InterfaceWebCliente | — | IBusca, IReserva, IAutenticacao |
| PortalDoParceiro | — | IGestaoOfertas, IAutenticacao |
| ModuloDeAutenticacao | IAutenticacao | IPersistencia |
| MotorDeBusca | IBusca | IDisponibilidade, IPersistencia |
| ModuloDeDisponibilidade | IDisponibilidade | IInventarioParceiro, IPersistencia |
| ModuloDeReservas | IReserva | IAutenticacao, IDisponibilidade, IPagamento, IVoucher, IPersistencia |
| ModuloDePagamento | IPagamento | IGatewayPagamento |
| GeradorDeVouchers | IVoucher | IEnvioEmail, IPersistencia |
| ModuloDeParceiros | IGestaoOfertas | IAutenticacao, IPersistencia |
| BancoDeDados | IPersistencia | — |
| GatewayDePagamento | IGatewayPagamento | — |
| APIInventarioParceiro | IInventarioParceiro | — |
| ServicoDeEmail | IEnvioEmail | — |

### 5.3 Interfaces

| Interface | Serviços oferecidos |
|-----------|---------------------|
| IAutenticacao | cadastrar, autenticar, validarSessao |
| IBusca | buscarVoos, buscarQuartos, filtrarResultados |
| IDisponibilidade | consultarDisponibilidade, bloquearOferta, liberarBloqueio |
| IReserva | criarReserva, aplicarCupom, listarReservas, cancelarReserva |
| IPagamento | pagar, estornar |
| IVoucher | emitirVoucher |
| IGestaoOfertas | salvarOferta, desativarOferta, salvarTarifa |
| IPersistencia | ler, gravar |
| IGatewayPagamento | autorizar, estornar (API externa) |
| IInventarioParceiro | consultarInventario, reservarInventario (API externa) |
| IEnvioEmail | enviarEmail (API externa) |

### 5.4 Portas (recomendado)

Usar portas nos componentes que falam com o exterior:
- **ModuloDePagamento** – porta `pGateway` (para IGatewayPagamento).
- **ModuloDeDisponibilidade** – porta `pInventario` (para IInventarioParceiro).
- **GeradorDeVouchers** – porta `pEmail` (para IEnvioEmail).
- **ModuloDeReservas** – porta `pApiReservas` (expõe IReserva ao Frontend).

---

## 6. Rastreabilidade: caso de uso → componentes

| Caso de uso | Componentes envolvidos |
|-------------|------------------------|
| UC01 / UC02 Buscar | InterfaceWebCliente → MotorDeBusca → ModuloDeDisponibilidade → APIInventarioParceiro |
| UC03 Verificar Disponibilidade | ModuloDeDisponibilidade → APIInventarioParceiro |
| UC04 Filtrar Resultados | InterfaceWebCliente → MotorDeBusca |
| UC05 Cadastrar Cliente | InterfaceWebCliente → ModuloDeAutenticacao → BancoDeDados |
| UC06 Autenticar Usuário | InterfaceWebCliente / PortalDoParceiro → ModuloDeAutenticacao |
| UC07 Realizar Reserva | InterfaceWebCliente → ModuloDeReservas → (Disponibilidade, Pagamento, Vouchers, BancoDeDados) |
| UC08 Processar Pagamento | ModuloDeReservas → ModuloDePagamento → GatewayDePagamento |
| UC09 Aplicar Cupom | ModuloDeReservas → BancoDeDados |
| UC10 Emitir Voucher | ModuloDeReservas → GeradorDeVouchers → ServicoDeEmail |
| UC11 Consultar Reservas | InterfaceWebCliente → ModuloDeReservas → BancoDeDados |
| UC12 Cancelar Reserva | ModuloDeReservas → ModuloDePagamento → GatewayDePagamento |
| UC13 / UC14 Gerenciar Ofertas e Tarifas | PortalDoParceiro → ModuloDeParceiros → BancoDeDados |
