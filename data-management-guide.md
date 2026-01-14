---
title: Data Management Guidelines
slug: data-management
post_status: future
post_type: page
---

These guidelines supplement and strictly adhere to the **Charles University (CU) Research Data Policy** (adopted 2024), ensuring all data generated within the facility are managed in line with the **FAIR principles** (Findable, Accessible, Interoperable, Reusable).

---

## 1. Responsibilities and Ownership

### Institutional Mandate
The Facility operates in accordance with the [CU Research Data Policy](https://cuni.cz/UKEN-1958.html). Users must manage their research data to ensure transparency, reproducibility, and compliance with the CU Code of Ethics and **GDPR**.

### Data Ownership
The **User/Principal Investigator (PI)** of the research project is the data owner by default, unless specific agreements (e.g., consortium contracts) state otherwise.

### Long-Term Preservation
Determining and adhering to the **mandatory data retention period** (which varies by funder, discipline, and national law) is the **sole responsibility of the User/PI**. The facility directs users to the Faculty Data Steward for best practice consultation.

---

## 2. Active Data Storage and Retention

The Facility provides temporary, secure storage for active experiments only. It is the User's responsibility to transfer data to long-term storage within the retention window.

For detailed information, you can refer to our Storage Guidelines.

### Immediate Storage
Immediately after acquisition, data are temporarily stored on the **Local Network Attached Storage (NAS)**, utilizing **RAID 5** for fault tolerance. This storage is secured but is **not intended for long-term data preservation**.

### Access Control
Access to the NAS, software, and analysis hardware is secured via the **Faculty/CU authentication system (CAS)**. Authorized external/commercial users are provided with secure credentials.

### Data Retention Window
* Data are stored for a maximum of **3 months (90 days)** from the date of acquisition.
* Users are responsible for transferring their data within this period.
* **Important:** Data remaining on the NAS after 90 days will be deleted without further notice.

---

## 3. Data Transfer and Long-Term Preservation

### Recommended Transfer Methods
* **Local Network Transfer:** Use secure local network options.
* **CU/CESNET Cloud:** Use services like CESNET ownCloud or CESNET storage.
* **Disk Media:** The use of personal Flash Drives or USB external hard drives is **strongly discouraged** to ensure secure and auditable transfers.

### GDPR and Personal Data
Research data containing **personal data** (e.g., human-derived images) must be anonymized or pseudonymized before transfer. Transfers of personal data must be conducted via secure, encrypted methods. The use of unencrypted flash drives for personal data is **strictly prohibited**.

### Long-Term Storage
Since CU/Faculty do not provide a centralized institutional repository for final research data, the **User/PI must arrange long-term preservation**. Common routes include:
* **CESNET** (through negotiation).
* **User-specific storages**.
* All preservation must align with the User’s **Data Management Plan (DMP)**.

---

## 4. Metadata and Open Science Support

### Metadata Collection
Key experimental metadata—including Instrument used, imaging parameters, objective, and sample name—are specified during initial consultation and experiment setup.

### Metadata Storage
Key metadata is typically **stored within the image data file format itself**. Users are encouraged to verify this and utilize **OMERO file formats** (Open Microscopy Environment) for organized annotation and metadata enrichment, enhancing data Findability.

### DMP and Consultation
The Faculty provides access to the **FAIR Wizard** for creating DMPs. The Facility also offers consultation on:
* BioImage Analysis services.
* Data publication and scripts.
* Reproducible data analysis workflow publication.

---

## 5. Faculty Data Steward Contact

For consultation regarding research data management, creating a Data Management Plan (DMP), and compliance with the CU Research Data Policy, please contact the Faculty Data Steward:

* **Name:** Jiri Grulich, Data Steward
* **Department:** Research Support Department
* **Email:** jiri.grulich@natur.cuni.cz
* **Phone:** +420 221 95 1259
* **Office:** Albertov 6, 4NP, room 312