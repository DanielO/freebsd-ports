# $FreeBSD$

PORTNAME=	libbobcat
PORTVERSION=	3.25.01
CATEGORIES=	devel
MASTER_SITES=	SF/bobcat/bobcat/${PORTVERSION}
DISTNAME=	bobcat_${PORTVERSION}
EXTRACT_SUFX=	.orig.tar.gz

MAINTAINER=	bofh@FreeBSD.org
COMMENT=	Brokken's Own Base Classes And Templates

LICENSE=	GPLv3

BUILD_DEPENDS=	icmake:${PORTSDIR}/devel/icmake \
		yodl>=3.0:${PORTSDIR}/textproc/yodl

USE_GCC=	4.9+
USE_XORG=	x11

DOCSDIR=	${PREFIX}/share/doc/${PORTNAME}-${PORTVERSION}
PORTDOCS=	*

PLIST_SUB+=	PORTVERSION="${PORTVERSION}"

USE_LDCONFIG=	yes
WRKSRC=		${WRKDIR}/bobcat-${PORTVERSION}

USES=		readline shebangfix

SHEBANG_LANG=	icmake
icmake_OLD_CMD=	/usr/bin/icmake
icmake_CMD=	${LOCALBASE}/bin/icmake

SHEBANG_FILES=	build \
		documentation/examples/sockets/client/build \
		documentation/examples/sockets/client2/build \
		documentation/examples/sockets/forkserver/build \
		documentation/examples/sockets/forkserver2/build \
		documentation/examples/sockets/server/build

OPTIONS_DEFINE=	DOCS

.include <bsd.port.options.mk>

post-patch:
	${REINPLACE_CMD} -e 's|"/usr"|"${PREFIX}"| ; \
		s|"/share/doc/libbobcat3"|"/share/doc/${PORTNAME}-${PORTVERSION}"| ; \
		s|"/share/doc/libbobcat3-dev"|"/share/doc/${PORTNAME}-${PORTVERSION}/dev"| ; \
		s|"/share/man"|"/man"| ; \
		s|"-d"|"-Pp"| ; \
		s|#define MANHTML|| ; \
		s|g++|${CXX}| ; \
		s|Wall|Wall -D_GLIBCXX_USE_C99| ; \
		s|gcc|${CC}|' \
		${WRKSRC}/INSTALL.im
	@${REINPLACE_CMD} -e 's|"cp -r |"cp -R |' \
		${WRKSRC}/icmake/install
	@${REINPLACE_CMD} -e 's|-lssl|-lssl -L${LOCALBASE}/lib| ; \
		s|-lX11|-lX11 -L${LOCALBASE}/lib| ; \
		s|-lmilter|-lmilter -lpthread|' \
		${WRKSRC}/icmake/special
.if ! ${PORT_OPTIONS:MDOCS}
	@${REINPLACE_CMD} -e 's|#define DOCOTHER||' \
		${WRKSRC}/INSTALL.im
.endif

do-build:
	@cd ${WRKSRC} && ./build libraries all strip && ./build man

do-install:
	@cd ${WRKSRC} && ./build install ${STAGEDIR} ${STAGEDIR}

.include <bsd.port.mk>
