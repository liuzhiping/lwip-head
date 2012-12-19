Import('RTT_ROOT')
from building import *

src = Split("""
src/api/api_lib.c
src/api/api_msg.c
src/api/err.c
src/api/netbuf.c
src/api/netdb.c
src/api/netifapi.c
src/api/sockets.c
src/api/tcpip.c
src/arch/sys_arch.c
src/core/def.c
src/core/dhcp.c
src/core/dns.c
src/core/inet_chksum.c
src/core/init.c
src/core/memp.c
src/core/netif.c
src/core/pbuf.c
src/core/raw.c
src/core/stats.c
src/core/sys.c
src/core/tcp.c
src/core/tcp_in.c
src/core/tcp_out.c
src/core/timers.c
src/core/udp.c
src/core/ipv4/autoip.c
src/core/ipv4/icmp.c
src/core/ipv4/igmp.c
src/core/ipv4/ip4.c
src/core/ipv4/ip4_addr.c
src/core/ipv4/ip_frag.c
src/core/ipv6/dhcp6.c
src/core/ipv6/ethip6.c
src/core/ipv6/icmp6.c
src/core/ipv6/inet6.c
src/core/ipv6/ip6.c
src/core/ipv6/ip6_addr.c
src/core/ipv6/ip6_frag.c
src/core/ipv6/mld6.c
src/core/ipv6/nd6.c
src/netif/etharp.c
src/netif/ethernetif.c
src/netif/slipif.c
""")

snmp_src = Split("""
src/core/snmp/asn1_dec.c
src/core/snmp/asn1_enc.c
src/core/snmp/mib2.c
src/core/snmp/mib_structs.c
src/core/snmp/msg_in.c
src/core/snmp/msg_out.c
""")

ppp_src = Split("""
src/netif/ppp/auth.c
src/netif/ppp/chap.c
src/netif/ppp/chpms.c
src/netif/ppp/fsm.c
src/netif/ppp/ipcp.c
src/netif/ppp/lcp.c
src/netif/ppp/magic.c
src/netif/ppp/md5.c
src/netif/ppp/pap.c
src/netif/ppp/ppp.c
src/netif/ppp/ppp_oe.c
src/netif/ppp/randm.c
src/netif/ppp/vj.c
""")

# The set of source files associated with this SConscript file.
path = [GetCurrentDir() + '/src',
    GetCurrentDir() + '/src/include',
    GetCurrentDir() + '/src/include/lwip',
    GetCurrentDir() + '/src/include/ipv4',
    GetCurrentDir() + '/src/include/ipv6',
    GetCurrentDir() + '/src/arch/include',
    GetCurrentDir() + '/src/include/netif']

if GetDepend(['RT_LWIP_SNMP']):
    src += snmp_src

if GetDepend(['RT_LWIP_PPP']):
    src += ppp_src
    path += [GetCurrentDir() + '/src/netif/ppp']

# For testing apps
if GetDepend(['RT_USING_NETUTILS']):
    src += Glob('./apps/*.c')

group = DefineGroup('LwIP', src, depend = ['RT_USING_LWIP', 'RT_USING_LWIP_HEAD'], CPPPATH = path)

Return('group')

