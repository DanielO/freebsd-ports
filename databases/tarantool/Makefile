# Created by: Veniamin Gvozdikov <vg@FreeBSD.org>
# $FreeBSD$

PORTNAME=	tarantool
PORTVERSION=	1.6.5
PORTREVISION=	1
CATEGORIES=	databases
MASTER_SITES=	http://tarantool.org/dist/master/
DISTNAME=	${PORTNAME}-${PORTVERSION}-${TR_REV}-src

MAINTAINER=	vg@FreeBSD.org
COMMENT=	NoSQL database running in a Lua application server

LICENSE=	BSD2CLAUSE

TR_REV=		238-g74f3d65
MAKE_JOBS_UNSAFE=yes
USES=		cmake compiler:c++11-lang gettext gmake perl5 readline
USE_GCC=	4.9+ # clang bug PR/201270
USE_LDCONFIG=	yes
USE_RC_SUBR=	${PORTNAME}
SUB_FILES=	pkg-message

TT_DATADIR?=	/var/db/tarantool
TT_RUNDIR?=	/var/run/tarantool
TT_LOGDIR?=	/var/log/tarantool

CMAKE_ARGS=	-DCMAKE_INSTALL_MANDIR=man \
		-DCMAKE_INSTALL_SYSCONFDIR=${ETCDIR} \
		-DCMAKE_LOCALSTATE_DIR=${DATADIR} \
		-DTARANTOOL_DATADIR="${TT_DATADIR}"

USERS=		tarantool
GROUPS=		tarantool

SUB_LIST+=	PORTNAME=${PORTNAME} \
	TT_USER=${USERS} \
	TT_DATADIR=${TT_DATADIR} \
	TT_LOGDIR=${TT_LOGDIR} \
	TT_RUNDIR=${TT_RUNDIR}

PLIST_SUB+=	TT_USER=${USERS} \
	TT_GROUP=${GROUPS} \
	TT_LOGDIR=${TT_LOGDIR} \
	TT_DATADIR=${TT_DATADIR} \
	TT_RUNDIR=${TT_RUNDIR}

OPTIONS_DEFINE=	DEBUG
DEBUG_DESC=	Enable debug

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MDEBUG}
CMAKE_BUILD_TYPE=	RelWithDebugInfo
CMAKE_ARGS+=	-DENABLE_BACKTRACE=ON
.else
CMAKE_BUILD_TYPE=	Rel
CMAKE_ARGS+=	-DENABLE_BACKTRACE=OFF
.endif

.if ${OSVERSION} < 1000000
IGNORE=	does not support FreeBSD versions < 10.0
.endif

post-install:
	${MKDIR} ${STAGEDIR}${TT_LOGDIR} \
		${STAGEDIR}${TT_DATADIR} \
		${STAGEDIR}${TT_RUNDIR} \
		${STAGEDIR}${ETCDIR}/instances.enabled

.include <bsd.port.mk>
