#-----------------------------------------------------------------------
# Licensed Materials - Property of IBM
#
# (C) Copyright IBM Corporation 2020.
#
# US Government Users Restricted Rights - Use, duplication or disclosure
# restricted by GSA ADP Schedule Contract with IBM Corporation.
#-----------------------------------------------------------------------

GO ?= $(shell which go 2>/dev/null)
GOEXT_COUNT ?= 1
GOEXT_PACKAGES ?=
GOEXT_SOURCE_DIR != pwd

# Builds one or more packages.
#
# Variables:
#   GOEXT_PACKAGES:
#     One or more packages to build.  Example:  GOEXT_PACKAGES="./util ./web"
#   GOEXT_SOURCE_DIR:
#     Typically, the parent directory containing GOEXT_PACKAGES.  This target
#     will switch to GOEXT_SOURCE_DIR before building the packages.  Default:
#     the current working directory.
## Builds one or more packages
.PHONY: go/ext/build
go/ext/build:
	$(call assert-set,GO)
	$(call assert-set,GOEXT_PACKAGES)
	cd $(GOEXT_SOURCE_DIR) && $(GO) build $(GOEXT_PACKAGES)

# Gets one or more packages.
#
# Variables:
#   GOEXT_PACKAGES:
#     One or more packages to get.  Example:  GOEXT_PACKAGES=github.com/fsnotify/fsnotify
## Gets one or more packages
.PHONY: go/ext/get
go/ext/get:
	$(call assert-set,GO)
	$(call assert-set,GOEXT_PACKAGES)
	$(GO) get -u -v $(GOEXT_PACKAGES)

# Installs one or more packages.
#
# Variables:
#   GOEXT_PACKAGES:
#     One or more packages to install.  Example:  GOEXT_PACKAGES=./server"
#   GOEXT_SOURCE_DIR:
#     Typically, the parent directory containing GOEXT_PACKAGES.  This target
#     will switch to GOEXT_SOURCE_DIR before installing the packages.  Default:
#     the current working directory.
## Installs one or more packages.
.PHONY: go/ext/install
go/ext/install:
	$(call assert-set,GO)
	$(call assert-set,GOEXT_PACKAGES)
	cd $(GOEXT_SOURCE_DIR) && $(GO) install $(GOEXT_PACKAGES)

# Tests one or more packages.
#
# Variables:
#   GOEXT_COUNT:
#     The number of times to run the tests.  Default: one.
#   GOEXT_PACKAGES:
#     One or more packages to test.  Example:  GOEXT_PACKAGES="./util ./web"
#   GOEXT_SOURCE_DIR:
#     Typically, the parent directory containing GOEXT_PACKAGES.  This target
#     will switch to GOEXT_SOURCE_DIR before building the packages.  Default:
#     the current working directory.
## Tests one or more packages
.PHONY: go/ext/test
go/ext/test:
	$(call assert-set,GO)
	$(call assert-set,GOEXT_PACKAGES)
	cd $(GOEXT_SOURCE_DIR) && $(GO) test -count=$(GOEXT_COUNT) $(GOEXT_PACKAGES)
