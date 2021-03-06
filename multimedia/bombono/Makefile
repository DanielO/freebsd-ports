# Created by: Stas Timokhin <stast@bsdportal.ru>
# $FreeBSD$

PORTNAME=	bombono
PORTVERSION=	1.2.2
PORTREVISION=	6
CATEGORIES=	multimedia
MASTER_SITES=	SF/${PORTNAME}/${PORTNAME}-dvd/${PORTVERSION:R}
DISTNAME=	${PORTNAME}-dvd-${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	DVD authoring program

BUILD_DEPENDS=	gm:${PORTSDIR}/graphics/GraphicsMagick
LIB_DEPENDS=	libgtkmm-2.4.so:${PORTSDIR}/x11-toolkits/gtkmm24 \
		libxml++-2.6.so:${PORTSDIR}/textproc/libxml++26 \
		liblavfile.so:${PORTSDIR}/multimedia/mjpegtools \
		libdvdread.so:${PORTSDIR}/multimedia/libdvdread \
		libavcodec.so:${PORTSDIR}/multimedia/ffmpeg \
		libboost_filesystem.so:${PORTSDIR}/devel/boost-libs
RUN_DEPENDS=	gm:${PORTSDIR}/graphics/GraphicsMagick \
		dvda-author:${PORTSDIR}/audio/dvda-author \
		enca:${PORTSDIR}/converters/enca \
		growisofs:${PORTSDIR}/sysutils/dvd+rw-tools \
		toolame:${PORTSDIR}/audio/toolame

USES=		gettext pkgconfig scons tar:bzip2
USE_GCC=	any
INSTALLS_ICONS=	yes

CXXFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib -lintl
MAKE_ARGS=	DVDREAD_INCLUDE=${LOCALBASE}/include \
		DVDREAD_LIBPATH=${LOCALBASE}/lib \
		CXXFLAGS="${CXXFLAGS}" LDFLAGS="${LDFLAGS}" \
		CC="${CC}" CXX="${CXX}"

.include <bsd.port.pre.mk>

.if ${OPSYS} == FreeBSD && ${OSVERSION} >= 1000000
BROKEN=		does not build on 10.x+
.endif

post-patch:
	@${REINPLACE_CMD} -e 's|-O2||' ${WRKSRC}/SConstruct

post-install:
	cd ${WRKSRC}/docs/man/man1 && ${INSTALL_MAN} bombono-dvd.1 \
		mpeg2demux.1 ${STAGEDIR}${MANPREFIX}/man/man1

.include <bsd.port.post.mk>
