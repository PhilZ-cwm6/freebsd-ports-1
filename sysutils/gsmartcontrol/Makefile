# Created by: Pawel Pekala <c0rn@o2.pl>

PORTNAME=	gsmartcontrol
PORTVERSION=	1.1.3
PORTREVISION=	4
CATEGORIES=	sysutils
MASTER_SITES=	SF/${PORTNAME}/${PORTVERSION}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Graphical user interface for smartmontools

LICENSE=	BSD3CLAUSE BSL GPLv2 GPLv3 PD ZLIB
LICENSE_COMB=	multi
LICENSE_FILE_BSD3CLAUSE=${WRKSRC}/LICENSE_bsd-ac.txt
LICENSE_FILE_BSL=	${WRKSRC}/LICENSE_boost_1_0.txt
LICENSE_FILE_GPLv2=	${WRKSRC}/LICENSE_gpl2.txt
LICENSE_FILE_GPLv3=	${WRKSRC}/LICENSE_gpl3.txt
LICENSE_FILE_PD=	${WRKSRC}/LICENSE_unlicense.txt
LICENSE_FILE_ZLIB=	${WRKSRC}/LICENSE_zlib.txt

LIB_DEPENDS=	libpcre.so:devel/pcre
RUN_DEPENDS=	bash:shells/bash \
		pkexec:sysutils/polkit \
		smartctl:sysutils/smartmontools \
		xterm:x11/xterm

USES=		compiler:c++11-lang gnome libtool pkgconfig tar:bzip2
USE_CXXSTD=	c++11
USE_GNOME=	atkmm cairo glibmm gtk30 gtkmm30 libsigc++20 pangomm

GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--disable-libglade

OPTIONS_DEFINE=	DOCS

post-patch:
# Avoid conflict with C++20 <version> by ignoring <...> under WRKSRC
	@${REINPLACE_CMD} -i .c++20 '/ADDITIONAL_INCLUDES/s/-I/-iquote/g' \
		${WRKSRC}/configure
	@${REINPLACE_CMD} -i .c++20 's/-I/-iquote/g' \
		${WRKSRC}/src/Makefile.in \
		${WRKSRC}/src/*/Makefile.in
	@${REINPLACE_CMD} -i .c++20 '/config\.h/y/<>/""/' \
		${WRKSRC}/src/global_macros.h
	@${REINPLACE_CMD} -i '' 's|%%PREFIX%%|${PREFIX}|g' \
		${WRKSRC}/data/org.gsmartcontrol.policy

.include <bsd.port.mk>
