# $FreeBSD$

PORTNAME=	django-assets
PORTVERSION=	0.10
PORTREVISION=	1
CATEGORIES=	www python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	wg@FreeBSD.org
COMMENT=	Compress and merge CSS and Javascript files

LICENSE=	BSD2CLAUSE

RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}django>0:${PORTSDIR}/www/py-django \
		${PYTHON_PKGNAMEPREFIX}webassets>0:${PORTSDIR}/www/py-webassets

USES=		python
USE_PYTHON=	autoplist distutils

.include <bsd.port.mk>
