# $FreeBSD$

PORTNAME=	etcd
PORTVERSION=	0.4.6
DISTVERSIONPREFIX=	v
CATEGORIES=	devel
PKGNAMEPREFIX=	coreos-

MAINTAINER=	robak@FreeBSD.org
COMMENT=	Highly-available key value store and service discovery

LICENSE=	APACHE20

BUILD_DEPENDS=	${LOCALBASE}/bin/go:${PORTSDIR}/lang/go

USE_GITHUB=	yes
GH_ACCOUNT=	coreos

PLIST_FILES=	bin/bench \
		bin/etcd

PORTDOCS=	README.md

OPTIONS_DEFINE=	DOCS
DOCS_DESC=	Install etcd README file

.include <bsd.port.options.mk>

post-patch:
	@${REINPLACE_CMD} -e 's|$$VER|${DISTVERSION}|' ${WRKSRC}/scripts/release-version
	@${REINPLACE_CMD} -e '/VER=/d' ${WRKSRC}/scripts/release-version

do-build:
	cd ${WRKSRC}; ${SH} build

do-install:
.if ${PORT_OPTIONS:MDOCS}
	${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/${PORTDOCS} ${STAGEDIR}${DOCSDIR}
.endif
	${INSTALL_PROGRAM} ${WRKSRC}/bin/bench ${STAGEDIR}${PREFIX}/bin/
	${INSTALL_PROGRAM} ${WRKSRC}/bin/etcd ${STAGEDIR}${PREFIX}/bin/

.include <bsd.port.mk>
