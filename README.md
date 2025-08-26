# **Automacao de Limpeza e Monitoramento de Backups - Konsist**

[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/status-stable-success.svg)]()

> Script em Python para **gerenciar e monitorar backups do sistema Konsist**, garantindo integridade e enviando alertas via Telegram.

---

## **📖 Sumário**

* [Descrição](#-descrição)
* [Funcionalidades](#-funcionalidades)
* [Pré-requisitos](#-pré-requisitos)
* [Instalação](#-instalação)
* [Configuração](#-configuração)
* [Como Usar](#-como-usar)
* [Exemplo de Saída](#-exemplo-de-saída)
* [Logs e Alertas](#-logs-e-alertas)
* [Melhorias Futuras](#-melhorias-futuras)
* [Licença](#-licença)

---

## **📌 Descrição**

Este projeto é uma automação para **verificação e manutenção de backups do sistema Konsist**. Ele percorre todos os discos do sistema, encontra pastas relacionadas ao Konsist, valida a existência de backups recentes e remove arquivos antigos para economizar espaço.

Além disso, o script envia **alertas automáticos via Telegram** em situações críticas, como:

* Ausência de backup do dia anterior.
* Backup mais recente vazio.
* Erros durante a execução.

---

## **⚙️ Funcionalidades**

✅ Varredura automática de todos os discos do sistema
✅ Ignora pastas críticas do Windows (`Program Files`, `ProgramData`, etc.)
✅ Validação da integridade dos backups
✅ Limpeza de arquivos antigos, mantendo os **N mais recentes**
✅ Envio de alertas via **Telegram**
✅ Registro detalhado em arquivo de log e no console

---

## **✅ Pré-requisitos**

* **Sistema Operacional:** Windows
* **Python:** 3.8 ou superior
* **Dependências:** Somente bibliotecas padrão do Python:

  * `os`, `re`, `json`, `logging`, `datetime`, `urllib`, `pathlib`

---

## **📥 Instalação**

Clone este repositório e acesse a pasta:

```bash
git clone https://github.com/seu-usuario/automacao-konsist.git
cd automacao-konsist
```

---

## **🔑 Configuração**

Antes de rodar, configure as seguintes variáveis de ambiente:

```bash
set TELEGRAM_TOKEN=seu_token_do_telegram
set TELEGRAM_CHAT_ID=seu_chat_id
```

| Variável           | Descrição                                                 |
| ------------------ | --------------------------------------------------------- |
| `TELEGRAM_TOKEN`   | Token do bot do Telegram (criado via BotFather)           |
| `TELEGRAM_CHAT_ID` | ID do chat ou grupo que receberá os alertas               |
| `MANTER_ARQUIVOS`  | Quantidade de backups a manter por pasta (default: **7**) |

---

## **▶ Como Usar**

Execute o script diretamente com Python:

```bash
python automacao_konsist_v5.py
```

Se quiser **agendar para rodar diariamente**, use o **Agendador de Tarefas do Windows**:

1. Abra o Agendador de Tarefas (`taskschd.msc`);
2. Crie uma nova tarefa;
3. Configure o gatilho para rodar diariamente (por exemplo, às 23h);
4. Em **Ação**, adicione:

   ```
   python caminho_completo\automacao_konsist_v5.py
   ```

---

## **📜 Exemplo de Saída no Console**

```
2025-08-26 14:00:00 - INFO - Iniciando automação de limpeza de backups...
2025-08-26 14:00:01 - INFO - Discos encontrados: ['C:\\', 'D:\\']
2025-08-26 14:00:05 - INFO - 📂 Pasta: D:\Backups\Konsist
2025-08-26 14:00:05 - WARNING - ⚠ ATENÇÃO: Não existe backup de ontem (2025-08-25)!
2025-08-26 14:00:07 - INFO - 🗑 Apagando 3 backups antigos...
```

---

## **📲 Exemplo de Alerta no Telegram**

```
⚠ Backup do Konsist do(a) DOMÍNIO está em estado de erro:

• Diretório do backup:
D:\Backups\Konsist
```

---

## **📂 Estrutura do Projeto**

```
.
├── automacao_konsist_v5.py   # Script principal
├── backup_automation.log     # Log da execução (gerado automaticamente)
├── README.md                 # Documentação do projeto
```

---

## **📊 Melhorias Futuras**

* [ ] Suporte a compressão automática dos backups antigos
* [ ] Integração com sistemas de monitoramento (Zabbix, Prometheus)
* [ ] Execução como serviço do Windows

---
