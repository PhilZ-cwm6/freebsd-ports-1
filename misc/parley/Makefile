PORTNAME=	parley
DISTVERSION=	${KDE_APPLICATIONS_VERSION}
CATEGORIES=	misc education kde kde-applications

MAINTAINER=	kde@FreeBSD.org
COMMENT=	Vocabulary trainer for KDE

BUILD_DEPENDS=	${LOCALBASE}/share/xsl/docbook/html/docbook.xsl:textproc/docbook-xsl \
		docbook-xml>0:textproc/docbook-xml

USES=		cmake desktop-file-utils gettext gnome kde:5 qt:5 tar:xz xorg
USE_GNOME=	libxml2 libxslt
USE_KDE=	attica auth codecs completion configwidgets coreaddons config \
		crash doctools i18n jobwidgets kcmutils kio newstuff \
		notifications kross khtml service solid sonnet textwidgets \
		widgetsaddons windowsystem xmlgui \
		libkeduvocdocument \
		ecm_build
USE_QT=		concurrent core dbus declarative gui location network multimedia \
		printsupport script svg webchannel webengine widgets xml \
		buildtools_build qmake_build
USE_XORG=	x11 xrender

OPTIONS_DEFINE=	DOCS

.include <bsd.port.mk>
