| **Comandos**                                   | **Descripción**                                      |
| ---------------------------------------------- | ---------------------------------------------------- |
| **[lab][lab-docs]**                            |                                                      |
| `/usr/local/etc/wake lab102-204 -y`            | Enciende una máquina del laboratorio de forma remota |
| `/usr/local/etc/shutdown.sh -y lab102-204`     | Apaga una máquina del laboratorio de forma remota    |
| **[virsh][virsh-docs]**                        |                                                      |
| `virsh --help`                                 | Muestra los comandos agrupados                       |
| `virsh <command> --help`                       | Muestra la ayuda de un comando                       |
| `virsh -c qemu+ssh://${USER}@${TARGET}/system` | Connecta con la URI de conexión al hipervisor        |
| `virsh -c ${URI} start <domain>`               | Inicia un dominio                                    |
| `virsh -c ${URI} reboot <domain>`              | Reinicia un dominio                                  |
| `virsh -c ${URI} shutdown <domain>`            | Apaga un dominio                                     |
| `virsh -c ${URI} list [...options]`            | Lista de dominios [...filtros]                       |
| `virsh -c ${URI} list --all`                   | Lista de dominios inactivos y activos                |
| `virsh -c ${URI} list --state-running`         | Lista de dominios en estado de ejecución             |

[lab-docs]: http://webdiis.unizar.es/~chus/docencia/trabajo_remoto/trabajo_remoto.html
[virsh-docs]: https://access.redhat.com/documentation/es-es/red_hat_enterprise_linux/5/html/virtualization/ch-virt-task-virsh

```
virsh -c qemu+ssh://a798095@155.210.154.204/system start router7
```
