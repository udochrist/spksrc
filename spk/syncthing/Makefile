SPK_NAME = syncthing
SPK_VERS = 0.14.49
SPK_REV = 15
SPK_ICON = src/syncthing.png
DSM_UI_DIR = app

DEPENDS = cross/busybox cross/$(SPK_NAME)

MAINTAINER = Safihre
DESCRIPTION = Automatically sync files via secure, distributed technology.
DESCRIPTION_FRE = Synchronisation automatique de fichiers via une technologie sécurisée et distribuée.
RELOAD_UI = yes
DISPLAY_NAME = Syncthing
CHANGELOG = "Integrate with DSM5+6 Generic Service support for correct permissions."
HOMEPAGE = http://www.syncthing.net
LICENSE = MPLv2.0
STARTABLE = yes

WIZARDS_DIR = src/wizard/

SERVICE_USER = auto
SERVICE_SETUP = src/service-setup.sh
SERVICE_PORT = 8384
SERVICE_PORT_TITLE = $(DISPLAY_NAME)

# Use busybox start-stop-daemon support
# Options and environment are provided in service-setup.sh
SERVICE_EXE = $${SYNOPKG_PKGDEST}/bin/syncthing

# Admin link for in DSM UI
ADMIN_PORT = $(SERVICE_PORT)

FWPORTS = src/${SPK_NAME}.sc

POST_STRIP_TARGET = syncthing_extra_install

BUSYBOX_CONFIG = usrmng daemon nice
ENV += BUSYBOX_CONFIG="$(BUSYBOX_CONFIG)"

include ../../mk/spksrc.spk.mk

.PHONY: syncthing_extra_install
syncthing_extra_install:
	install -m 755 -d $(STAGING_DIR)/var
	install -m 600 src/config.xml $(STAGING_DIR)/var/config.xml
	install -m 644 src/options.conf $(STAGING_DIR)/var/options.conf
