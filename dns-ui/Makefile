#
#
PORTNAME=	dns-ui
DISTVERSIONPREFIX=	v
DISTVERSION=	0.2.3-47
DISTVERSIONSUFFIX=	-g53f5118
CATEGORIES=	dns

MAINTAINER=	sipopo@yandex.ru
COMMENT=	Opera DNS UI - A tool to manage a PowerDNS authoritative server in a corporate LDAP-driven environment

LICENSE=	APACHE20
LICANSE_FILE=	${WRKSRC}/LICENSE
	
USE_GITHUB=	yes
GH_ACCOUNT=	operasoftware
GH_PROJECT=	dns-ui

USE_PHP=	intl json curl mbstring ldap pdo pdo_pgsql
NO_ARCH=	yes
NO_BUILD=	yes

DNSUIDIR?=	share/dns-ui

PLIST_SUB+=	DNSUIDIR=${DNSUIDIR}

do-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/${DNSUIDIR}
	${CP} -R ${WRKSRC}/* ${STAGEDIR}${PREFIX}/${DNSUIDIR}

post-install:
	${FIND} -s ${STAGEDIR}${PREFIX}/${DNSUIDIR} -not -type d | ${SORT} |\
		${SED} -e 's#^${STAGEDIR}${PREFIX}/##' >> ${TMPPLIST}

.include <bsd.port.mk>
