# $FreeBSD$

PORTNAME=	cyoi
PORTVERSION=	0.11.3
CATEGORIES=	devel rubygems
MASTER_SITES=	RG

MAINTAINER=	ruby@FreeBSD.org
COMMENT=	Library to prompt for infrastructure and login credentials

LICENSE=	MIT

RUN_DEPENDS=	rubygem-fog>=0:${PORTSDIR}/devel/rubygem-fog \
		rubygem-highline>=1.6:${PORTSDIR}/devel/rubygem-highline \
		rubygem-readwritesettings>=3.0:${PORTSDIR}/devel/rubygem-readwritesettings

NO_ARCH=	yes
USE_RUBY=	yes
USE_RUBYGEMS=	yes
RUBYGEM_AUTOPLIST=	yes

PLIST_FILES=	bin/cyoi

.include <bsd.port.mk>
