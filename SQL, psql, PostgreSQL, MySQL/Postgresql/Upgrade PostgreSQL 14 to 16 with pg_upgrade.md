

![Maly Mohsem Ahmed](https://miro.medium.com/v2/resize:fill:88:88/1*DgGQTJpkBliQiWDu6m0VnQ.jpeg)

### [Say Goodbye to Downtime Upgrade PostgreSQL 14 to 16 Effortlessly with pg_upgrade by Maly Mohsem Ahmed Feb, 2024 Medium](https://medium.com/@malymohsem/say-goodbye-to-downtime-upgrade-postgresql-14-to-16-effortlessly-with-pg-upgrade-42ef4dbf8524)

## Table of contents

-   [What’s waiting for you in PostgreSQL 16?](https://malymohsemahmed.hashnode.dev/say-goodbye-to-downtime-upgrade-postgresql-14-to-16-effortlessly-with-pgupgrade#heading-whats-waiting-for-you-in-postgresql-16)
-   [Getting Started](https://malymohsemahmed.hashnode.dev/say-goodbye-to-downtime-upgrade-postgresql-14-to-16-effortlessly-with-pgupgrade#heading-getting-started)
-   [For Debian/Ubuntu](https://malymohsemahmed.hashnode.dev/say-goodbye-to-downtime-upgrade-postgresql-14-to-16-effortlessly-with-pgupgrade#heading-for-debianubuntu)
-   [For `RHEL/AlmaLinux/RockyLinux`](https://malymohsemahmed.hashnode.dev/say-goodbye-to-downtime-upgrade-postgresql-14-to-16-effortlessly-with-pgupgrade#heading-for-rhelalmalinuxrockylinux)

![](https://miro.medium.com/v2/resize:fit:1083/1*3DQJVPc6bpuBWS540m1xSg.png)

Tired of juggling database upgrades with downtime stress? Fear not, fellow devs! This blog post unveils the secret weapon in your arsenal: a seamless transition From PostgreSQL 14 to PostgreSQL 16 using the mighty pg\_upgrade utility. Buckle up, because we’re about to turbocharge your database without missing a single line of code.

Say goodbye to the days of:

-   Scrambling users with downtime notices.
-   Juggling database backups like a circus performer.
-   Sweating the upgrade process, and praying for data integrity.

With **pg\_upgrade** by your side, you can smoothly glide from **PostgreSQL 14 to 16** while your database hums happily along. We’re talking zero downtime, zero headaches, and zero compromises. Just pure, unadulterated database bliss.

## What’s waiting for you in PostgreSQL 16?

-   **Performance boost:** Witness your queries light up the speedway with improved indexing and execution plans.
-   **Enhanced security:** Rest easy knowing your precious data is shielded by tighter access controls and encryption options.
-   **New features galore:** Dive into a treasure trove of fresh functionalities, from parallel query execution to improved replication, ready to unlock new possibilities for your apps.

## Getting Started

## For Debian/Ubuntu

_Step 1: Welcoming PostgreSQL 16_

Start by installing the shining star of our show, PostgreSQL 16. Let the magic unfold!

```
# Create the file repository configuration:  
sudo sh -c 'echo "deb https://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'  
  
# Import the repository signing key:  
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo tee /etc/apt/trusted.gpg.d/apt.postgresql.org.gpg
  
# Update the package lists:  
sudo apt-get update  
  
# Install the latest version of PostgreSQL.  
# If you want a specific version, use 'postgresql-12' or similar instead of 'postgresql':  
sudo apt-get -y install postgresql-16
```

_Step 2: Checking Your Database Clusters_

Verify that your server now proudly hosts both PostgreSQL 14 and PostgreSQL 16 using the `pg_lsclusters` command.

```
sudo pg_lsclusters
```

_Step 3: Preparing for the Upgrade_

Stop the PostgreSQL 16 cluster to prepare for the upgrade.

```
sudo pg_dropcluster 16 main --stop
```

_Step 4: Initiating the Upgrade Process_

Start the upgrade process by executing the following command:

```
sudo pg_upgradecluster 14 main
```

Monitor the process, and upon success, confidently remove the older version.

```
sudo pg_dropcluster 14 main
```

_Step 5: Final Touch — Removing the Old Package_

Clean up the remnants of PostgreSQL 14 by purging the old package.

```
sudo apt purge postgresql-14 postgresql-client-14
```

_Step 6: Verification — Ensuring a Successful Upgrade_

Double-check your current clusters to confirm the successful upgrade.

```
sudo pg_lsclusters
```

## For RHEL/AlmaLinux/RockyLinux

_Step 1: Checking the Digital Skies_

Kick off your journey by ensuring a smooth connection to the digital cosmos. Ping the stars and make sure your database adventure is ready for liftoff.

```
ping google.com
```

_Step 2: Capturing the Cosmic Essence — Database Backup_

Preserve the essence of your data by creating a celestial backup using the powerful `pg_dumpall` command.

```
sudo su - postgres
pg_dumpall > /path/to/backup/all.sql
exit
```

_Step 3: Unveiling the Future — PostgreSQL 16 Emerges_

Introduce the star of our cosmic show — PostgreSQL 16! Witness its rise as we set the stage for its magnificent debut.

```
# Initialize cluster  
sudo su  
yum install postgresql16-server postgresql16  
/usr/pgsql-16/bin/postgresql-16-setup initdb  
  
# Modify port from 5432 to 5433  
sudo su - postgres  
vim /var/lib/pgsql/16/data/postgresql.conf  
  
# Start   
sudo systemctl start postgresql-16
```

_Step 4: The Grand Cosmic Transformation_ — `pg_upgrade` _Symphony_

The highlight of our celestial performance — the magnificent `pg_upgrade` utility! Experience the seamless transition from version 14 to the cosmic PostgreSQL 16.

```
/usr/pgsql-16/bin/pg_upgrade \  
  -b /usr/pgsql-14/bin/ \  
  -B /usr/pgsql-16/bin/ \  
  -d /var/lib/pgsql/14/data/ \  
  -D /var/lib/pgsql/16/data/ \  
  -o ' -c config_file=/var/lib/pgsql/14/data/postgresql.conf' \  
  -O ' -c config_file=/var/lib/pgsql/16/data/postgresql.conf'
```

_Step 5: Celestial Harmony_ — `pg_hba.conf` _Choreography_

Adjust the cosmic dance steps in `pg_hba.conf` the new data directory for perfect synchronization of old and new celestial moves.

_Step 6: Galactic Applause! PostgreSQL 16 Takes the Stage_

Initiate the standing ovation for PostgreSQL 16. Let the applause echo through your server environment.

```
sudo systemctl start postgresql-16
```

_Step 7: The Cosmic Encore — Verifying the Galactic Upgrade_

Ensure PostgreSQL 16 basks in the cosmic spotlight.

```
bashCopy codesudo systemctl status postgresql-16
```

_Step 8: Interstellar Connection — Testing Database Connections_

Step into the interstellar world by testing your database connections with cosmic flair.

```
psql -h localhost -p 5433 -U your_username -d your_database
```

_Step 9: Curtain Call — Clearing the Galactic Stage_

As the final act unfolds, gracefully remove the older PostgreSQL version to make way for the cosmic era.

```
sudo su  
yum remove postgresql14-server postgresql14
```

But the best part? You can enjoy this upgrade feast without sacrificing uptime. It’s like the ultimate database buffet served while you keep crunching code. Delicious!

Hungry for more? This blog post will be your map to upgrade Nirvana. We’ll navigate the process step-by-step, from initial prep to post-upgrade verification, ensuring you arrive at your destination — a sleek, powerful PostgreSQL 16 database, ready to propel your projects to new heights.

So, fellow developers, ditch the downtime drama and embrace the pg\_upgrade revolution. Join us on this exciting journey to unleash the full potential of PostgreSQL 16, all while your users bask in uninterrupted database sunshine.