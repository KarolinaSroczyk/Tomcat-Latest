# Copyright 2020 Google LLC
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     https://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
FROM tomcat:latest as chroot

# Set up your Tomcat environment
RUN /usr/sbin/useradd --no-create-home -u 1000 user

#Create a directory and coping files - to show the API of the tomcat
RUN mkdir -p /usr/local/tomcat/webapps/ROOT
RUN mkdir -p /home/user
RUN cp -R /usr/local/tomcat/webapps.dist/docs/* /usr/local/tomcat/webapps/ROOT/

# Switch to the nsjail image
FROM gcr.io/kctf-docker/challenge@sha256:0f7d757bcda470c3bbc063606335b915e03795d72ba1d8fdb6f0f9ff3757364f

# Copy the chroot environment from the first stage
COPY --from=chroot / /chroot

# Set ownership for the user
RUN chown -Rc user /chroot/home/user

# Declare a volume
VOLUME /usr/local/tomcat
VOLUME /chroot/home/user/

# Start Tomcat
CMD ["catalina.sh", "run"]
