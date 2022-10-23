# ZabbixTemplateForGamingPC
Welcome to the ZabbixTemplateForGamingPC wiki!
# Summary

This is a Zabbix template designed for use on gaming PCs.
It is intended to work only on Windows PCs and NVIDA GPUs.

The following information is obtained and displayed on the graph.
* CPU Usage %
* GPU Usage %
* Network Traffic
* Memory Usage
* VRAM Usage
* Swap Usage
* GPU Power 
* GPU Temperature
* Disk IOPS (read/write rates)
* Disk average waiting time

# Installation

Zabbix Agent must be installed on the client side.
Also, the following user parameter must be added to zabbix_agentd.conf

UserParameter=gpu.temp,nvidia-smi --query-gpu=temperature.gpu --format=csv,noheader,nounits -i 0
UserParameter=gpu.memtotal,nvidia-smi --query-gpu=memory.total --format=csv,noheader,nounits -i 0
UserParameter=gpu.used,nvidia-smi --query-gpu=memory.used --format=csv,noheader,nounits -i 0
UserParameter=gpu.free,nvidia-smi --query-gpu=memory.free --format=csv,noheader,nounits -i 0
UserParameter=gpu.fanspeed,nvidia-smi --query-gpu=fan.speed --format=csv,noheader,nounits -i 0
UserParameter=gpu.utilisation,nvidia-smi --query-gpu=utilization.gpu --format=csv,noheader,nounits -i 0
UserParameter=gpu.power,nvidia-smi --query-gpu=power.draw --format=csv,noheader,nounits -i 0

The retention period for history is 90 days.
Change it according to the disk space of your Zabbix server.



