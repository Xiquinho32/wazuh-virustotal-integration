# 🛡️ Wazuh + VirusTotal Integration

Integração entre o **Wazuh Manager (Ubuntu)** e a **API do VirusTotal**, com resposta automática a ficheiros maliciosos detetados por agentes (exemplo: Windows 10).

---

## ⚙️ Objetivo

Automatizar a deteção e remoção de ficheiros maliciosos através da integração entre:
- **Wazuh** — Monitorização e correlação de eventos;
- **VirusTotal** — Validação de reputação de ficheiros;
- **Active Response** — Execução automática de scripts para mitigação.

---

## 🧩 Estrutura do Projeto

wazuh-virustotal-integration/
│
├── scripts/
│ └── remove-threat.py
│
├── configs/
│ ├── ossec.conf
│ └── local_rules.xml
│
├── docs/
│ ├── architecture_diagram.png
│ └── agent_install_windows.md
│
└── README.md

---

## 🚀 Funcionamento

1. O **Wazuh Agent (Windows)** monitoriza o sistema em tempo real.  
2. Ao detetar um ficheiro suspeito, envia o evento para o **Wazuh Manager (Ubuntu)**.  
3. O Manager consulta a **API do VirusTotal** conforme definido em `/var/ossec/etc/ossec.conf`.  
4. Se o ficheiro for classificado como malicioso, o **Active Response** executa o script `remove-threat.py`, eliminando-o de forma segura.  
5. O resultado da ação é registado e notificado através das regras definidas em `local_rules.xml`.

---

## 🧠 Detalhes Técnicos

- O script `remove-threat.py` é baseado no exemplo oficial da **Wazuh Inc.**  
  > ⚠️ Copyright (C) 2015-2025, Wazuh Inc. — All rights reserved.  
  Adaptado para integração direta com o **VirusTotal** e execução no ambiente do **Wazuh Manager (Ubuntu)**.

- As regras e comandos foram configurados no `ossec.conf` e `local_rules.xml`.

- O agente utilizado para teste foi instalado num **Windows 10**, comunicando com o Manager via rede local.

---

## 🧱 Requisitos

- Ubuntu 22.04+ com Wazuh Manager instalado;  
- Wazuh Agent no Windows 10;  
- Ligação à Internet para consulta da API VirusTotal;  
- Chave API válida do VirusTotal (configurada no Manager).

---

## 📚 Documentação e Créditos

- [Documentação Oficial do Wazuh](https://documentation.wazuh.com/)
- [API VirusTotal](https://developers.virustotal.com/)
- Projeto adaptado e documentado por *[Francisco Morais]*.

---

## 📜 Licença

> Baseado em código da Wazuh Inc., sob licença GPL v2.  
> Este repositório destina-se a fins **educacionais e demonstrativos**.