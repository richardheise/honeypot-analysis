# Análise de Tráfego de Rede de um Honeypot

Este repositório contém os artefatos e a análise de um ataque de rede capturado em um honeypot. O objetivo deste trabalho é dissecar o tráfego de rede para entender as ações do atacante.

## Estrutura do Repositório

*   `attack-trace.pcap`: Arquivo de captura de pacotes (packet capture) contendo todo o tráfego de rede relacionado ao ataque. Este é o arquivo principal para a análise.
*   `Perguntas.txt`: Uma lista de perguntas que guiaram a investigação sobre o ataque.
*   `saida.txt`: As respostas para as perguntas, incluindo os comandos utilizados e os resultados obtidos durante a análise. Este arquivo serve como um relatório da investigação.
*   `098.114.205.102.08884-192.150.011.111.36296` e `192.150.011.111.36296-098.114.205.102.08884`: Diretórios que provavelmente contêm os fluxos TCP extraídos da captura de pacotes, separados por origem e destino.

## Como Entender o Trabalho

1.  **Comece pelas Perguntas:** Leia o arquivo `Perguntas.txt` para entender quais informações estavam sendo buscadas na análise.
2.  **Siga as Respostas:** O arquivo `saida.txt` detalha o processo de análise. Ele mostra quais ferramentas (como `tcpdump`, `whois`, `tshark`, `snort`) foram usadas para inspecionar o arquivo `.pcap` e responder a cada pergunta.
3.  **Inspecione a Captura:** Para uma análise mais profunda ou para verificar os resultados, você pode usar ferramentas como o Wireshark ou o `tcpdump` para abrir e examinar o arquivo `attack-trace.pcap`.

## Resumo do Ataque

A análise em `saida.txt` revela os seguintes pontos principais sobre o ataque:

*   **IPs Envolvidos:**
    *   **Atacante:** `98.114.205.102`
    *   **Honeypot (Vítima):** `192.150.11.111`
*   **Alvo:** O ataque foi direcionado a um serviço SMB (porta 445) em um sistema operacional Windows XP.
*   **Vulnerabilidade:** A vulnerabilidade explorada foi a **MS04-11**, relacionada ao serviço LSASS.
*   **Ações do Atacante:** O atacante explorou a vulnerabilidade para executar um shellcode na máquina vítima. Os comandos no payload indicam tentativas de baixar e executar um arquivo malicioso (`ssms.exe`).

Este repositório serve como um estudo de caso prático sobre como analisar um ataque de rede a partir de uma captura de pacotes.
