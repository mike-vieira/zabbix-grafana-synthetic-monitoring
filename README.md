# Zabbix Monitoring Projects

Repositório público com projetos de monitoramento desenvolvidos e sanitizados para estudo, reutilização e adaptação pela comunidade.

## Projetos

### 1. MikroTik Zabbix Dashboard Overlay

Template para **Zabbix 6.4** focado em MikroTik RouterOS via SNMP, com cockpit operacional e páginas dedicadas a interfaces e qualidade.

**Principais recursos:**
- status ICMP, latência e perda;
- CPU, memória e uptime;
- descoberta automática de interfaces;
- tráfego RX/TX;
- estado operacional;
- erros e descartes RX/TX.

➡️ [Abrir MikroTik Zabbix Dashboard Overlay](./projects/mikrotik-zabbix-dashboard-overlay/)

---

### 2. Zabbix + Grafana Synthetic Internet Monitoring

Monitoramento sintético de serviços da Internet com **Zabbix + Grafana**, baseline individual, filtros por categoria e fallback TCP/443 para serviços que não respondem ICMP.

**Principais recursos:**
- 60 serviços monitorados;
- 7 categorias;
- ICMP Ping, Loss e Response Time;
- fallback TCP/443;
- dashboard Grafana sanitizado;
- indicadores de disponibilidade, perda, instabilidade e desvio da baseline.

➡️ [Abrir Synthetic Internet Monitoring](./projects/synthetic-internet-monitoring/)

## Segurança

Os projetos públicos deste repositório são preparados para compartilhamento externo. Exports originados de ambientes reais são revisados para remover credenciais, identificadores internos e referências operacionais antes da publicação.

## Autor

**Mike Vieira**

Projetos voltados a monitoramento, troubleshooting e observabilidade de redes.
