# $FreeBSD$

PORTNAME=	chromaprint
PORTVERSION=	1.1
CATEGORIES=	audio
MASTER_SITES=	http://bitbucket.org/acoustid/${PORTNAME}/downloads/

MAINTAINER=	jhale@FreeBSD.org
COMMENT=	AcoustID audio fingerprinting library

LICENSE=	LGPL21

LIB_DEPENDS=	libavcodec.so:${PORTSDIR}/multimedia/ffmpeg

USES=		cmake:outsource
USE_LDCONFIG=	yes

CMAKE_ARGS=	-DBUILD_EXAMPLES:BOOL=ON \
		-DWITH_AVFFT:BOOL=ON \

post-patch:
	${REINPLACE_CMD} -e '/pkgconfig/s|$${LIB_INSTALL_DIR}|libdata|' \
		 ${WRKSRC}/CMakeLists.txt

.include <bsd.port.mk>
