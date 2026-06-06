# Data Center Cooling Infrastructure Management & Capacity Planning

![Cooling Systems](https://img.shields.io/badge/Domain-Cooling%20Infrastructure-blue)
![ASHRAE](https://img.shields.io/badge/Standard-ASHRAE%20TC%209.9-green)
![CRAC/CRAH](https://img.shields.io/badge/Focus-CRAC%20%26%20CRAH%20Systems-orange)
![Grafana](https://img.shields.io/badge/Monitoring-Thermal%20Dashboards-orange)
![Schneider DCCA](https://img.shields.io/badge/Cert-Schneider%20DCCA-green)
![Critical Infrastructure](https://img.shields.io/badge/Role-Critical%20Infrastructure-red)

---

## Project Overview

This project documents comprehensive data center cooling infrastructure management — covering CRAC/CRAH systems, chilled water design, hot/cold aisle containment, thermal monitoring, and capacity planning aligned with ASHRAE TC 9.9 thermal standards.

Built to demonstrate operational readiness for:
- ✅ Critical Infrastructure Engineer roles
- ✅ Data Center Operations Engineer roles
- ✅ Facilities Engineer roles
- ✅ Data Center Design Engineer roles

---

## Real World Foundation

This documentation is informed by hands-on operational experience managing:

- **Industrial cooling systems** in mission-critical production environments
- **Environmental monitoring** across server room and data center infrastructure
- **Temperature and humidity management** for production server environments
- **Preventive maintenance** of cooling infrastructure using operational data

---

## Repository Structure
---

## Cooling Architecture Overview

---

## ASHRAE Thermal Guidelines

### Recommended Environmental Ranges

| Parameter | ASHRAE A1 | ASHRAE A2 | ASHRAE A3 |
|---|---|---|---|
| Inlet Temperature | 15–32°C | 10–35°C | 5–40°C |
| Relative Humidity | 20–80% | 20–80% | -15°C DP to 80% |
| Max Dew Point | 17°C | 21°C | 24°C |
| Max Altitude | 1050m | 1050m | 1050m |

### Temperature Monitoring Thresholds

| Location | Normal | Warning | Critical |
|---|---|---|---|
| Server Inlet | 18–27°C | 27–32°C | Above 32°C |
| Server Outlet | 30–45°C | 45–50°C | Above 50°C |
| CRAC Return | 24–30°C | 30–35°C | Above 35°C |
| CRAC Supply | 16–18°C | 18–20°C | Above 20°C |
| Ambient | 20–24°C | 24–28°C | Above 28°C |

---

## Hot/Cold Aisle Containment

### Design Principles
←←←←←                    →→→→→

### Containment Benefits

| Benefit | Improvement |
|---|---|
| PUE Improvement | 0.1–0.2 reduction |
| Cooling Efficiency | 20–30% improvement |
| Capacity Increase | 15–25% more IT load |
| Energy Savings | 10–20% reduction |

---

## Cooling Load Calculations

### Calculation Methodology
### Example Calculation

---

## Capacity Planning Metrics

| Metric | Target | Warning | Critical |
|---|---|---|---|
| Cooling Utilization | Below 70% | 70–85% | Above 85% |
| CRAC Redundancy | N+1 minimum | N only | No redundancy |
| Temperature Headroom | Above 5°C | 3–5°C | Below 3°C |
| WUE Target | Below 1.5 | 1.5–2.0 | Above 2.0 |

---

## CRAC System Overview

### CRAC vs CRAH Comparison

| Feature | CRAC | CRAH |
|---|---|---|
| Full Name | Computer Room Air Conditioner | Computer Room Air Handler |
| Cooling Method | Direct expansion (DX) refrigerant | Chilled water coil |
| Best For | Smaller deployments | Large enterprise DC |
| Redundancy | Self-contained | Depends on chiller plant |
| Efficiency | Good | Better at scale |
| Typical Capacity | 5–50 kW | 20–200 kW |

### Key CRAC Maintenance Items

| Component | Check Frequency | Action |
|---|---|---|
| Air filters | Monthly | Clean or replace |
| Condensate drain | Monthly | Clear and test |
| Refrigerant level | Quarterly | Check and top up |
| Belt tension | Quarterly | Adjust if needed |
| Compressor | Annually | Full inspection |
| Coils | Annually | Clean and inspect |

---

## Water Usage Effectiveness (WUE)

### WUE Calculation

### WUE Reduction Strategies

| Strategy | WUE Reduction | Notes |
|---|---|---|
| Air-side economization | 30–50% | Climate dependent |
| Higher cooling tower cycles | 10–20% | Water treatment required |
| Closed loop systems | 20–40% | Higher capital cost |
| Waterless cooling | 100% | Air or liquid cooling |

---

## Cooling Failure Response Runbook

### Immediate Response (0–5 minutes)
1. Acknowledge cooling failure alert on dashboard
2. Identify which CRAC/CRAH unit has failed
3. Check inlet temperatures across all server aisles
4. Verify backup cooling unit status
5. Create P1 incident ticket immediately
6. Notify on-call supervisor

### Stabilization (5–15 minutes)
1. Activate backup CRAC unit if available
2. Increase fan speed on remaining units
3. Monitor temperature trends every 2 minutes
4. Implement emergency airflow procedures
5. Alert all stakeholders via communication plan
6. Contact cooling vendor emergency line

### Critical Temperature Actions

| Temperature | Action |
|---|---|
| Above 32°C inlet | Initiate graceful shutdown planning |
| Above 35°C inlet | Begin non-critical system shutdown |
| Above 40°C inlet | Emergency shutdown all systems |

### Resolution & Recovery
1. Coordinate vendor emergency repair
2. Test repaired unit before returning to service
3. Verify all temperatures return to normal range
4. Monitor for 30 minutes post-recovery
5. Complete post-incident review within 24 hours
6. Update maintenance schedule

---

## Grafana Thermal Dashboard Configuration

### Dashboard Panels

| Panel | Metric | Visualization |
|---|---|---|
| Inlet Temperature Map | Per rack inlet temp | Heat map |
| CRAC Supply/Return | CRAC temperatures | Time series |
| Temperature Trends | 24hr temperature history | Line graph |
| Humidity Levels | Room humidity % | Gauge |
| Cooling Capacity | % cooling utilized | Bar gauge |
| Alert Status | Active thermal alerts | Alert list |
| PUE Trend | Real-time PUE | Stat panel |

### Alert Configuration

```yaml
# Grafana Alert — High Inlet Temperature
alert:
  name: High Server Inlet Temperature
  conditions:
    - type: query
      query: avg(server_inlet_temp) > 30
      for: 5m
  notifications:
    - name: NOC On-Call
      type: pagerduty
  message: |
    Server inlet temperature exceeded 30°C
    Current value: {{ $value }}°C
    Location: {{ $labels.rack }}
    Immediate investigation required
```

---

## Standards & Frameworks Referenced

- **ASHRAE TC 9.9** — Thermal Guidelines for Data Processing Environments
- **The Green Grid** — WUE and PUE measurement standards
- **ANSI/TIA-942** — Data Center Infrastructure Standard
- **Uptime Institute** — Tier classification and availability
- **ISO/IEC 30134** — Data center resource efficiency metrics
- **BICSI 002** — Data Center Design and Implementation Best Practices

---

## Tools & Technologies

![Grafana](https://img.shields.io/badge/Grafana-Thermal%20Dashboards-orange)
![Prometheus](https://img.shields.io/badge/Prometheus-Environmental%20Metrics-orange)
![DCIM](https://img.shields.io/badge/DCIM-Cooling%20Management-blue)
![Schneider](https://img.shields.io/badge/Schneider-EcoStruxure-green)
![ASHRAE](https://img.shields.io/badge/ASHRAE-TC%209.9-green)
![Python](https://img.shields.io/badge/Python-Automation-blue)

---

## Author

**George Amankwaa Sarpong**
Critical Infrastructure Engineer | Data Center Cooling Systems
📍 Accra, Ghana
🔗 [LinkedIn](https://linkedin.com/in/georgesarpong)
🌐 [GitHub Portfolio](https://github.com/GeorgeSarpong)

---

*This project is part of a broader portfolio demonstrating readiness for Critical Infrastructure Engineer and Data Center Operations roles in the US and global market.*
