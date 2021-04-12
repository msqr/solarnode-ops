NAME = msqr-solarnode-app-core
VERSION = 1.0.0_1
ARCH = all
PATHS = usr
SN_BUILD_ROOT = solarnetwork-build
DEB_BUILD_ROOT = $(SN_BUILD_ROOT)/solarnode-deploy/generic/build/deb
IVY_FILE = ${CURDIR}/ivy-msqr-main.xml

deb : app-core table
	fpm -s dir \
		-t freebsd \
		-n $(NAME) \
		-v $(VERSION) \
		--description 'msqr standard device support' \
		--chdir $(DEB_BUILD_ROOT) \
		-a $(ARCH) \
		--maintainer 'Matt Magoffin <matt@msqr.us>' \
		--vendor 'Matt Magoffin' \
		--license 'Proprietary' \
		-f \
		-d 'solarnode-app-core (>= 1.14.0)' \
		$(PATHS)

clean : 
	rm -f $(NAME)-$(VERSION).txz

app-core :
	ant -f $(SN_BUILD_ROOT)/solarnode-deploy/generic/build.xml \
		"-Divy.file=$(IVY_FILE)" \
		"-Ddeb.nocopy=1" \
		"-Ddir.deb.app.path=usr/local/solarnode" \
		clean deb-package-assemble

table :
	java -jar "$(SN_BUILD_ROOT)/solarnetwork-osgi-lib/lib/bh.jar" \
		"$(SN_BUILD_ROOT)/solarnode-deploy/generic/build/deb"
