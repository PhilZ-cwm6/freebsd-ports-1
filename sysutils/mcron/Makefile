# Created by: ijliao

PORTNAME=	mcron
PORTVERSION=	1.2.1
PORTREVISION=	1
CATEGORIES=	sysutils
MASTER_SITES=	GNU

MAINTAINER=	ports@FreeBSD.org
COMMENT=	100% compatible replacement for Vixie cron

LICENSE=	GPLv3
LICENSE_FILE=	${WRKSRC}/COPYING

LIB_DEPENDS=	libguile-2.2.so:lang/guile2

USES=		gmake pkgconfig
GNU_CONFIGURE=	yes

CONFLICTS_INSTALL=	interchange isc-cron # bin/crontab

TEST_TARGET=	check

INFO=		mcron

PLIST_SUB=	GUILE_SITE=share/guile/site/2.2 \
		GUILE_SITE_CCACHE=lib/guile/2.2/site-ccache

.include <bsd.port.mk>
