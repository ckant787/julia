default: Pkg
SRCDIR := $(abspath $(dir $(lastword $(MAKEFILE_LIST))))
JULIAHOME := $(abspath $(SRCDIR)/..)
SRCCACHE := $(abspath $(SRCDIR)/srccache)
BUILDDIR := $(SRCCACHE)

include $(JULIAHOME)/Make.inc
include $(JULIAHOME)/deps/tools/common.mk
include $(JULIAHOME)/deps/tools/git-external.mk

PKG := https://github.com/JuliaLang/Pkg.jl
PKG_TAR_URL = https://api.github.com/repos/JuliaLang/Pkg.jl/tarball/$1
$(eval $(call git-external,Pkg,PKG,,,$(BUILDDIR)))

extract-pkg: $(BUILDDIR)/$(PKG_SRC_DIR)/source-extracted
Pkg: $(BUILDDIR)/$(PKG_SRC_DIR)/source-extracted
	rm -rf $@
	cp -r $(BUILDDIR)/$(PKG_SRC_DIR) $@
get-pkg: Pkg
clean-pkg:
	-rm -rf Pkg
	-rm -rf $(BUILDDIR)/$(PKG_SRC_DIR)

.PHONY: default get clean
