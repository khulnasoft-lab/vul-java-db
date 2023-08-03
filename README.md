# vul-java-db

## Overview
`vul-java-db` parses all indexes from [maven repository](https://repo.maven.apache.org/maven2) and stores `ArtifactID`, `GroupID`, `Version` and `sha1` for jar files to SQlite DB.

The DB is used in Vul to discover information about `jars` without GAV inside them.

## Update interval
Every Thursday in 00:00

## Download the java indexes database
You can download the actual compiled database via [Vul](https://khulnasoft-labs.github.io/vul/) or [Oras CLI](https://oras.land/cli/).

Vul:
```sh
TRIVY_TEMP_DIR=$(mktemp -d)
vul --cache-dir $TRIVY_TEMP_DIR image --download-java-db-only
tar -cf ./javadb.tar.gz -C $TRIVY_TEMP_DIR/java-db metadata.json vul-java.db
rm -rf $TRIVY_TEMP_DIR
```

oras >= v0.13.0:
```sh
$ oras pull ghcr.io/khulnasoft-labs/vul-java-db:1
```

oras < v0.13.0:
```sh
$ oras pull -a ghcr.io/khulnasoft-labs/vul-java-db:1
```
The database can be used for [Air-Gapped Environment](https://khulnasoft-labs.github.io/vul/latest/docs/advanced/air-gap/).
