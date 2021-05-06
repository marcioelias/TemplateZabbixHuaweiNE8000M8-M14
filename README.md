# TemplateZabbixHuaweiNE8000M8-M14

Template de monitoramento do Huawei NE8000 M8-M14 (testado em um M8)
Desenvolvido na versão 4.4.3 do Zabbix, devendo funcionar em versões futuras.

**SNMP V2C**

**Dependencias**

- MIBS
  - HUAWEI-AAA-MIB
  - HUAWEI-IPPOOL-MIB
  - HUAWEI-BRAS-SRVCFG-INTERFACE-MIB

- Template
  - Template SNMP Generic (default do Zabbix para coleta de informações genéricas sobre hosts monitorados via SNMP)

Link para download das MIB's: https://support.huawei.com/enterprise/en/routers/netengine-8000-m8-pid-250517142?category=reference-guides&subcategory=mib-reference

**Items do Template**

- Total PPPoE Online Num
- Total IPv6 Online Num
- Total Dual-Stack Online Num
- Itens herdados do template SNMP Generic

**Regras de Descoberta**

- IP-Pool-Group Discovery
  - Protótipos de Item
    - IP-Pool-Group NOME-DO-POOL-GROUP Total IP Num
    - IP-Pool-Group NOME-DO-POOL-GROUP Total IP Used
    - IP-Pool-Group NOME-DO-POOL-GROUP Total IP Free
    - IP-Pool-Group NOME-DO-POOL-GROUP Total IP Conflited
    - IP-Pool-Group NOME-DO-POOL-GROUP Percent Usage
  - Protótipos de Trigger (ativadas se {$IP_POOL_GROUP_TRIGGER_USAGE} = 1) 
    - Endereços IPv4 ESGOTADOS em NOME-DO-POOL-GROUP
    - Uso de Endereços IPv4 em NOME-DO-POOL-GROUP está acima de {$IP_POOL_USAGE_THRESHOLD}%
  - Protótipo de Gráfico
    - IP-Pool-Group NOME-DO-POOL-GROUP Usage Statistics
- IP-Pool Discovery
 - Protótipos de Item
    - IP-Pool NOME-DO-POOL Total IP Num
    - IP-Pool NOME-DO-POOL Total IP Used
    - IP-Pool NOME-DO-POOL Total IP Idle
    - IP-Pool NOME-DO-POOL Total IP Conflited
    - IP-Pool NOME-DO-POOL Percent Usage
  - Protótipos de Trigger (ativadas se {$IP_POOL_TRIGGER_USAGE} = 1) 
    - Endereços IPv4 ESGOTADOS em NOME-DO-POOL (Severidade Desastre)
    - Uso de Endereços IPv4 em NOME-DO-POOL está acima de {$IP_POOL_USAGE_THRESHOLD}% (Severidade Alta)
  - Protótipo de Gráfico
    - IP-Pool-Group NOME-DO-POOL Usage Statistics
- IPU Discovery
  - Protótipos de Item
    - IPU SLOT NUM-SLOT Administrative Status
    - IPU SLOT NUM-SLOT CPU Usage
    - IPU SLOT NUM-SLOT CPU Usage (1 min)
    - IPU SLOT NUM-SLOT CPU Usage (5 min)
    - IPU SLOT NUM-SLOT Description
    - IPU SLOT NUM-SLOT Free Memory
    - IPU SLOT NUM-SLOT Operational Status
    - IPU SLOT NUM-SLOT Percent Memory Used
    - IPU SLOT NUM-SLOT Total Memory
  - Protótipos de Trigger
    - IPU SLOT NUM-SLOT uso de CPU acima de 80% (Severidade Média)
    - IPU SLOT NUM-SLOT uso de CPU acima de 90% (Severidade Alta)
    - IPU SLOT NUM-SLOT uso de Memória acima de 80% (Severidade Média)
    - IPU SLOT NUM-SLOT uso de Memória acima de 90% (Severidade Alta)
  - Protótipos de Gráficos
    - IPU SLOT NUM-SLOT CPU Usage
    -	IPU SLOT NUM-SLOT Memory Usage
- PPPoE Access-User Interface Discovery
  - Protótipos de Item
    - PPPoE Access-User Inferface S-VLAN.C-VLAN
  - Protótipos de Grafico
    - PPPoE Connections Interface S-VLAN.C-VLAN

**Macros**

- {$IP_POOL_GROUP_TRIGGER_USAGE}
- {$IP_POOL_TRIGGER_USAGE}
- {$IP_POOL_USAGE_THRESHOLD}
- {$SNMP_COMMUNITY} (padrão)
