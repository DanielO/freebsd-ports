# Created by: Lucio Costa <lucio@zetasolucoes.com.br>
# $FreeBSD$

PORTNAME=	ezradius
PORTVERSION=	0.2.1.2
PORTREVISION=	1
CATEGORIES=	net-mgmt
MASTER_SITES=	SF/${PORTNAME}/${PORTNAME}/${PORTNAME}-0.2.1stable
DISTNAME=	${PORTNAME}-${PORTVERSION}stable

MAINTAINER=	ports@FreeBSD.org
COMMENT=	EzRADIUS is FreeRADIUS and Chillispot web-based management software

LICENSE=	GPLv2

RUN_DEPENDS=	radiusd:${PORTSDIR}/net/freeradius2

WRKSRC=		${WRKDIR}/${PORTNAME}-intl
NO_BUILD=	yes
USE_MYSQL=	yes
USE_PHP=	mysql session xml
WANT_PHP_WEB=	yes

do-install:
	@${MKDIR} ${STAGEDIR}${WWWDIR}
	@cd ${WRKSRC} && \
	${FIND} . -type d -exec ${MKDIR} ${STAGEDIR}${WWWDIR}/{} \; \
		-exec ${CHOWN} ${WWWOWN}:${WWWGRP} ${STAGEDIR}${WWWDIR}/{} \;
	@cd ${WRKSRC} && \
	${FIND} . \! -type d -exec ${INSTALL_DATA} {} ${STAGEDIR}${WWWDIR}/{} \; \
		-exec ${CHOWN} ${WWWOWN}:${WWWGRP} ${STAGEDIR}${WWWDIR}/{} \;

.include <bsd.port.mk>
