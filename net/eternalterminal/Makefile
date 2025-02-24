PORTNAME=	eternalterminal
DISTVERSIONPREFIX=	et-v
DISTVERSION=	6.1.11
PORTREVISION=	2
CATEGORIES=	net

MAINTAINER=	willtisdale@gmail.com
COMMENT=	Remote shell that reconnects without interrupting session

LICENSE=	APACHE20
LICENSE_FILE=	${WRKSRC}/LICENSE

LIB_DEPENDS=	libgflags.so:devel/gflags \
		libglog.so:devel/glog \
		libprotobuf.so:devel/protobuf \
		libsodium.so:security/libsodium \
		libunwind.so:devel/libunwind

USES=		cmake compiler:c++11-lang ncurses
USE_GITHUB=	yes
GH_ACCOUNT=	MisterTea
GH_PROJECT=	EternalTerminal

CMAKE_ON=	DISABLE_VCPKG

MAKE_JOBS_UNSAFE=	yes # temporarily set due to weird races resulting in build failures

CONFLICTS_INSTALL=	linux-enemyterritory # bin/et

post-patch:
	@${REINPLACE_CMD} -e 's,/usr/local,${PREFIX},' ${WRKSRC}/rc.d/etserver

post-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/etc/etserver
	${INSTALL_DATA} ${WRKSRC}/etc/et.cfg \
		${STAGEDIR}${PREFIX}/etc/etserver/et.cfg.sample
	${INSTALL_SCRIPT} ${WRKSRC}/rc.d/etserver \
		${STAGEDIR}${PREFIX}/etc/rc.d

.include <bsd.port.mk>
