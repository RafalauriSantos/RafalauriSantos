<div align="center">

# ⚽ ArenaSys
### O Sistema Operacional para Complexos Esportivos

> **Gestão inteligente, agendamento instantâneo e fim do caos no WhatsApp.**

![Status](http://img.shields.io/static/v1?label=STATUS&message=EM%20PRODUÇÃO&color=GREEN&style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)
![AI Assisted](https://img.shields.io/badge/AI%20Pair-Programming-purple?style=for-the-badge&logo=openai&logoColor=white)

<br/>

![React](https://img.shields.io/badge/React-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)
![Vite](https://img.shields.io/badge/Vite-%23646CFF.svg?style=for-the-badge&logo=vite&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)
![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white)
![Bun](https://img.shields.io/badge/Bun-%23000000.svg?style=for-the-badge&logo=bun&logoColor=white)

<br/>

[**🌐 Ver Demo Online**](https://arenasys.com.br) &nbsp;|&nbsp; [**📄 Documentação da API**](./docs)

</div>

---

## 💡 Sobre o Projeto

O **ArenaSys** é uma plataforma SaaS Multi-tenant (B2B2C) que resolve a dor latente de donos de quadras: **perda de receita por desorganização**.

Diferente de agendas genéricas, o sistema foi desenhado para alta concorrência e velocidade, permitindo que o cliente final agende seu horário em menos de 30 segundos, enquanto o dono da quadra tem controle financeiro total.

### Principais Funcionalidades

| 🏢 Para a Arena (Admin) | ⚽ Para o Jogador (App) |
| :--- | :--- |
| **Dashboard Financeiro** com gráficos em tempo real | **Agendamento Instantâneo** sem login obrigatório |
| **Gestão de Quadras** e preços dinâmicos | **Pagamento Online** via Pix/Cartão (Asaas) |
| **Bloqueio de Horários** recorrentes (Mensalistas) | **Histórico de Jogos** e convites via WhatsApp |
| **Multi-Tenant:** Isolamento total de dados | **UX Mobile-First:** Funciona como app nativo |

---

## 🧠 Engenharia & Arquitetura

Este projeto utiliza uma arquitetura **Serverless** moderna focada em performance e segurança de dados.

### 1. Performance "Piscar de Olhos" (Optimistic UI)
> **Desafio:** Usuários abandonam o agendamento se a tela demorar a carregar.
> **Solução:** Implementação de **React Query** com *Optimistic Updates*. A interface responde instantaneamente ao clique do usuário, sincronizando com o banco em background. Redução de 40% no tempo de percepção de latência.

### 2. Segurança Bancária (Row Level Security)
> **Desafio:** Garantir que a "Arena A" jamais veja os dados da "Arena B" no mesmo banco.
> **Solução:** Políticas de RLS (Row Level Security) nativas do PostgreSQL. O isolamento é feito no nível do banco de dados, não apenas na aplicação. Mesmo se o frontend for comprometido, os dados vizinhos estão blindados.

### 3. Billing & Assinaturas (Integração Asaas)
> **Motor de Pagamentos:** Sistema completo de assinatura (SaaS) integrado via Webhooks.
> * Trial automático de 7 dias.
> * Bloqueio automático de inadimplentes via Edge Functions.
> * Webhooks seguros com validação de assinatura digital.

---

## 🎨 Layout & Preview

<div align="center">
  <img src="https://via.placeholder.com/800x450?text=Dashboard+ArenaSys+Dark+Mode" alt="ArenaSys Dashboard" style="border-radius: 10px; box-shadow: 0px 4px 20px rgba(0,0,0,0.5);">
  <br/><br/>
  <img src="https://via.placeholder.com/300x600?text=Mobile+Booking" alt="Mobile View" height="400" style="border-radius: 10px; margin-right: 20px;">
  <img src="https://via.placeholder.com/300x600?text=Financial+Reports" alt="Financial View" height="400" style="border-radius: 10px;">
</div>

---

## 🚀 Guia de Desenvolvimento (Receita de Bolo)

Este projeto utiliza **Bun** como runtime padrão para instalação e scripts, garantindo builds até 3x mais rápidos.

### 1. Pré-requisitos
* **Bun** instalado (ou Node.js 18+)
* Conta no **Supabase** (Projeto criado)
* Conta no **Asaas** (Sandbox ou Produção para billing)

### 2. Instalação

```bash
# Clone o repositório
git clone [https://github.com/RafalauriSantos/arena-sys.git](https://github.com/RafalauriSantos/arena-sys.git)
cd arena-sys

# Instale as dependências (Ultra rápido com Bun)
bun install

# Configure as variáveis de ambiente
cp .env.example .env.local
