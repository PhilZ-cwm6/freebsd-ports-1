PORTNAME=	libretro-paralleln64
PORTVERSION=	0.20210127
PORTREVISION=	1
CATEGORIES=	games

MAINTAINER=	dmenelkir@gmail.com
COMMENT=	Improved Nintendo 64 core for libretro

# Commercial users must seek permission from copyright holders.
LICENSE=	BITSTREAM_VERA CC0-1.0 GFDL GPLv2 GPLv3 LGPL3 MIT ZLIB
LICENSE_COMB=	multi
LICENSE_NAME_BITSTREAM_VERA=	Bitstream Vera Sans - Roman Release 1.10
LICENSE_FILE_BITSTREAM_VERA=	${WRKSRC}/mupen64plus-core/doc/font-license
LICENSE_PERMS_BITSTREAM_VERA=	auto-accept

BROKEN_aarch64=	fails to build: mupen64plus-core/src/r4300/new_dynarec/arm64/assem_arm64.h:141:8: error: unknown type name 'u_int'
BROKEN_i386=	Doesn't build.

USES=		compiler:c++11-lang gmake gl localbase
USE_GL=		gl
USE_LDCONFIG=	yes

DYNAREC=	${ARCH:S/amd64/x86_64/:C/armv.*/arm/:S/i386/x86/}

MAKE_ARGS=	WITH_DYNAREC=${DYNAREC}

USE_GITHUB=	yes
GH_ACCOUNT=	libretro
GH_PROJECT=	parallel-n64
GH_TAGNAME=	6e26fbb

PLIST_FILES=	lib/libretro/parallel_n64_libretro.so

do-install:
	${MKDIR} ${STAGEDIR}/${PREFIX}/lib/libretro;
	${INSTALL_LIB} ${WRKSRC}/parallel_n64_libretro.so ${STAGEDIR}/${PREFIX}/lib/libretro;

.include <bsd.port.mk>
