VERSION=$(shell sed -n 's/^VERSION=//p' mkbootdisk)

mandir=/usr/share/man

all:
	echo version $(VERSION)

install:
	for i in sbin $(mandir)/man8; do \
		if [ ! -d $(BUILDROOT)/$$i ]; then \
			mkdir -p $(BUILDROOT)/$$i; \
		fi; \
	done
	if [ `uname -m | sed s/sparc64/sparc/` = "sparc" ]; then \
		sed 's/%VERSIONTAG%/$(VERSION)/' < mkbootdisk.sparc > $(BUILDROOT)/sbin/mkbootdisk; \
	else \
		cp -p mkbootdisk $(BUILDROOT)/sbin/mkbootdisk; \
	fi
	chmod 755 $(BUILDROOT)/sbin/mkbootdisk
	install -m644 mkbootdisk.8 $(BUILDROOT)$(mandir)/man8/mkbootdisk.8
