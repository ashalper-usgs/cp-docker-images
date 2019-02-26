#
# Copyright 2018 Confluent Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

FROM confluentinc/cp-kafka-connect:5.1.2

ENV CONNECT_PLUGIN_PATH="/usr/share/java,/usr/share/confluent-hub-components"

RUN confluent-hub install --no-prompt confluentinc/kafka-connect-datagen:latest

# install jq
RUN apt-get update && apt-get install -y jq && apt-get clean

# Copy the Apache assembly. It would be nice to not have to maintain a separate copy
# of the archive file in this directory for Docker, but soft-linking doesn't seem to work.
#
# See also:
#
# https://stackoverflow.com/questions/46309423/dockerfile-copy-from-a-windows-file-system-to-a-docker-container
COPY kafka-connect-waterservices-1.0-SNAPSHOT.tar.gz /

# install the assembly
RUN cd / && tar -xzf kafka-connect-waterservices-1.0-SNAPSHOT.tar.gz && rm -f kafka-connect-waterservices-1.0-SNAPSHOT.tar.gz
