# Created by: Riaan Kruger <riaank@gmail.com>
# $FreeBSD$

PORTNAME=	strongswan
PORTVERSION=	5.3.2
CATEGORIES=	security
MASTER_SITES=	http://download.strongswan.org/ \
		http://download2.strongswan.org/

MAINTAINER=	strongswan@nanoteq.com
COMMENT=	Open Source IKEv2 IPsec-based VPN solution

LICENSE=	GPLv2

USES=		cpe execinfo libtool:keepla tar:bzip2 pkgconfig
USE_OPENSSL=	yes
USE_RC_SUBR=	strongswan
GNU_CONFIGURE=	yes
USE_LDCONFIG=	yes
INSTALL_TARGET=	install-strip

CONFIGURE_ARGS=	--enable-kernel-pfkey \
		--enable-kernel-pfroute  \
		--disable-kernel-netlink  \
		--disable-scripts  \
		--disable-gmp \
		--enable-openssl \
		--enable-eap-identity \
		--enable-eap-md5 \
		--enable-eap-tls \
		--enable-eap-mschapv2 \
		--enable-eap-peap \
		--enable-eap-ttls \
		--enable-md4 \
		--enable-blowfish \
		--enable-addrblock \
		--enable-whitelist \
		--enable-cmd \
		--with-group=wheel  \
		--with-lib-prefix=${PREFIX}

OPTIONS_DEFINE=	CURL EAPAKA3GPP2 EAPDYNAMIC EAPRADIUS EAPSIMFILE GCM IKEv1 \
		IPSECKEY KERNELLIBIPSEC LOADTESTER LDAP MYSQL PKI SCEP SMP \
		SQLITE TESTVECTOR UNBOUND UNITY XAUTH
OPTIONS_DEFAULT=	IKEv1
OPTIONS_SUB=	yes
CURL_DESC=	Enable CURL to fetch CRL/OCSP
EAPAKA3GPP2_DESC=	Enable EAP AKA with 3gpp2 backend
EAPDYNAMIC_DESC=	Enable EAP dynamic proxy module
EAPRADIUS_DESC=		Enable EAP Radius proxy authentication
EAPSIMFILE_DESC=	Enable EAP SIM with file backend
GCM_DESC=		Enable GCM AEAD wrapper crypto plugin
IKEv1_DESC=	Enable IKEv1 support
IPSECKEY_DESC=	Enable authentication with IPSECKEY resource records with DNSSEC
KERNELLIBIPSEC_DESC=	Enable IPSec userland backend
LOADTESTER_DESC=	Enable load testing plugin
TESTVECTOR_DESC=	Enable crypto test vectors
PKI_DESC=	Enable PKI tools
SCEP_DESC=	Enable Simple Certificate Enrollment Protocol
SMP_DESC=	Enable XML-based management protocol
UNBOUND_DESC=	Enable DNSSEC-enabled resolver
UNITY_DESC=	Enable Cisco Unity extension plugin
XAUTH_DESC=	Enable XAuth password verification

# Extra options
CURL_CONFIGURE_ON=	--enable-curl
CURL_LIB_DEPENDS=	libcurl.so:${PORTSDIR}/ftp/curl
EAPAKA3GPP2_CONFIGURE_ON=	--enable-eap-aka --enable-eap-aka-3gpp2
EAPAKA3GPP2_LIB_DEPENDS=libgmp.so:${PORTSDIR}/math/gmp
EAPDYNAMIC_CONFIGURE_ON=--enable-eap-dynamic
EAPRADIUS_CONFIGURE_ON=	--enable-eap-radius
EAPSIMFILE_CONFIGURE_ON=--enable-eap-sim --enable-eap-sim-file
GCM_CONFIGURE_ON=	--enable-gcm
IKEv1_CONFIGURE_OFF=	--disable-ikev1
IPSECKEY_CONFIGURE_ON=	--enable-ipseckey
KERNELLIBIPSEC_CONFIGURE_ON=	--enable-kernel-libipsec
LOADTESTER_CONFIGURE_ON=--enable-load-tester
LDAP_CONFIGURE_ON=	--enable-ldap
LDAP_USE=		OPENLDAP=yes
MYSQL_CONFIGURE_ON=	--enable-mysql
MYSQL_USE=		MYSQL=yes
SMP_LIB_DEPENDS=	libxml2.so:${PORTSDIR}/textproc/libxml2
SMP_CONFIGURE_ON=	--enable-smp
SQLITE_CONFIGURE_ON=	--enable-sqlite
SQLITE_LIB_DEPENDS=	libsqlite3.so:${PORTSDIR}/databases/sqlite3
TESTVECTOR_CONFIGURE_ON=--enable-test-vectors
PKI_CONFIGURE_OFF=	--disable-pki
SCEP_CONFIGURE_OFF=	--disable-scepclient
UNBOUND_CONFIGURE_ON=	--enable-unbound
UNBOUND_LIB_DEPENDS=	libunbound.so:${PORTSDIR}/dns/unbound
UNITY_CONFIGURE_ON=	--enable-unity
XAUTH_CONFIGURE_ON=	--enable-xauth-eap --enable-xauth-generic

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MEAPSIMFILE} || ${PORT_OPTIONS:MEAPAKA3GPP2}
PLIST_SUB+=	SIMAKA=""
.else
PLIST_SUB+=	SIMAKA="@comment "
.endif

.if ${PORT_OPTIONS:MMYSQL} || ${PORT_OPTIONS:MSQLITE}
CONFIGURE_ARGS+=	--enable-attr-sql --enable-sql
PLIST_SUB+=	SQL=""
.else
PLIST_SUB+=	SQL="@comment "
.endif

.if ${PORT_OPTIONS:MIKEv1} || ${PORT_OPTIONS:MXAUTH}
PLIST_SUB+=	XAUTHGEN=""
.else
PLIST_SUB+=	XAUTHGEN="@comment "
.endif

.include <bsd.port.mk>
