# 🥋 Sensei Chicão System

**Plataforma Híbrida para Gestão de Torneios de Karatê**

O **Sensei Chicão System** é uma plataforma híbrida desenvolvida para organizar, gerenciar e executar **torneios de karatê** em diferentes níveis — desde competições federativas nacionais até torneios abertos entre academias. Ele combina uma **parte online (central de inscrições e gerenciamento)** com uma **parte offline (execução do torneio)**, permitindo máxima flexibilidade e operação mesmo sem internet.

---

## 🌐 Parte Online – Central de Inscrições e Gerenciamento

A interface web da plataforma será responsável por:

- Contratação de torneios por federações ou organizadores
- Cadastro e gerenciamento de federações e academias
- Área de inscrições de atletas por categoria e modalidade (Kata ou Kumite)
- Armazenamento centralizado dos dados no banco de dados online
- Exportação dos dados para execução local

### Funcionalidades

- **Tipos de Torneio Suportados**:
  - Federativos (Nacional)
  - Torneios Open (Multi-estado)
- **Cadastro pré-existente**:
  - Federações e academias previamente registradas
- **Controle do contratante**:
  - Seleção de academias participantes por torneio
  - Criação de academias ad-hoc (para torneios estaduais)
- **Área de Inscrição**:
  - Escolha da categoria e modalidade por atleta
- **Banco de dados centralizado**:
  - Todas as informações ficam registradas online

---

## 💻 Parte Offline – Execução do Torneio no Local

A aplicação desktop do torneio será utilizada no local do evento, sem necessidade de conexão com a internet. Desenvolvida em **Electron**, ela realiza:

- Importação dos dados dos atletas, categorias e chaves
- Execução completa do torneio (chaveamento, lutas, placar, pontuação)
- Controle local de árbitros e cronômetro com interface amigável
- Relatórios automáticos (resultados, pódio, estatísticas)
- Exportação dos resultados para reintegração com o sistema online

### Funcionalidades

- **Chaveamento Automático**:
  - Separação de atletas por ranking e academia
  - Suporte a repescagem
- **Placar Eletrônico**:
  - Controle de pontos, penalidades, tempo, alertas sonoros
  - Exibição em telões ou TVs
- **Gerador de Relatórios**:
  - Resultado de lutas, campeões, rendimento por academia

---

## ⚙️ Stack Tecnológica Proposta

| Camada        | Tecnologia sugerida              |
|---------------|----------------------------------|
| Front-end     | React ou Angular (Ionic opcional)|
| Back-end      | .NET Core ou Node.js (Express)   |
| Banco de dados| SQL Server         |
| Offline       | Electron + SQLite                |
| Comunicação   | API REST + JWT Auth / WebSocket  |
| Hospedagem    | VPS, Azure, ou AWS               |

---

## 🧱 Modelagem de Dados (Entidades Principais)

- **Usuário** (com perfis: administrador, contratante, técnico, árbitro)
- **Estado**
- **Federação**
- **Academia**
- **Torneio**
- **AcademiaTorneio**
- **Categoria**
- **Atleta**
- **Inscrição**
- **Chaveamento**
- **Resultado**

---

## 🚀 Módulos e Rotas da API (Exemplo)

### Cadastro

- `POST /federacoes`
- `POST /academias`
- `POST /torneios`
- `POST /torneios/{id}/habilitar-academia`

### Inscrição

- `POST /inscricoes`
- `GET /torneios/{id}/inscricoes`
- `GET /categorias`

### Exportação

- `GET /torneios/{id}/exportar` → JSON

---

## 📅 Planejamento de Desenvolvimento

| Etapa | Entrega | Tempo Estimado |
|-------|---------|----------------|
| 1     | Modelagem de dados e API | 1 a 2 semanas |
| 2     | Cadastro de federações, academias, torneios | 1 semana |
| 3     | Módulo de inscrição de atletas | 1 a 2 semanas |
| 4     | Exportação dos dados para o módulo offline | 1 semana |
| 5     | Desenvolvimento do app Electron com chaveamento e placar | 3 a 4 semanas |
| 6     | Geração de relatórios no offline | 2 semanas |
| 7     | Sincronização dos resultados com sistema online | 1 a 2 semanas |

---

## 🔄 Sincronização Online ↔️ Offline

- **Exportação**: `.json` ou `.sqlite` com dados do torneio
- **Importação**: aplicação Electron consome localmente
- **Retorno**: resultado pode ser reimportado no sistema online

---

## 📈 Funcionalidades Futuras

- Exportação de boletos ou recibos
- Estatísticas de rendimento por atleta e academia
- Cadastro de árbitros com permissões restritas
- Transmissão ao vivo de placar (via telão)
- Suporte a múltiplos dispositivos locais via Wi-Fi (sem internet)

---

## 📚 Conclusão

O **Sensei Chicão System** nasce como uma solução robusta, modular e eficiente, pensada para a realidade dos torneios de karatê no Brasil. Ele une praticidade para organizadores e profissionalismo para atletas, técnicos e árbitros.

---
