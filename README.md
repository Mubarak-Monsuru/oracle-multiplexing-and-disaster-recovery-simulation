# Oracle 19c Enterprise Disaster Recovery & Multiplexing Simulation

## 📋 Project Overview
This project simulates an enterprise-grade database disaster recovery, storage redundancy, and multiplexing architecture using **Oracle Database 19c Enterprise Edition** on Oracle Linux. The core focus is eliminating Single Points of Failure (SPOF) by separating storage across physical disks (`/u02` and `/u03`), implementing robust RMAN backup hierarchies (Level 0 and Level 1), executing complex disaster simulations including Point-In-Time Recovery (PITR) and control file restoration, and configuring Automatic Storage Management (ASM).

---

## 1. 🎯 Project Objectives
◆ **Eliminate Single Points of Failure (SPOF):** Prove how disk multiplexing across separate block devices protects critical database control files and redo logs from hardware loss.

◆ **Master Enterprise Backup & Recovery:** Implement RMAN backup strategies and execute precise recovery workflows.

◆ **Simulate Real-World Disasters:** Handle missing storage paths, unmounted disks, missing control files, and perform precise Point-In-Time Recovery (PITR).

◆ **Explore Advanced Storage:** Transition from standard file system architectures to Oracle Automatic Storage Management (ASM).

---

## 2. ✅ **Key Concepts Covered**
◆ **Storage Redundancy & Multiplexing:** Mirroring online redo log members and control files across separate physical disks (`/u02` and `/u03`).

◆ **Database Operating Modes:** Transitioning from `NOARCHIVELOG` to `ARCHIVELOG` mode alongside Fast Recovery Area (FRA) configuration and sizing.

◆ **RMAN Backup Hierarchies:** Establishing common users, configuring backup permissions, and capturing incremental backups (Level 0 full baseline and Level 1 differential/cumulative).

◆ **Recovery Operations:** Using System Change Number (SCN) targets for Point-In-Time Recovery (PITR) and restoring lost control files.

◆ **Automatic Storage Management (ASM):** Provisioning and organizing ASM disk groups for enterprise storage virtualization.

---

## 3. 🗺️ Project Phases & Implementation Steps

### Phase 1: Storage Architecture & Expansion
* Attaching a secondary virtual hard disk and mounting it at `/u03`.
* Designing a multi-disk storage layout to separate data files, redo logs, and recovery areas to prevent SPOFs.

### Phase 2: Logging & Recovery Foundations
* Enabling `ARCHIVELOG` mode and configuring the Fast Recovery Area (FRA) path and size.
* Dropping existing redo logs and creating multiplexed redo log groups across separate physical disks.
* Multiplexing archive log destinations.

### Phase 3: Data Simulation & RMAN Backups
* Creating a test table on `PDB2` and executing initial transactional DML inserts.
* Creating a dedicated common user to manage backups and taking a Level 0 baseline backup (database + archive logs).
* Performing secondary DML changes and capturing a Level 1 incremental backup.

### Phase 4: Disaster Simulation & Advanced Recovery
* Simulating physical storage failure by committing transactions and unmounting the `/u03` disk.
* Performing a Point-In-Time Recovery (PITR) to restore data back to a precise target SCN.
* Simulating control file loss, remounting `/u03`, and executing control file recovery.

### Phase 5: Modern Storage Virtualization
* Provisioning and configuring Oracle Automatic Storage Management (ASM) storage pools.

---

## 📦 Project Deliverables
* **GitHub Repository Documentation:** A professional technical README documenting each architecture phase, command outputs, and validation queries.
* **RMAN Recovery Playbook:** Step-by-step scripts and notes covering Level 0/Level 1 backups, PITR, and control file restoration workflows.
* **Disaster Simulation Log:** A record of failure simulations (unmounting `/u03`, dropping control files) and the exact recovery syntax used to restore service.
* **ASM Configuration Report:** Summary notes and validation checks from implementing ASM storage management.