NAME = jwg-solarnode-app-main
VERSION = 3.1.0-1
PATHS = var
SN_BUILD_ROOT = ${CURDIR}/solarnetwork-build
SN_IVY_FILE = ${CURDIR}/ivy-jwg-main.xml
DEB_BUILD_ROOT = $(SN_BUILD_ROOT)/solarnode-deploy/generic/build/deb
SN_ANT_OPTS =

deb : app-main table
	fpm -s dir \
		-t deb \
		-n $(NAME) \
		-v $(VERSION) \
		--description 'jwg standard device support' \
		--chdir $(DEB_BUILD_ROOT) \
		-a all \
		--maintainer 'Matt Magoffin <matt@msqr.us>' \
		--vendor 'Matt Magoffin' \
		--license 'Proprietary' \
		-f \
		-d 'solarnode-app-core (>= 3.27.1)' \
		-d 'solarnode-app-io-modbus-server (>= 1.0)' \
		-d 'solarnode-app-camera-ffmpeg (>= 1.0)' \
		-d 'solarnode-app-datumfilters (>= 1.3)' \
		-d 'solarnode-app-deson (>= 1.0)' \
		-d 'solarnode-app-modbus (>= 1.2)' \
		-d 'solarnode-app-osstat (>= 1.1.1)' \
		-d 'solarnode-app-sma (>= 1.2.0)' \
		-d 'solarnode-app-solarflux (>= 1.2)' \
		-d 'solarnode-app-sunspec (>= 1.1)' \
		-d 'solarnode-app-storage-s3 (>= 1.0.1)' \
		-d 'solarnode-app-storage-upload (>= 1.1)' \
		-d 'solarnode-io-modbus' \
		-d 'solarnode-io-serial' \
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
