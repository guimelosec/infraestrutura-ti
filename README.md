# infraestrutura-ti

# Infraestrutura de TI

Repositório destinado à documentação, scripts, procedimentos e projetos relacionados à infraestrutura de TI.

## Conteúdo

- Servidores
- Active Directory
- Hyper-V
- Redes
- Firewall
- Backup
- Impressoras
- Scripts PowerShell
- Troubleshooting
- Documentação técnica

## Objetivo

Centralizar conhecimento técnico e procedimentos utilizados na administração da infraestrutura de TI.
<p align="center">
  <img src="../imagens/00-fundamentos/banner-infraestrutura.svg" alt="Banner: Infraestrutura de TI" width="100%">
</p>

# 🏗️ O que é Infraestrutura de TI

> [!TIP]
> **Antes de começar:** pense em um sistema que você usa todo dia (o app do banco, o portal da faculdade, o sistema do trabalho). Guarde ele na cabeça, porque vamos voltar nele várias vezes ao longo desta página.

---

## 🤔 Pergunta de aquecimento

Quando você abre o app do seu banco e vê o saldo em 2 segundos, **o que precisou funcionar para isso acontecer?**

<details>
<summary>👀 Clique para ver uma resposta possível</summary>

<br>

Seu celular (hardware) com um sistema operacional (software) se conectou pela internet (rede) até os servidores do banco, que consultaram um banco de dados (armazenamento), tudo protegido por criptografia e autenticação (segurança), monitorado 24h por uma equipe seguindo processos definidos (pessoas e processos).

<p align="center">
  <img src="../imagens/00-fundamentos/fluxo-app-banco.svg" alt="Fluxo: celular, internet, firewall, servidor e banco de dados" width="100%">
</p>

**Tudo isso é infraestrutura de TI.** E você só percebeu que ela existe agora, porque ela funcionou. 😉

</details>

---

## 📖 Definição

Infraestrutura de TI é o conjunto de **componentes físicos, lógicos, humanos e processuais** que permite a uma organização **armazenar, processar, transmitir e proteger** informações.

Ela é a base sobre a qual rodam todos os sistemas e serviços do negócio.

### 🏙️ A analogia da cidade

Imagine que os sistemas da empresa são uma cidade:

<p align="center">
  <img src="../imagens/00-fundamentos/analogia-cidade.svg" alt="Cidade com prédios, ruas, poste, prefeitura, cofre e câmera representando os pilares" width="100%">
</p>

| Na cidade 🏙️ | Na infraestrutura de TI 💻 |
|---|---|
| Terrenos e prédios | Hardware (servidores, data centers) |
| Ruas e avenidas | Redes |
| Rede elétrica e encanamento | Energia, refrigeração, serviços de base |
| Cofres e arquivos da prefeitura | Armazenamento e dados |
| Polícia, portões e câmeras | Segurança da informação |
| Prefeitura, leis e servidores públicos | Pessoas e processos |

> [!NOTE]
> Ninguém elogia o encanamento quando a água sai da torneira. Mas todo mundo reclama quando falta. Infraestrutura é exatamente assim: **invisível quando funciona, óbvia quando falha.**

---

## 🎯 Objetivos da infraestrutura

<p align="center">
  <img src="../imagens/00-fundamentos/objetivos.svg" alt="Ícones dos cinco objetivos" width="100%">
</p>

Marque os objetivos que você já viu falhar na prática (em algum sistema que você usa):

- [ ] **Disponibilidade** — os serviços precisam estar acessíveis quando o usuário precisa.
- [ ] **Desempenho** — responder com velocidade adequada à demanda.
- [ ] **Segurança** — proteger dados e sistemas contra acessos indevidos e falhas.
- [ ] **Escalabilidade** — crescer (ou diminuir) conforme a necessidade do negócio.
- [ ] **Custo controlado** — entregar tudo isso de forma financeiramente sustentável.

<details>
<summary>💡 Exemplos reais de cada falha</summary>

<br>

- **Disponibilidade:** site de ingressos fora do ar no dia da venda de um show.
- **Desempenho:** sistema de matrícula da faculdade travando no primeiro dia.
- **Segurança:** vazamento de dados de clientes de uma empresa.
- **Escalabilidade:** e-commerce que cai na Black Friday porque não aguentou o pico.
- **Custo:** empresa que migra para a nuvem sem planejamento e recebe uma fatura três vezes maior que o previsto.

</details>

---

## ☁️ Modelos de infraestrutura

<p align="center">
  <img src="../imagens/00-fundamentos/modelos-infraestrutura.svg" alt="Comparação visual entre on-premises, cloud e híbrida" width="100%">
</p>

