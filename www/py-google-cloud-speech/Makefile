# Created by: Po-Chuan Hsieh <sunpoet@FreeBSD.org>

PORTNAME=	google-cloud-speech
PORTVERSION=	2.12.0
CATEGORIES=	www python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	sunpoet@FreeBSD.org
COMMENT=	Google Cloud Speech API client library

LICENSE=	APACHE20
LICENSE_FILE=	${WRKSRC}/LICENSE

RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}google-api-core>=1.28.0<3.0.0:www/py-google-api-core@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}libcst>=0.2.5:devel/py-libcst@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}proto-plus>=1.4.0:devel/py-proto-plus@${PY_FLAVOR}

USES=		python:3.6+
USE_PYTHON=	autoplist concurrent distutils

NO_ARCH=	yes

.include <bsd.port.mk>
