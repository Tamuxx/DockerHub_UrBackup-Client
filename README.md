# UrBackup-Client1

This Alpine Linux container mount an local directory into /data and de UrBackup client service. 

From the UrBackup server set /data in "Default Directories to Backup".

## yml example:

    version: '3.5'

    services:
      urbackup_cliente_srv1:
      image: tamuxx/urbackup_client
      container_name: srv1_urclient
      restart: unless-stopped
      cap_add:
         - ALL
      hostname: SRV1
      volumes:
        - /data/to/backup/:/data
      networks:
        backup_bridge:
           ipv4_address: 10.221.0.10
    networks:
      backup_bridge:
      name: docker2
      driver: bridge
      ipam:
        config:
          - subnet: 10.221.0.0/16
        driver_opts:
          com.docker.network.bridge.name: docker2

