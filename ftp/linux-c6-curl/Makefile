# Created by: Artyom Mirgorodskiy <artyom.mirgorodsky@gmail.com>
# $FreeBSD$

PORTNAME=	curl
PORTVERSION=	7.19.7
PORTREVISION=	2
CATEGORIES=	ftp linux
DISTFILES=	curl-${PORTVERSION}-${RPMVERSION}.${LINUX_RPM_ARCH}.rpm \
		libcurl-${PORTVERSION}-${RPMVERSION}.${LINUX_RPM_ARCH}.rpm
MASTER_SITES=	CENTOS_LINUX_UPDATES

MAINTAINER=	emulation@FreeBSD.org
COMMENT=	Command line tool for transferring files with URL syntax (Linux CentOS ${LINUX_DIST_VER})

CONFLICTS=	linux-curl-[0-9]* linux-f10-curl-[0-9]*

ONLY_FOR_ARCHS=	i386 amd64

USE_LINUX=	c6
USE_LINUX_APPS=	openldap libssh2 # cyrus-sasl2
USE_LINUX_RPM=	yes
RPMVERSION=	40.el6_6.4
BRANDELF_FILES=	usr/bin/curl
USE_LDCONFIG=	yes

PLIST_FILES=	usr/bin/curl usr/lib/libcurl.so.4 usr/lib/libcurl.so.4.1.1 \
		usr/share/man/man1/curl.1.gz
DOCSDIR=	usr/share/doc/${PORTNAME}-${PORTVERSION}
PORTDOCS=	BUGS COPYING FEATURES README TODO CHANGES FAQ MANUAL RESOURCES TheArtOfHttpScripting
DESCR=	${.CURDIR}/../${PORTNAME}/pkg-descr

.include <bsd.port.mk>
