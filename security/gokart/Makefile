# Created by: Gabriel M. Dutra <0xdutra@gmail.com>

PORTNAME=	gokart
DISTVERSIONPREFIX=	v
DISTVERSION=	0.4.0
CATEGORIES=	security

MAINTAINER=	0xdutra@gmail.com
COMMENT=	Go Security Static Analysis

LICENSE=	APACHE20
LICENSE_FILE=	${WRKSRC}/LICENSE

USES=	go:modules

GO_MODULE=	github.com/praetorian-inc/gokart

GO_TARGET=	gokart

PLIST_FILES=	bin/${PORTNAME}

PORTDOCS=	README.md

OPTIONS_DEFINE=	DOCS

do-install-DOCS-on:
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/${PORTDOCS} ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>
