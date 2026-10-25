# Segurança em Redes Wi-Fi (WPA2)

Projeto prático desenvolvido no âmbito da unidade curricular de Segurança da Licenciatura em Engenharia Informática (Ramo de Redes e Administração de Sistemas) do ISEC.

## Visão Geral do Projeto
O projeto teve como principal objetivo estudar os mecanismos de segurança e as fragilidades associadas ao protocolo WPA2-PSK. A componente prática consistiu na execução de um cenário controlado de auditoria de segurança (pentest), focando-se na interceção do processo de autenticação inicial e na realização de um ataque de dicionário offline para recuperação da palavra-passe.

## Metodologia e Fases do Estudo
1. **Fundamentação Teórica:** Estudo aprofundado do protocolo WPA2, transição do TKIP para o CCMP (com cifra AES) e análise detalhada das quatro mensagens trocadas durante o processo de 4-Way Handshake.
2. **Ambiente de Testes:** Configuração de um laboratório isolado utilizando um Ponto de Acessos (AP), uma estação cliente legítima e uma máquina virtual Kali Linux equipada com uma placa Wi-Fi com suporte para Monitor Mode e injeção de pacotes (chipset RTL8821AU).
3. **Monitorização e Captura:** 
   * Ativação do modo monitor na interface (`wlan0`).
   * Utilização do `airodump-ng` para reconhecimento da rede alvo e direcionamento da captura de tráfego.
   * Execução de um ataque de desautenticação com o `aireplay-ng` para forçar a reautenticação do cliente e capturar o *4-Way Handshake* num ficheiro `.cap`.
4. **Validação:** Inspeção e isolamento do tráfego EAPOL no Wireshark para confirmar a integridade e a validade das mensagens capturadas.
5. **Ataque de Dicionário (Offline):** Utilização da ferramenta `aircrack-ng` em conjunto com a *wordlist* global `RockYou.txt` para testar chaves candidatas a partir do *handshake* obtido.

## Resultados Principais
* O ataque de dicionário *offline* demonstrou alta eficácia quando aplicados padrões de credenciais vulneráveis. 
* A palavra-passe da rede em estudo (`chocolate`) foi recuperada com sucesso em apenas 1 segundo, após testar 5979 chaves candidatas.
<p align="center">
  <img alt="key-found" src="https://github.com/user-attachments/assets/a09bc9e9-70f6-454d-b876-9d7f64bac0fc" />
</p>
* O estudo comprovou que, embora o WPA2 utilize cifras robustas como o AES-CCMP, a segurança da rede fica severamente comprometida se o utilizador optar por palavras-passe fracas ou presentes em listas públicas de fugas de informação.

## Conteúdo do Repositório
* [`relatorio/`](relatorio/) - Relatório técnico completo do projeto em formato PDF (`.pdf`).
* [`recursos/`](recursos/) - Ficheiros e recursos de suporte utilizados durante a demonstração experimental.
