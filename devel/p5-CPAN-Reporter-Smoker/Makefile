# Created by: Steve Wills <swills@FreeBSD.org>
# $FreeBSD$

PORTNAME=	CPAN-Reporter-Smoker
PORTVERSION=	0.27
CATEGORIES=	devel perl5
MASTER_SITES=	CPAN
MASTER_SITE_SUBDIR=	CPAN:DAGOLDEN
PKGNAMEPREFIX=	p5-

MAINTAINER=	swills@FreeBSD.org
COMMENT=	Turnkey CPAN Testers smoking

BUILD_DEPENDS=	p5-CPAN-Reporter>0:${PORTSDIR}/devel/p5-CPAN-Reporter \
		p5-Probe-Perl>0:${PORTSDIR}/sysutils/p5-Probe-Perl \
		p5-Test-Reporter>0:${PORTSDIR}/devel/p5-Test-Reporter \
		p5-Term-Title>0:${PORTSDIR}/devel/p5-Term-Title
RUN_DEPENDS:=	${BUILD_DEPENDS}

USES=		perl5
USE_PERL5=	configure

.include <bsd.port.mk>
