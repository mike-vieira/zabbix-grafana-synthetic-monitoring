# Changelog

## v8.0-public — 2026-09-28

Primeira publicação sanitizada do MikroTik Zabbix Dashboard Overlay.

### Incluído

- Cockpit com status, latência, perda, CPU, memória, identificação do sistema e uptime.
- Descoberta automática de interfaces via SNMP.
- Gráficos de RX/TX por interface.
- Estado operacional das interfaces.
- Gráficos de erros e descartes RX/TX.
- Chaves públicas isoladas sob `mk.overlay.*`.
- Nomenclatura interna removida.
- Revisão para remoção de credenciais, IPs, URLs e identificadores de clientes.

### Observação

A versão pública não cria triggers. O foco é visualização e troubleshooting.
