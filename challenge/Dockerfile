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
FROM tomcat:latest

#Create a directory and coping files - to show the API of the tomcat
RUN mkdir -p /usr/local/tomcat/webapps/ROOT
RUN cp -R /usr/local/tomcat/webapps.dist/docs/* /usr/local/tomcat/webapps/ROOT/

# Set the /usr/local/tomcat directory as a volume
VOLUME /usr/local/tomcat

# Start Tomcat
CMD ["catalina.sh", "run"]