| Modelo | Descrição | ✅ Vantagens | ⚠️ Desvantagens |
|---|---|---|---|
| **🏢 On-premises** | Equipamentos próprios, no local da empresa | Controle total, dados sob posse direta | Alto custo inicial (CAPEX), manutenção própria |
| **☁️ Cloud** | Recursos contratados de um provedor, sob demanda | Escala rápida, paga pelo uso (OPEX) | Dependência do provedor, custos podem crescer sem controle |
| **🔀 Híbrida** | Combinação de on-premises e cloud | Flexibilidade, equilíbrio entre controle e escala | Maior complexidade de gestão e integração |

### 🏠 Pense assim

- **On-premises** = comprar um carro. É seu, você cuida, paga tudo de uma vez e arca com a manutenção.
- **Cloud** = usar aplicativo de transporte. Paga só quando usa, mas depende da empresa e o preço pode subir.
- **Híbrida** = ter um carro para o dia a dia e chamar um app quando precisa de algo diferente.

### 🧩 Desafio rápido

Qual modelo você escolheria para cada caso?

<details>
<summary>1. Uma startup que acabou de nascer e não sabe quantos clientes terá</summary>

<br>

**☁️ Cloud.** Baixo custo inicial e escala conforme o negócio cresce. Não faz sentido comprar servidores sem saber a demanda.

</details>

<details>
<summary>2. Um hospital com dados sensíveis de pacientes e exigências legais rígidas</summary>

<br>

**🏢 On-premises ou 🔀 Híbrida.** Dados críticos ficam sob controle direto, enquanto serviços menos sensíveis (e-mail, site institucional) podem ir para a nuvem.

</details>

<details>
<summary>3. Uma loja que tem movimento normal o ano todo, mas triplica no Natal</summary>

<br>

**🔀 Híbrida.** A base fica on-premises e, nos picos, a loja "estica" para a nuvem. Isso tem até nome: *cloud bursting*.

</details>

---

## 🕰️ Evolução histórica

<p align="center">
  <img src="../imagens/00-fundamentos/evolucao-historica.svg" alt="Linha do tempo: mainframes até containers" width="100%">
</p>


> [!IMPORTANT]
> Repare no padrão: a cada fase, a infraestrutura fica **mais abstrata**. Primeiro você precisava de uma sala inteira para um computador; hoje você cria um servidor com uma linha de código. Esse movimento de abstração vai aparecer em todos os pilares.

---

## 💼 Por que isso importa para o negócio

<p align="center">
  <img src="../imagens/00-fundamentos/impacto-negocio.svg" alt="Infraestrutura mal planejada versus bem planejada" width="100%">
</p>


Infraestrutura **não é só uma questão técnica: é uma decisão estratégica.** Quem decide mal sobre infraestrutura decide mal sobre o negócio.

---

## 📝 Teste seus conhecimentos

Responda mentalmente (ou anote abaixo) antes de abrir as respostas.

<details>
<summary><b>1.</b> Quais são os quatro tipos de componentes que formam a infraestrutura de TI?</summary>

<br>

Físicos, lógicos, humanos e processuais.

</details>

<details>
<summary><b>2.</b> Qual a diferença entre CAPEX e OPEX?</summary>

<br>

**CAPEX** é investimento em bens duráveis (comprar servidores). **OPEX** é despesa operacional recorrente (pagar mensalidade da nuvem).

</details>

<details>
<summary><b>3.</b> Por que dizemos que a infraestrutura é "invisível"?</summary>

<br>

Porque quando funciona bem ninguém percebe; ela só chama atenção quando falha.

</details>

<details>
<summary><b>4.</b> Qual tecnologia dos anos 2000 permitiu rodar vários servidores em um único hardware?</summary>

<br>

A **virtualização**.

</details>

<details>
<summary><b>5.</b> Verdadeiro ou falso: migrar para a nuvem sempre reduz custos.</summary>

<br>

**Falso.** Sem planejamento e controle, os custos na nuvem podem crescer muito. A vantagem da nuvem é flexibilidade, não necessariamente economia.

</details>

---

## ✍️ Minhas anotações

> Volte naquele sistema que você pensou no começo da página. Tente responder:

- **Sistema escolhido:** _______________
- **Qual modelo ele provavelmente usa (on-premises, cloud, híbrido)?** _______________
- **Já vi ele falhar? Em qual objetivo?** _______________
- **Dúvidas que surgiram:** _______________
- **Links úteis que encontrei:** _______________

---

### ✅ Checklist da página

- [ ] Entendi a definição de infraestrutura de TI
- [ ] Consigo explicar a analogia da cidade para outra pessoa
- [ ] Sei diferenciar on-premises, cloud e híbrida
- [ ] Respondi o teste de conhecimentos
- [ ] Preenchi minhas anotações

---

⬅️ [Voltar ao índice](./README.md) · ➡️ [Pilares — visão geral](./pilares-visao-geral.md)
