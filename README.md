<h1 align="center">🌐 Protocolos de Rede</h1>

<p align="center">
  <i>Guia prático dos principais protocolos de rede: porta, função e exemplos reais de uso no terminal.</i>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/protocolos-20-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/shell-bash-green?style=for-the-badge&logo=gnubash&logoColor=white" />
  <img src="https://img.shields.io/badge/idioma-PT--BR-yellow?style=for-the-badge" />
</p>

---

## 📑 Índice

- [⚡ Tabela rápida](#-tabela-rápida)
- [🖥️ Usando o script no terminal](#️-usando-o-script-no-terminal)
- [🌍 Web](#-web) · [📁 Arquivos](#-transferência-de-arquivos) · [🔐 Acesso remoto](#-acesso-remoto) · [📧 E-mail](#-e-mail)
- [🏗️ Infraestrutura](#️-infraestrutura) · [📊 Gerência e diretório](#-gerência-e-diretório) · [🗄️ Banco de dados](#️-banco-de-dados) · [🩺 Diagnóstico](#-diagnóstico)
- [🧠 Conceitos importantes](#-conceitos-importantes)

---

## ⚡ Tabela rápida

| Protocolo | Porta | Transporte | Para que serve |
|:---|:---:|:---:|:---|
| **HTTP** | `80` | TCP | Navegação web sem criptografia |
| **HTTPS** | `443` | TCP | Navegação web segura (TLS) |
| **FTP** | `20` `21` | TCP | Transferência de arquivos |
| **SSH** | `22` | TCP | Acesso remoto seguro |
| **SFTP** | `22` | TCP | Transferência de arquivos segura |
| **Telnet** | `23` | TCP | Acesso remoto inseguro / teste de portas |
| **SMTP** | `25` `587` | TCP | Envio de e-mails |
| **DNS** | `53` | UDP/TCP | Tradução de nomes em IPs |
| **DHCP** | `67` `68` | UDP | Distribuição automática de IPs |
| **TFTP** | `69` | UDP | Transferência simples (firmware, boot) |
| **POP3** | `110` `995` | TCP | Download de e-mails |
| **NTP** | `123` | UDP | Sincronização de horário |
| **IMAP** | `143` `993` | TCP | Acesso a e-mails no servidor |
| **SNMP** | `161` `162` | UDP | Monitoramento de equipamentos |
| **LDAP** | `389` `636` | TCP | Serviços de diretório (AD) |
| **SMB** | `445` | TCP | Compartilhamento Windows |
| **MySQL** | `3306` | TCP | Banco de dados MySQL/MariaDB |
| **RDP** | `3389` | TCP | Área de trabalho remota |
| **PostgreSQL** | `5432` | TCP | Banco de dados PostgreSQL |
| **ICMP** | — | IP | Diagnóstico (ping, traceroute) |

---

## 🖥️ Usando o script no terminal

O repositório inclui o `protocolos.sh`, um guia colorido direto na linha de comando.

```bash
chmod +x protocolos.sh

./protocolos.sh           # mostra todos os protocolos
./protocolos.sh lista     # tabela resumida
./protocolos.sh ssh       # busca por nome
./protocolos.sh 443       # busca por porta
./protocolos.sh email     # busca por categoria
```

Saída de exemplo:

```text
╭── HTTPS · Web
│  Porta: 443    Transporte: TCP
│  Para que serve: HTTP protegido por TLS: garante sigilo e autenticidade na web.
│  Exemplo:
│    $ curl -v https://example.com
│    ↳ Exibe o handshake TLS e o certificado do site.
╰────────────────────────────────────────────────────────────
```

---

## 🌍 Web

### HTTP — `80/TCP`
> Protocolo base da web. Transfere páginas, imagens e APIs **sem criptografia**.

```bash
curl -I http://example.com
# Mostra apenas os cabeçalhos da resposta (código de status, servidor, tipo de conteúdo)
```

### HTTPS — `443/TCP`
> HTTP dentro de um túnel **TLS**. Garante que ninguém leia ou altere os dados no caminho.

```bash
curl -v https://example.com
# Exibe o handshake TLS e os dados do certificado do site
```

---

## 📁 Transferência de arquivos

### FTP — `20/TCP` (dados) · `21/TCP` (controle)
> Protocolo clássico de transferência de arquivos. Senha e dados trafegam **em texto puro**.

```bash
ftp ftp.exemplo.com
# Dentro da sessão: ls, cd, get arquivo.txt, put arquivo.txt, bye
```

### SFTP — `22/TCP`
> Transferência de arquivos **segura**, rodando por dentro do SSH.

```bash
sftp usuario@192.168.0.10
# sftp> put relatorio.pdf      → envia
# sftp> get backup.tar.gz      → baixa
```

### TFTP — `69/UDP`
> Versão mínima do FTP, **sem autenticação**. Usado para atualizar firmware e boot via rede (PXE).

```bash
tftp 192.168.0.1 -c get config.txt
# Baixa um arquivo de configuração de um roteador ou switch
```

### SMB — `445/TCP`
> Compartilhamento de arquivos e impressoras em redes **Windows** (e Samba no Linux).

```bash
smbclient -L //192.168.0.20 -U usuario
# Lista as pastas compartilhadas da máquina
```

---

## 🔐 Acesso remoto

### SSH — `22/TCP`
> Acesso a servidores por terminal **criptografado**. Padrão para administração de sistemas.

```bash
ssh usuario@192.168.0.10
ssh -p 2222 usuario@servidor.com   # usando uma porta personalizada
```

### Telnet — `23/TCP`
> Acesso remoto antigo e **inseguro** (tudo em texto puro). Hoje é útil para **testar se uma porta está aberta**.

```bash
telnet example.com 80
# "Connected" = porta aberta · "Connection refused" = porta fechada
```

### RDP — `3389/TCP`
> Área de trabalho remota do Windows, com interface gráfica completa.

```bash
xfreerdp /v:192.168.0.30 /u:usuario   # Linux
mstsc /v:192.168.0.30                 # Windows
```

---

## 📧 E-mail

### SMTP — `25/TCP` (servidores) · `587/TCP` (clientes, com STARTTLS)
> **Envia** e-mails do cliente para o servidor e entre servidores.

```bash
openssl s_client -starttls smtp -connect smtp.gmail.com:587
# Abre uma conversa manual com o servidor (comandos: EHLO, MAIL FROM, RCPT TO...)
```

### POP3 — `110/TCP` · `995/TCP` (SSL)
> **Baixa** os e-mails para o dispositivo e geralmente os remove do servidor.

```bash
openssl s_client -connect pop.gmail.com:995
```

### IMAP — `143/TCP` · `993/TCP` (SSL)
> **Acessa** os e-mails mantendo-os no servidor, sincronizando entre vários dispositivos.

```bash
openssl s_client -connect imap.gmail.com:993
```

| | POP3 📥 | IMAP 🔄 |
|:---|:---:|:---:|
| E-mails ficam no servidor | ❌ | ✅ |
| Sincroniza entre dispositivos | ❌ | ✅ |
| Funciona bem offline | ✅ | ⚠️ |

---

## 🏗️ Infraestrutura

### DNS — `53/UDP` e `TCP`
> A "agenda telefônica" da internet: traduz `google.com` em um endereço IP.

```bash
dig google.com A          # endereço IPv4
dig google.com MX         # servidores de e-mail do domínio
nslookup google.com       # alternativa (Windows e Linux)
```

### DHCP — `67/UDP` (servidor) · `68/UDP` (cliente)
> Entrega automaticamente **IP, máscara, gateway e DNS** para quem entra na rede.

```bash
sudo dhclient -v eth0     # Linux: solicita um novo IP
ipconfig /renew           # Windows
```

### NTP — `123/UDP`
> Mantém o **relógio** de todos os dispositivos sincronizado — essencial para logs e certificados.

```bash
ntpdate -q pool.ntp.org   # consulta a hora sem alterar o relógio
timedatectl               # mostra o status de sincronização (Linux)
```

---

## 📊 Gerência e diretório

### SNMP — `161/UDP` (consultas) · `162/UDP` (traps/alertas)
> Monitora roteadores, switches e servidores: CPU, tráfego, interfaces, temperatura.

```bash
snmpwalk -v2c -c public 192.168.0.1
# Lista todas as informações que o equipamento disponibiliza
```

### LDAP — `389/TCP` · `636/TCP` (LDAPS)
> Consulta **serviços de diretório** como o Active Directory: usuários, grupos e permissões.

```bash
ldapsearch -x -H ldap://servidor -b "dc=empresa,dc=com"
```

---

## 🗄️ Banco de dados

### MySQL / MariaDB — `3306/TCP`

```bash
mysql -h 127.0.0.1 -P 3306 -u root -p
```

### PostgreSQL — `5432/TCP`

```bash
psql -h localhost -p 5432 -U postgres
```

---

## 🩺 Diagnóstico

### ICMP — sem porta (camada de rede)
> Envia mensagens de controle e erro. É o que faz o `ping` e o `traceroute` funcionarem.

```bash
ping -c 4 8.8.8.8         # testa se o destino responde
traceroute google.com     # mostra o caminho até o destino (Windows: tracert)
```

### 🔎 Bônus: descobrindo portas abertas

```bash
ss -tuln                  # portas escutando na sua máquina (Linux)
netstat -an               # alternativa (Windows/macOS)
nmap -sV 192.168.0.1      # varre as portas de um host e identifica os serviços
```

> ⚠️ Use o `nmap` apenas em redes e equipamentos que você tem autorização para testar.

---

## 🧠 Conceitos importantes

**TCP vs UDP**

| | TCP 🤝 | UDP ⚡ |
|:---|:---:|:---:|
| Conexão | Estabelece antes de enviar | Envia direto |
| Garante entrega e ordem | ✅ | ❌ |
| Velocidade | Menor | Maior |
| Usado em | Web, e-mail, SSH, arquivos | DNS, DHCP, streaming, jogos |

**Faixas de portas**

| Faixa | Nome | Exemplos |
|:---|:---|:---|
| `0 – 1023` | Portas bem conhecidas | 22, 80, 443 |
| `1024 – 49151` | Portas registradas | 3306, 3389, 5432 |
| `49152 – 65535` | Portas dinâmicas/privadas | Usadas temporariamente pelos clientes |

**Seguro vs inseguro**

| ❌ Inseguro | ✅ Substituto seguro |
|:---|:---|
| HTTP (80) | HTTPS (443) |
| Telnet (23) | SSH (22) |
| FTP (21) | SFTP (22) / FTPS |
| POP3 (110) / IMAP (143) | POP3S (995) / IMAPS (993) |

---

<p align="center">
  Feito com 💙 para estudos de redes · Contribuições são bem-vindas!
</p>
