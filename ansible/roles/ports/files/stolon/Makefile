# v0.13.0-67-gdead601
#
PORTNAME=	stolon
DISTVERSIONPREFIX=  v
DISTVERSION=	0.14.0-4
DISTVERSIONSUFFIX=  -g8048057
CATEGORIES=	databases

MAINTAINER=	sipopo@yandex.ru
COMMENT=	Stolon - PostgreSQL cloud native High Availability

LICENSE=	APACHE20
LICENSE_FILE=	${WRKSRC}/LICENSE

USES=		go
GO_PKGNAME=	github.com/sorintlab/stolon
GO_TARGET=	github.com/sorintlab/stolon-sentinel \
		github.com/sorintlab/stolon-proxy \
		github.com/sorintlab/stolon-keeper \
		github.com/sorintlab/stolonctl

USE_RC_SUBR=	stolonkeeper stolonproxy stolonsentinel

USE_GITHUB=	yes
GH_ACCOUNT=	sorintlab
GH_PROJECT=	stolon

UID_FILES=      ${FILESDIR}/UIDs
GID_FILES=      ${FILESDIR}/GIDs

USERS=		stolon
GROUPS=		stolon

# Make a version for utils
LD_FLAGS=	-s -X ${GO_PKGNAME}/cmd.Version=${DISTVERSIONFULL}
GO_BUILDFLAGS=	-installsuffix cgo -ldflags "${LD_FLAGS}"
CGO_ENABLED=	0


do-build:
	(cd ${GO_WRKSRC}; \
	${GO_ENV}  ${GO_CMD} build ${GO_BUILDFLAGS} -o ${GO_WRKDIR_BIN}/stolon-sentinel ${GO_PKGNAME}/cmd/sentinel; \
	${GO_ENV} ${GO_CMD} build ${GO_BUILDFLAGS} -o ${GO_WRKDIR_BIN}/stolon-proxy ${GO_PKGNAME}/cmd/proxy; \
	${GO_ENV} ${GO_CMD} build ${GO_BUILDFLAGS} -o ${GO_WRKDIR_BIN}/stolonctl ${GO_PKGNAME}/cmd/stolonctl; \
	${GO_ENV} CGO_ENABLED=1 ${GO_CMD} build ${GO_BUILDFLAGS} -o ${GO_WRKDIR_BIN}/stolon-keeper ${GO_PKGNAME}/cmd/keeper) 
	${MKDIR} ${STAGEDIR}${ETCDIR}
.for i in stolon-keeper.conf stolon-proxy.conf stolon-sentinel.conf
	${INSTALL_DATA} ${FILESDIR}/${i} ${STAGEDIR}${ETCDIR}/${i}-dist
.endfor

.include <bsd.port.mk>
