# Created by: Pedro F. Giffuni <giffunip@tutopia.com>

PORTNAME=	silo
PORTVERSION=	4.10.2
DISTVERSIONSUFFIX=	-bsd
PORTREVISION=	14
CATEGORIES=	science
MASTER_SITES=	http://wci.llnl.gov/content/assets/docs/simulation/computer-codes/${PORTNAME}/silo-${PORTVERSION}/

MAINTAINER=	dbaio@FreeBSD.org
COMMENT=	Mesh and field I/O library and scientific database

LICENSE=	BSD3CLAUSE
LICENSE_FILE=	${WRKSRC}/COPYRIGHT

USES=		gmake libtool readline
USE_LDCONFIG=	yes

GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--enable-shared --disable-static
INSTALL_TARGET=	install-strip

CONFLICTS_INSTALL=		deforaos-browser # bin/browser

OPTIONS_DEFINE=			FORTRAN HDF5 PYTHON
OPTIONS_DEFAULT=		HDF5
OPTIONS_SUB=			yes

FORTRAN_CONFIGURE_ENABLE=	fortran
FORTRAN_USES=			fortran

HDF5_LIB_DEPENDS=		libhdf5.so:science/hdf5
HDF5_CONFIGURE_ON=		--with-hdf5=${LOCALBASE}/include,${LOCALBASE}/lib
HDF5_PLIST_SUB=			SUFX_HDF5="h5"
HDF5_PLIST_SUB_OFF=		SUFX_HDF5=""

PYTHON_CONFIGURE_ENABLE=	pythonmodule
PYTHON_USES=			python

post-patch:
	@${REINPLACE_CMD} -e \
		's|\(_Qt_dir/include\)"|\1/qt4"| ; \
		 s|\(_Qt_dir/lib\)"|\1/qt4"| ; \
		 s|\(/uic\)"|\1-qt4"| ; \
		 s|\(/moc\)"|\1-qt4"| ; \
		 s|\(/lrelease\)"|\1-qt4"| ; \
		 s|\(/lupdate\)"|\1-qt4"|' ${WRKSRC}/configure
	@${REINPLACE_CMD} -e \
		'/-avoid-version/s|^|#| ; \
		 /^install-data-am/s|:.*|:|' ${WRKSRC}/src/Makefile.in
	@${REINPLACE_CMD} -e \
		'/-ldl/s|^|#|' ${WRKSRC}/tests/Makefile.in
	@${REINPLACE_CMD} -e \
		's|@libdir@|@pythondir@|' ${WRKSRC}/tools/python/Makefile.in
	@${REINPLACE_CMD} -e \
		's|\(INBUILD\));|\1, me);|' ${WRKSRC}/src/hdf5_drv/silo_hdf5.c

.if defined(MAINTAINER_MODE)
regression-test: build
	@cd ${WRKSRC}/tests && ${SETENV} ${MAKE_ENV} ${MAKE_CMD} check
.endif

.include <bsd.port.mk>
