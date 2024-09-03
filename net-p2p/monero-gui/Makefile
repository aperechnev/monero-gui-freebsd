PORTNAME=		monero-gui
DISTVERSIONPREFIX=	source-v
DISTVERSION=	0.18.3.4
CATEGORIES=		net-p2p finance
MASTER_SITES=	https://downloads.getmonero.org/gui/

MAINTAINER=	alexander@perechnev.com
COMMENT=	Monero: the secure, private, untraceable cryptocurrency (GUI).
WWW=		https://www.getmonero.org/

LICENSE=	BSD3CLAUSE

BUILD_DEPENDS= \
		${LOCALBASE}/include/rapidjson/document.h:devel/rapidjson \
		${LOCALBASE}/include/zmq.hpp:net/cppzmq
LIB_DEPENDS= \
		libboost_chrono.so:devel/boost-libs \
		libboost_date_time.so:devel/boost-libs \
		libboost_filesystem.so:devel/boost-libs \
		libboost_program_options.so:devel/boost-libs \
		libboost_regex.so:devel/boost-libs \
		libboost_serialization.so:devel/boost-libs \
		libboost_system.so:devel/boost-libs \
		libboost_thread.so:devel/boost-libs \
		libgcrypt.so:security/libgcrypt \
		libgpg-error.so:security/libgpg-error \
		libgssapi_krb5.so:security/krb5 \
		libhidapi.so:comms/hidapi \
		libminiupnpc.so:net/miniupnpc \
		libnorm.so:net/norm \
		libpgm.so:net/openpgm \
		libsodium.so:security/libsodium \
		libunbound.so:dns/unbound \
		libunwind.so:devel/libunwind \
		libzmq.so:net/libzmq4
RUN_DEPENDS= \
		monero-cli>0:net-p2p/monero-cli

USES= qmake qt:5 xorg cmake compiler:c++11-lib pkgconfig readline ssl tar:bzip2

USE_QT=	buildtools:build qmake:build concurrent:build l10n linguist declarative svg widgets gui xml xmlpatterns network core

USE_XORG= sm ice x11 xext

CMAKE_ARGS+= \
		-DMANUAL_SUBMODULES:BOOL=ON \
		-DCMAKE_BUILD_TYPE=Release \
		-DARCH=default \
		-DWITH_DESKTOP_ENTRY:BOOL=OFF \
		-DWITH_UPDATER:BOOL=OFF

PLIST_FILES=	bin/monero-wallet-gui

do-install:
	${INSTALL_PROGRAM} ${WRKDIR}/.build/bin/monero-wallet-gui ${STAGEDIR}${PREFIX}/bin/

.include <bsd.port.mk>
