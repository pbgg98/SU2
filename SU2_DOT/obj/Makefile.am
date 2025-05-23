################################################################################
#
# \file Makefile.am
# \brief Makefile for SU2_DOT
# \author M. Colonno, T. Economon, F. Palacios
# \version 7.5.1 "Blackbird"
#
# SU2 Project Website: https://su2code.github.io
#
# The SU2 Project is maintained by the SU2 Foundation
# (http://su2foundation.org)
#
# Copyright 2012-2023, SU2 Contributors (cf. AUTHORS.md)
#
# SU2 is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# SU2 is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with SU2. If not, see <http://www.gnu.org/licenses/>.
#
################################################################################

AUTOMAKE_OPTIONS = subdir-objects
ACLOCAL_AMFLAGS = ${ACLOCAL_FLAGS}

bin_PROGRAMS =

if BUILD_NORMAL
bin_PROGRAMS += ../bin/SU2_DOT
endif

if BUILD_REVERSE
bin_PROGRAMS += ../bin/SU2_DOT_AD
endif

su2_dot_sources = ../include/SU2_DOT.hpp \
		../src/SU2_DOT.cpp

su2_dot_ldadd =
su2_dot_cxx_flags = -std=c++11

if BUILD_NORMAL
su2_dot_ldadd += \
  ../../SU2_CFD/obj/libSU2Core.a \
  ../../Common/lib/libSU2.a
endif

if BUILD_REVERSE
su2_dot_ldadd += \
  ../../SU2_CFD/obj/libSU2Core_AD.a \
  ../../Common/lib/libSU2_AD.a
endif

# always link to built dependencies from ./externals
su2_dot_cxx_flags += @su2_externals_INCLUDES@
su2_dot_ldadd += @su2_externals_LIBS@
su2_dot_ldadd += @su2_externals_LIBPTHREAD@

# if BUILD_MUTATIONPP
su2_dot_cxx_flags += @MUTATIONPP_CXX@
su2_dot_ldadd += @MUTATIONPP_LD@
# endif

if BUILD_NORMAL
___bin_SU2_DOT_SOURCES = ${su2_dot_sources}
___bin_SU2_DOT_CXXFLAGS = ${su2_dot_cxx_flags}
___bin_SU2_DOT_LDADD =  ${su2_dot_ldadd}
endif

if BUILD_REVERSE
___bin_SU2_DOT_AD_SOURCES = ${su2_dot_sources}
___bin_SU2_DOT_AD_CXXFLAGS = @REVERSE_CXX@ ${su2_dot_cxx_flags}
___bin_SU2_DOT_AD_LDADD = @REVERSE_LIBS@ ${su2_dot_ldadd}
endif
