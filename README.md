# 🛠️ Industrial IoT Honeypot & Threat Enrichment Pipeline

Simulate an industrial control system (ICS) environment and track malicious activity using a Modbus honeypot, threat detection, enrichment, and full-stack visualization — all containerized and powered by open-source tech.

---

## 📡 Project Overview

This project deploys a fake ICS device using **Conpot** to lure attackers and simulate vulnerabilities on port 502 (Modbus). Logs are captured using **Suricata**, enriched using **Logstash** with **GeoIP** and **AbuseIPDB**, stored in **Elasticsearch**, and visualized in **Kibana**.

---

## 🧱 Stack Components

| Component        | Role                                                       |
|------------------|------------------------------------------------------------|
| `Conpot`         | ICS honeypot emulating Modbus-based devices                |
| `Suricata`       | Intrusion detection system (writes logs to `eve.json`)     |
| `Logstash`       | Parses + enriches logs (GeoIP, threat intelligence, tags) |
| `Elasticsearch`  | Log storage and search                                     |
| `Kibana`         | Real-time data visualization and dashboards                |

---

## 🔁 Data Flow

1. Attacker connects to honeypot (Modbus TCP port `502`)
2. Suricata logs the network event to `eve.json`
3. Logstash watches `eve.json`, enriches with:
   - IP metadata
   - GeoIP data
   - AbuseIPDB threat score
4. Output is pushed to Elasticsearch
5. Kibana displays data with threat dashboards

---

## 🔍 Enrichment Logic

**Logstash tags logs with:**
- `threat_match` if `abuseConfidenceScore > 50`
- Adds fields: `threat_score`, `geoip.location`, `asn.organization`, etc.

---

# 🛠️ Industrial IoT Honeypot & Threat Enrichment Pipeline

Simulate an industrial control system (ICS) environment and track malicious activity using a Modbus honeypot, threat detection, enrichment, and full-stack visualization — all containerized and powered by open-source tech.

---

## 📡 Project Overview

This project deploys a fake ICS device using **Conpot** to lure attackers and simulate vulnerabilities on port 502 (Modbus). Logs are captured using **Suricata**, enriched using **Logstash** with **GeoIP** and **AbuseIPDB**, stored in **Elasticsearch**, and visualized in **Kibana**.

---

## 🧱 Stack Components

| Component        | Role                                                       |
|------------------|------------------------------------------------------------|
| `Conpot`         | ICS honeypot emulating Modbus-based devices                |
| `Suricata`       | Intrusion detection system (writes logs to `eve.json`)     |
| `Logstash`       | Parses + enriches logs (GeoIP, threat intelligence, tags) |
| `Elasticsearch`  | Log storage and search                                     |
| `Kibana`         | Real-time data visualization and dashboards                |

---

## 🔁 Data Flow

1. Attacker connects to honeypot (Modbus TCP port `502`)
2. Suricata logs the network event to `eve.json`
3. Logstash watches `eve.json`, enriches with:
   - IP metadata
   - GeoIP data
   - AbuseIPDB threat score
4. Output is pushed to Elasticsearch
5. Kibana displays data with threat dashboards

---

## 🔍 Enrichment Logic

**Logstash tags logs with:**
- `threat_match` if `abuseConfidenceScore > 50`
- Adds fields: `threat_score`, `geoip.location`, `asn.organization`, etc.

---

## 📂 Folder Structure

iot-honeypot-project/ ├── docker-compose.yml ├── suricata/ │   └── eve.json ├── logstash/ │   ├── pipeline/ │   │   └── logstash.conf │   └── geoip/ ├── testmodbus.csv

