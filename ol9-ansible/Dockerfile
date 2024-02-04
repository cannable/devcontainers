FROM oraclelinux:9

ENV DC_USER_UID=1000
ENV DC_USER_GID=1000
ENV DC_USER_USERNAME=user
ENV DC_USER_GROUPNAME=user

# Install pre-reqs
RUN dnf -y install \
  git \
  python-pip \
  sudo \
  && pip install \
  ansible-core \
  ansible-lint \
  hvac \
  && groupadd -g "$DC_USER_GID" \
  "${DC_USER_GROUPNAME}" \
  && useradd -m \
    -u "$DC_USER_UID" \
    -g "$DC_USER_GROUPNAME" \
    -G "$DC_USER_GROUPNAME" \
    "${DC_USER_USERNAME}" \
  && echo "${DC_USER_USERNAME} ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/10-container

USER "${DC_USER_USERNAME}"
ENTRYPOINT ["/bin/bash"]