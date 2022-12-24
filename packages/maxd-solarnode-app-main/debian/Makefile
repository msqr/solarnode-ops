NAME = maxd-solarnode-app-main
VERSION = 1.0.0-1
PATHS = var
SN_BUILD_ROOT = ${CURDIR}/solarnetwork-build
SN_IVY_FILE = ${CURDIR}/ivy-maxd-main.xml
DEB_BUILD_ROOT = $(SN_BUILD_ROOT)/solarnode-deploy/generic/build/deb
SN_ANT_OPTS =

deb : app-main table
	fpm -s dir \
		-t deb \
		-n $(NAME) \
		-v $(VERSION) \
		--description 'maxd standard device support' \
		--chdir $(DEB_BUILD_ROOT) \
		-a all \
		--maintainer 'Matt Magoffin <matt@msqr.us>' \
		--vendor 'Matt Magoffin' \
		--license 'Proprietary' \
		-f \
		-d 'solarnode-app-core (>= 2.8)' \
		-d 'solarnode-io-modbus' \
		--chdir "$(DEB_BUILD_ROOT)" \
		$(PATHS)

clean : 
	rm -f $(NAME)-$(VERSION).txz

app-main :
	ant -f "$(SN_BUILD_ROOT)/solarnode-deploy/generic/build.xml" \
		"-Divy.file=$(SN_IVY_FILE)" \
		"-Ddir.deb.assemble=$(DEB_BUILD_ROOT)" \
		"-Ddeb.nocopy=1" \
		$(SN_ANT_OPTS) \
		clean deb-package-assemble

table :
	java -jar "$(SN_BUILD_ROOT)/solarnetwork-osgi-lib/lib/bh.jar" "$(DEB_BUILD_ROOT)"
