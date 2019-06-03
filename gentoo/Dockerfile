# Use the empty image with the portage tree as the first stage
FROM gentoo/portage:latest as portage

# Gentoo stage3 is the second stage, basically an unpacked Gentoo Linux
FROM gentoo/stage3-amd64:latest as gentoo

# Copy the portage tree into the current stage
COPY --from=portage /usr/portage /usr/portage

MAINTAINER alicef@gentoo.org

RUN mkdir /etc/portage/package.keywords
RUN printf "dev-lang/python sqlite" > /etc/portage/package.use/python
RUN printf "sys-apps/elivepatch-server ~amd64\nsys-kernel/kpatch ~amd64\napp-crypt/pesign ~amd64" > /etc/portage/package.keywords/elivepatch

RUN emerge --sync
RUN ROOT=/destination emerge -qv sys-kernel/kpatch
RUN ROOT=/destination emerge -qv sys-apps/elivepatch-server
