PORTNAME=	libretro-cap32
PORTVERSION=	0.20210110
CATEGORIES=	games

MAINTAINER=	dmenelkir@gmail.com
COMMENT=	Amstrad CPC computers emulator core for libretro API

LICENSE=	GPLv2

USES=		compiler:c++11-lang gmake localbase
USE_LDCONFIG=	yes

USE_GITHUB=	yes
GH_ACCOUNT=	libretro
GH_TAGNAME=	ad7397f

PLIST_FILES=	lib/libretro/cap32_libretro.so

do-install:
	${MKDIR} ${STAGEDIR}/${PREFIX}/lib/libretro;
	${INSTALL_LIB} ${WRKSRC}/cap32_libretro.so ${STAGEDIR}/${PREFIX}/lib/libretro;

.include <bsd.port.mk>
