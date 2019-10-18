#
#
PORTNAME=	dns-ui
PORTREVISION=	3
DISTVERSIONPREFIX=	v
DISTVERSION=	0.2.3-61
DISTVERSIONSUFFIX=	-gc2e1e53
CATEGORIES=	dns

MAINTAINER=	sipopo@yandex.ru
COMMENT=	Opera DNS UI - A tool to manage a PowerDNS authoritative server in a corporate LDAP-driven environment

LICENSE=	APACHE20
LICANSE_FILE=	${WRKSRC}/LICENSE
	
USE_GITHUB=	yes
GH_ACCOUNT=	operasoftware
GH_PROJECT=	dns-ui

USE_PHP=	intl json curl mbstring ldap pdo pdo_pgsql hash
NO_ARCH=	yes
NO_BUILD=	yes

EXTRA_PATCHES=	${FILESDIR}/001-force_tag_comment.patch:-p1

DNSUIDIR?=	share/dns-ui

PLIST_SUB+=	DNSUIDIR=${DNSUIDIR}

do-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/${DNSUIDIR}
	${CP} -R ${WRKSRC}/* ${STAGEDIR}${PREFIX}/${DNSUIDIR}
	${CP} ${FILESDIR}/get_tag_comment.php ${STAGEDIR}${PREFIX}/${DNSUIDIR}/extensions
	${CP} ${FILESDIR}/site.css ${STAGEDIR}${PREFIX}/${DNSUIDIR}/public_html

post-install:
	${FIND} -s ${STAGEDIR}${PREFIX}/${DNSUIDIR} -not -type d | ${SORT} |\
		${SED} -e 's#^${STAGEDIR}${PREFIX}/##' >> ${TMPPLIST}

.include <bsd.port.mk>
