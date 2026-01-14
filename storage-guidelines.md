---
title: Storage Guidelines
slug: storage-guidelines
post_status: future
post_type: page
---

## 1. Raw Data Lifecycle & NAS Storage
All data acquired on facility microscopes are initially saved to the local **NAS (Network Attached Storage)**.

* **Temporary Nature:** The NAS is a transition zone, not an archive.
* Data will be automatically deleted after **[Insert Number]** days.
* **Transfer Responsibility:** Users must move their raw data to a permanent storage solution before the expiration period.
* **Data Integrity:** We recommend verifying the checksum or file size after transfer to ensure no corruption occurred during the move.

---

## 2. BioImage Analysis & Scripts
For users requiring high-performance computing, data can be copied to the **BioImage Analysis servers**.

> [!WARNING]
> Data on Analysis servers are **NOT** backed up. These volumes are intended for processing only. Once analysis is complete, results must be moved to your primary storage or archive.

### Version Control (GitHub)
To ensure the reproducibility of your research, the facility supports the setup of **GitHub** via **GitHub Desktop**. We can assist you in:
* Connecting your local analysis folders to a GitHub repository.
* Backing up **scripts (.py, .ijm, .m)**, **pipelines (.cppipe)**, and **text-based metadata**.
* Managing version history for your custom analysis workflows.

---

## 3. Long-term Archiving & Repositories
The following table provides an overview of recommended repositories for your microscopy data. The facility staff is available to help you with **metadata preparation** and **data formatting** (e.g., converting to OME-TIFF or ZARR) to meet repository standards.

| Repository | Max Storage | Max Files | DOI Provided | Licenses | Embargo |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Zenodo** | 50 GB / upload* | 100 per record | Yes | Wide range (CC-BY, MIT, etc.) | Yes |
| **BioImage Archive** | No strict limit (TB+) | High | Yes (Accession #) | CC0, CC-BY | Yes |
| **CESNET Storage** | 2+ TB (standard) | High | No | User-defined | N/A (Private) |
| **CzechBioImaging** | In Development | TBD | Expected | TBD | TBD |
| **Personal (Flash/HDD)** | Device limit | N/A | No | None | No |

*\*Note: Zenodo quotas can be increased upon request for specific projects.*

---

## 4. Practical Steps for Users
* **Acquisition:** Save experiment data to the NAS in a folder named `YYYY-MM-DD_ProjectName_Surname`.
* **Immediate Backup:** Copy raw data to your **CESNET** storage or departmental server within 48 hours.
* **Analysis:** If using the Analysis Server, pull data from your backup, process it, and push the results/scripts back to your archive or **GitHub**.
* **Publication:** Prepare a subset of "Representative Data" or the full "Raw Dataset" for **Zenodo** or **BioImage Archive** to satisfy journal requirements or to archive it.

These guidelines establish the standard procedures for data management within the Microscopy Core Facility. Following the Charles University Research Data Policy (2024), the responsibility for data preservation and management lies solely with the data producer/owner (Principal Investigator or student). The facility provides the infrastructure for acquisition and short-term handling, but long-term archival is the user's duty.