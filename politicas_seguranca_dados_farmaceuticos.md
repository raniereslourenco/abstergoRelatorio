# POLÍTICA DE SEGURANÇA DE DADOS EM NUVEM (V1.0)

**Empresa:** Abstergo Industries (Divisão Farmacêutica)  
**Escopo:** Infraestrutura AWS e Dados de Pesquisa & Desenvolvimento  
**Classificação:** Confidencial / Uso Restrito  

---

## 1. Objetivo
Esta política define as diretrizes para garantir a Confidencialidade, Integridade e Disponibilidade (CID) dos dados farmacêuticos da Abstergo Industries armazenados na AWS, assegurando conformidade com normas regulatórias (como LGPD e diretrizes da ANVISA/FDA).

## 2. Controle de Acesso (IAM - Identity and Access Management)
* **Princípio do Privilégio Mínimo:** Todo colaborador terá acesso apenas aos recursos estritamente necessários para sua função.
* **Autenticação Multi-Fator (MFA):** Obrigatória para todos os usuários com acesso ao Console AWS e acesso programático.
* **Rotação de Credenciais:** Chaves de acesso (Access Keys) de desenvolvedores e sistemas de automação devem ser rotacionadas a cada 90 dias através do **AWS Secrets Manager**.
* **Segregação de Funções:** Engenheiros de Pesquisa não terão permissões de exclusão de dados em produção; essa função é exclusiva da equipe de Governança de Dados.

## 3. Criptografia e Proteção de Dados
Para proteger a propriedade intelectual das fórmulas:

* **Dados em Repouso (Encryption at Rest):**
    - Todos os buckets do **Amazon S3** contendo fórmulas e dados clínicos devem utilizar criptografia AES-256 via **AWS KMS (Key Management Service)**.
    - Discos de instâncias EC2 (EBS) devem ser criptografados por padrão.
* **Dados em Trânsito (Encryption in Transit):**
    - Toda comunicação entre a fábrica da Abstergo e a AWS deve ocorrer via **TLS 1.2+**.
    - Utilização obrigatória de **AWS Site-to-Site VPN** para tráfego entre o datacenter local e a VPC na nuvem.

## 4. Governança e Retenção (Amazon S3)
* **S3 Object Lock:** Implementar para documentos de ensaios clínicos finalizados, impedindo a exclusão ou alteração por um período definido (WORM - Write Once, Read Many), atendendo a requisitos legais.
* **Versionamento:** Ativado em todos os buckets críticos para permitir a recuperação de dados em caso de erro humano ou ataques de Ransomware.

## 5. Auditoria e Monitoramento
* **AWS CloudTrail:** Habilitado em todas as regiões para registrar todas as chamadas de API (quem fez o quê, quando e de onde).
* **Amazon GuardDuty:** Ativado para detecção inteligente de ameaças e tentativas de acesso não autorizadas ou comportamentos anômalos na conta.
* **AWS Config:** Monitoramento contínuo para garantir que as configurações de rede (Security Groups) não sejam alteradas para "aberto ao mundo" (0.0.0.0/0).

## 6. Plano de Resposta a Incidentes
* Em caso de detecção de acesso não autorizado a dados de fórmulas:
    1. Bloqueio imediato do usuário/role via IAM.
    2. Isolamento da rede (VPC Security Groups).
    3. Notificação ao DPO (Data Protection Officer) e equipe jurídica da Abstergo em até 4 horas.

---

## 7. Responsabilidades

| Ator | Responsabilidade |
| :--- | :--- |
| **AWS** | Segurança "da" nuvem (Hardware, Redes Físicas, Data Centers). |
| **Abstergo (TI)** | Segurança "na" nuvem (Configuração de Firewall, IAM, Criptografia). |
| **Pesquisadores** | Classificação correta da sensibilidade dos dados enviados. |

---
**Última Revisão:** 09 de abril de 2026  
**Aprovado por:** Raniere - Arquiteto de Soluções
