Zabbix + Grafana Synthetic Internet Monitoring

Monitoramento sintético de serviços da Internet usando Zabbix + Grafana, com visualização por categoria, baseline individual e fallback TCP/443 para destinos que não respondem ICMP.

A proposta é ter uma visão operacional rápida da experiência de acesso a serviços conhecidos sem precisar criar um host separado para cada destino.

Visão geral

60 serviços monitorados

7 categorias: Financeiro, Streaming, Jogos, Redes Sociais, Varejo, Cloud e DNS Público

196 itens no Zabbix

60 × ICMP Ping

60 × ICMP Loss

60 × ICMP Response Time

8 × TCP/443 Availability

8 × TCP/443 Response Time

Fallback TCP/443 para serviços que não respondem ICMP

Baseline individual por serviço

Filtros por categoria, estado e serviço

Indicadores de disponibilidade, perda, instabilidade e desvio da baseline

Arquivos

Synthetic_Monitoring_Internet_Services_Zabbix_6.4_PUBLIC.yaml
Export sanitizado do host para Zabbix 6.4.

Internet_Experience_Synthetic_Monitoring_Grafana_PUBLIC.json
Dashboard sanitizado e portátil para Grafana.

Requisitos

Zabbix 6.4

Grafana 9.x ou versão compatível

Plugin Grafana-Zabbix

Plugin Business Charts / Apache ECharts (Volkov Labs)

Como importar

1. Zabbix

Importe o arquivo:

Synthetic_Monitoring_Internet_Services_Zabbix_6.4_PUBLIC.yaml

O export cria:

Grupo: Synthetic Monitoring
Host:  Synthetic Monitoring - Internet Services

Depois da importação, valide em Dados recentes / Latest data se os itens estão coletando.

Os Simple Checks são executados pelo Zabbix Server quando o host não está associado a um proxy.
Se quiser medir a experiência a partir de uma região, POP ou saída específica, associe o host ao proxy correspondente.

2. Grafana

Importe o arquivo:

Internet_Experience_Synthetic_Monitoring_Grafana_PUBLIC.json

Durante a importação, selecione o datasource Zabbix do seu ambiente.

O JSON público não contém:

UID do datasource original

Item IDs do ambiente original

nomes internos da empresa

referências ao grupo/host interno original

As queries usam o host e grupo públicos criados pelo YAML para facilitar a reutilização.

ICMP x TCP/443

Nem todos os serviços respondem ICMP.

Nesses casos, o projeto utiliza:

net.tcp.service[tcp,<destino>,443]
net.tcp.service.perf[tcp,<destino>,443]

como fallback.

Importante:

ICMP Response Time mede RTT de ping.

TCP 443 Response Time mede o tempo para estabelecer a conexão TCP na porta 443.

Essas duas métricas não devem ser comparadas diretamente como se fossem iguais.

O dashboard utiliza a baseline do próprio serviço para identificar desvios do comportamento habitual.

Segurança

Os arquivos deste repositório foram sanitizados antes da publicação.

Foram removidos:

credenciais

proxies internos

UID do datasource original

Item IDs do ambiente original

nomes e grupos internos da empresa

Mesmo assim, revise qualquer export antes de importar em um ambiente de produção.

Créditos

Projeto adaptado e publicado por Mike Vieira.

A ideia inicial surgiu em uma conversa com William Bruno, que compartilhou uma referência de monitoramento utilizada no ambiente dele.

🔗 LinkedIn — Mike Vieira
