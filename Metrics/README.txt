# Boomi Otel Setup

Follow these instructions to set up Apica Monitoring for a Boomi Atom

## Extract the Apica-Boomi.zip archive

## Check you have all the files

-opentelemetry-javaagent.yaml
-atom.vmoptions
-opentelemetry-javaagent.jar
-opentelemetry-jmx-metrics.jar
-README.md
-apica-otel-darwin_amd64
-apica-otel-linux_amd64
-otelcol-linux.yaml

## Overview
 
 1. Download the latest Otel Collector Release:
        - https://github.com/open-telemetry/opentelemetry-collector-contrib/releases 

 1. Find the correct OpenTelemetry collector yaml file
        - Linux/Mac with JMX - otelcol-linux.yaml

 2. Replace the atom.vmoptions file in your boomi bin folder /Boomi_AtomSphere/Atom/{Your_Atom_Name}/bin
         -Update the file path for javaagent & Dotel.jmx.config, explained in step #3

 3. Using JAR files
    - opentelemetry-javaagent.jar - use the path for this as REPLACE_PATH_TO_AGENT in the atom.vmoptions file
    - opentelemetry-jmx-metrics.jar - use the path for this as REPLACE_PATH_TO_JMX_METRICS_JAR

 4. Update the otelcol-linux.yaml 
        -Authorization Token -> You can find this token in the portal -> top right user icon -> License -> Account - Ingest Token 
        -Machine_Name -> Replace this with the name of your machine. This will help later when IDing the metrics.

 5. Use the apropriate OpenTelemetry collector binary for you platform linux, windows, darwin (macosx)
        - apica-otel-windows_amd64.exe , apica-otel-linux_amd64, apica-otel-darwin_amd64
        - Ex Linux:  ./apica-otel-linux_amd64 --config PATH_TO_OTEL_CONFIG_FILE

 6. curl http://0.0.0.0:9464/metrics to see all the metrics that are being exposed and *should* be being pushed to ADF if configured correctly.

 7. Take one of those metrics and search for it in ADF under:
       Queries -> ... Actions (top right) -> New Query -> Left side dropdown -> Otel Metrics -> Find metric and hit Execute -> Look for your machine name
 

 