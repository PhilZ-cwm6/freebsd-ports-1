PORTNAME=	birdfont
DISTVERSIONPREFIX=	v
DISTVERSION=	2.29.6
CATEGORIES=	graphics x11-fonts

MAINTAINER=	0mp@FreeBSD.org
COMMENT=	Editor for vector graphics and TTF, OTF, EOT and SVG fonts

LICENSE=	GPLv3+
LICENSE_FILE=	${WRKSRC}/GPLv3.txt

BUILD_DEPENDS=	${PYTHON_PKGNAMEPREFIX}doit>0:devel/py-doit@${PY_FLAVOR} \
		valac:lang/vala
LIB_DEPENDS=	libfontconfig.so:x11-fonts/fontconfig \
		libfreetype.so:print/freetype2 \
		libgee-0.8.so:devel/libgee \
		libharfbuzz.so:print/harfbuzz \
		libnotify.so:devel/libnotify \
		libsoup-2.4.so:devel/libsoup \
		libwebkit2gtk-4.0.so:www/webkit2-gtk3 \
		libxmlbird.so:textproc/libxmlbird

USES=		compiler:c++11-lang gettext-tools gnome pkgconfig \
		python:3.7+,build shared-mime-info shebangfix sqlite:3 tar:xz
USE_GITHUB=	yes
GH_ACCOUNT=	johanmattssonm
USE_GNOME=	cairo gdkpixbuf2 glib20 gtk30
USE_LDCONFIG=	yes
SHEBANG_FILES=	configure install.py

HAS_CONFIGURE=	yes
CONFIGURE_ARGS=	--cc="${CC}" \
		--cflags="${CFLAGS}" \
		--dest="${STAGEDIR}" \
		--ldflags="${LDFLAGS}" \
		--prefix="${PREFIX}"

_STRIPPABLE=	bin/birdfont bin/birdfont-autotrace bin/birdfont-export \
		bin/birdfont-import lib/libbirdfont.so.36.0 \
		lib/libbirdgems.so.0.0

do-build:
	(cd ${WRKSRC} && ${SETENV} ${MAKE_ENV} ${PYTHON_CMD} build.py)

do-install:
	(cd ${WRKSRC} && ./install.py \
		--dest="${STAGEDIR}" \
		--nogzip=1 \
		--manpages-directory="/share/man/man1")
	@(cd ${STAGEDIR}${PREFIX} && \
		${STRIP_CMD} ${_STRIPPABLE})

.include <bsd.port.mk>
