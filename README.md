# RELATÓRIO DE IMPLEMENTAÇÃO DE SERVIÇOS AWS: MODERNIZAÇÃO ABSTERGO

**Data:** 09 de abril de 2026  
**Empresa:** Abstergo Industries (Divisão Farmacêutica)  
**Responsável:** Raniere

---

## 1. Introdução
Este relatório detalha a estratégia de entrada da **Abstergo Industries** no ecossistema de nuvem AWS. Sendo uma indústria farmacêutica que opera atualmente com infraestrutura local (on-premises), o projeto foca na implementação inicial de três serviços fundamentais. O objetivo central é reduzir custos de manutenção física e garantir alta disponibilidade para dados críticos de pesquisa e desenvolvimento.

## 2. Descrição do Projeto
A implementação foi estruturada para migrar cargas de trabalho de arquivos e bancos de dados, estabelecendo uma base sólida de governança financeira desde o "Dia 1".

### Etapa 1: Amazon S3 (Simple Storage Service) com Lifecycle Policies
- **Foco da ferramenta:** Armazenamento escalável e durável de dados de pesquisa.
- **Caso de Uso:** Centralização de documentos de ensaios clínicos e fórmulas químicas. Ao utilizar políticas de ciclo de vida, arquivos que não são acessados há mais de 30 dias são movidos automaticamente para a classe **S3 Glacier Deep Archive**. Isso reduz drasticamente o custo em comparação com a manutenção de servidores de arquivos físicos e fitas de backup locais.

### Etapa 2: AWS Lambda (Serverless Computing)
- **Foco da ferramenta:** Processamento de dados sem necessidade de servidores ligados 24/7.
- **Caso de Uso:** Automação do processamento de relatórios de inventário e logs de temperatura de lotes farmacêuticos. Como o serviço é cobrado apenas por milissegundos de execução, a Abstergo elimina o custo fixo de manter servidores ligados para tarefas esporádicas, pagando apenas pelo processamento efetivamente utilizado.

### Etapa 3: AWS Budget & Cost Explorer
- **Foco da ferramenta:** Governança e controle financeiro proativo.
- **Caso de Uso:** Como a empresa é nova na nuvem, esta etapa garante que alertas sejam disparados caso o consumo exceda o orçamento planejado. A ferramenta permite identificar quais departamentos (Pesquisa, Logística ou Vendas) estão consumindo recursos, evitando surpresas na fatura mensal e permitindo ajustes de rota em tempo real.

---

## 3. Conclusão
A implementação inicial na **Abstergo Industries** tem como benefícios esperados a **eliminação de custos de capital (CapEx) com hardware físico e a adoção de um modelo de despesas operacionais (OpEx) sob demanda**. A transição para o modelo serverless e armazenamento em camadas garante que a farmacêutica cresça sua capacidade computacional sem aumentar proporcionalmente seus custos fixos. Recomenda-se, em uma fase futura, a exploração de serviços de IA (como Amazon SageMaker) para acelerar a análise de compostos químicos.

## 4. Anexos
* `planejamento_migracao_v1.pdf` https://docs.google.com/document/d/1dp6FZ7JUsqXQLt9eBcotpW4ObIBO-MySEYxh2BuC1-I/edit?usp=sharing
* `politicas_seguranca_dados_farmaceuticos.md`
* `estimativa_custos_mensais.xlsx`

---
**Assinatura do Responsável pelo Projeto:**

**Raniere** *Solutions Architecture & Tech Leadership*
