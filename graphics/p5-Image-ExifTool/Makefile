# Created by: Tod McQuillin <devin@spamcop.net>
# $FreeBSD$

PORTNAME=	Image-ExifTool
PORTVERSION=	9.90
CATEGORIES=	graphics perl5
MASTER_SITES=	http://www.sno.phy.queensu.ca/~phil/exiftool/ \
		CPAN
MASTER_SITE_SUBDIR=	CPAN:EXIFTOOL
PKGNAMEPREFIX=	p5-

MAINTAINER=	devin@spamcop.net
COMMENT=	Perl module for getting EXIF data from image files

LICENSE=	ART10 GPLv1
LICENSE_COMB=	dual

CONFLICTS=	p5-Image-ExifTool-devel-[0-9]*

USES=		perl5
USE_PERL5=	configure

PORTDOCS=	*

DOCSRCDIR1=	${WRKSRC}
DOC_FILES1=	Changes README

DOCSRCDIR2=	${DOCSRCDIR1}/html
DOCSDIR2=	${DOCSDIR}/html
DOC_FILES2=	*.css *.html *.pdf

DOCSRCDIR3=	${DOCSRCDIR2}/TagNames
DOCSDIR3=	${DOCSDIR2}/TagNames
DOC_FILES3=	*.css *.html

OPTIONS_DEFINE=	DOCS

post-install:
	@${MKDIR} ${STAGEDIR}${DOCSDIR3}
	${INSTALL_DATA} ${DOC_FILES1:S|^|${DOCSRCDIR1}/|} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${DOC_FILES2:S|^|${DOCSRCDIR2}/|} ${STAGEDIR}${DOCSDIR2}
	${INSTALL_DATA} ${DOC_FILES3:S|^|${DOCSRCDIR3}/|} ${STAGEDIR}${DOCSDIR3}

.include <bsd.port.mk>
