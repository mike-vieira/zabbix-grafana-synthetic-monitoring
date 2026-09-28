# MikroTik Zabbix Dashboard Overlay

Template público e sanitizado para **Zabbix 6.4**, voltado ao monitoramento de equipamentos **MikroTik RouterOS** via SNMP, com foco em uma visão operacional rápida para troubleshooting.

O projeto nasceu de uma necessidade prática: reunir em um único template os principais sinais para análise de CPE/roteadores MikroTik sem substituir templates já existentes no host.

## O que o template monitora

- Status ICMP do equipamento
- Latência ICMP
- Perda de pacotes
- CPU
- Memória total, usada e percentual
- Nome e descrição do sistema
- Uptime
- Descoberta automática de interfaces via SNMP LLD
- Tráfego RX/TX por interface
- Estado operacional das interfaces
- Erros RX/TX
- Descartes RX/TX

## Dashboard incluído

O template inclui o dashboard **MikroTik | Cockpit**, organizado em três páginas:

1. **Cockpit**
   - Status do CPE
   - Latência
   - Perda
   - CPU
   - Memória
   - Equipamento
   - Sistema/modelo
   - Uptime
   - Gráficos de conectividade e recursos

2. **Interfaces**
   - Tráfego RX/TX por interface
   - Estado operacional

3. **Qualidade**
   - Erros RX/TX
   - Descartes RX/TX

## Características

- Zabbix export version: **6.4**
- Coleta SNMP usando **HOST-RESOURCES-MIB** e **IF-MIB**
- Compatível com hosts que já possuem outro template vinculado
- Chaves próprias com prefixo `mk.overlay.*`
- Não cria triggers
- Foco em visualização e troubleshooting N1/N2
- Utiliza Simple Checks ICMP com `{HOST.CONN}`
- Descoberta de interfaces executada a cada 1 hora
- Histórico principal de 7 dias e trends de 30 dias

## Requisitos

- Zabbix 6.4
- Equipamento MikroTik RouterOS com SNMP habilitado
- Interface SNMP configurada no host Zabbix
- HOST-RESOURCES-MIB e IF-MIB expostas pelo equipamento

## Como importar

No Zabbix:

1. Acesse **Data collection > Templates**.
2. Clique em **Import**.
3. Selecione `zabbix_mikrotik_dashboard_overlay_v8.yaml`.
4. Revise as opções de importação e confirme.
5. Vincule o template **MikroTik Dashboard Overlay** ao host desejado.
6. Confirme que o host possui uma interface SNMP válida.
7. Valide os itens em **Monitoring > Latest data**.
8. Abra o dashboard do template para visualizar o cockpit.

## Uso como overlay

A proposta é usar este template como uma camada adicional de monitoramento.

Você pode manter o template MikroTik já utilizado no seu ambiente e vincular este overlay ao mesmo host. As chaves foram separadas em `mk.overlay.*` para reduzir o risco de colisão com outros templates.

## Observações de compatibilidade

Alguns índices da HOST-RESOURCES-MIB podem variar entre modelos ou versões do RouterOS. Se CPU ou memória aparecerem como não suportados, valide os OIDs disponíveis no equipamento antes de alterar o template.

A descoberta e as métricas de interfaces usam IF-MIB e dependem do suporte SNMP do dispositivo.

## Segurança e sanitização

Esta versão foi preparada especificamente para publicação.

Foram verificados e removidos/evitados:

- nomes de clientes;
- nomes internos de empresa;
- endereços IP de clientes/ambiente;
- URLs internas;
- usuários;
- senhas;
- tokens;
- SNMP communities;
- outras credenciais ou identificadores operacionais.

Os números semelhantes a endereços presentes no YAML correspondem a **OIDs SNMP**, não a endereços IP de clientes.

Mesmo assim, revise qualquer template antes de importar ou publicar alterações feitas em um ambiente real.

## Arquivos

- `zabbix_mikrotik_dashboard_overlay_v8.yaml` — template público para importação.
- `CHANGELOG.md` — histórico da versão pública.
- `SECURITY.md` — orientações para manter futuras versões sanitizadas.
- `LICENSE` — licença MIT.

## Licença

MIT License.

Você pode usar, adaptar e redistribuir o projeto conforme os termos da licença.

## Autor

**Mike Vieira**

Projeto desenvolvido a partir de necessidades reais de monitoramento e troubleshooting de redes, com publicação sanitizada para estudo e reutilização pela comunidade.
