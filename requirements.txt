from monitor.cpu import get_cpu_usage
from monitor.memory import get_memory_usage
from monitor.disk import get_disk_usage
from monitor.alerts import check_alerts
from utils.logger import log_data
import time

INTERVAL = 2  # seconds

def run_monitor():
    while True:
        cpu = get_cpu_usage()
        memory = get_memory_usage()
        disk = get_disk_usage()

        print(f"CPU: {cpu}% | Memory: {memory}% | Disk: {disk}%")

        log_data(cpu, memory, disk)
        check_alerts(cpu, memory, disk)

        time.sleep(INTERVAL)

if __name__ == "__main__":
    run_monitor()
