# DockerHub_UrBackup-Client

  version: '3.5'

services:
  urbackup_cliente_srv1:
    image: sades_urbackup_client:1.0
    container_name: srv1_urclient
    restart: unless-stopped
    cap_add:
       - ALL
    hostname: SRV1
    volumes:
       - /var/lib/docker/volumes/:/data

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

