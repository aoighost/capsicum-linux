TARGETS = breakpoints
TARGETS += cpu-hotplug
TARGETS += efivarfs
TARGETS += exec
TARGETS += firmware
TARGETS += ftrace
TARGETS += kcmp
TARGETS += memfd
TARGETS += memory-hotplug
TARGETS += mount
TARGETS += mqueue
TARGETS += net
TARGETS += openat
TARGETS += powerpc
TARGETS += ptrace
TARGETS += size
TARGETS += sysctl
TARGETS += timers
TARGETS += user
TARGETS += vm
#Please keep the TARGETS list alphabetically sorted

TARGETS_HOTPLUG = cpu-hotplug
TARGETS_HOTPLUG += memory-hotplug

# Clear LDFLAGS and MAKEFLAGS if called from main
# Makefile to avoid test build failures when test
# Makefile doesn't have explicit build rules.
ifeq (1,$(MAKELEVEL))
undefine LDFLAGS
override MAKEFLAGS =
endif

all:
	for TARGET in $(TARGETS); do \
		make -C $$TARGET; \
	done;

run_tests: all
	for TARGET in $(TARGETS); do \
		make -C $$TARGET run_tests; \
	done;

hotplug:
	for TARGET in $(TARGETS_HOTPLUG); do \
		make -C $$TARGET; \
	done;

run_hotplug: hotplug
	for TARGET in $(TARGETS_HOTPLUG); do \
		make -C $$TARGET run_full_test; \
	done;

clean_hotplug:
	for TARGET in $(TARGETS_HOTPLUG); do \
		make -C $$TARGET clean; \
	done;

clean:
	for TARGET in $(TARGETS); do \
		make -C $$TARGET clean; \
	done;
