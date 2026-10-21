<div align="center">

# 🖥️ NOMBRE-DEL-PROYECTO

### Administración de sistemas, redes y mucho café ☕

![ASIR](https://img.shields.io/badge/CFGS-ASIR-blue?style=for-the-badge)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white)
![Estado](https://img.shields.io/badge/estado-en%20desarrollo-orange?style=for-the-badge)
![Licencia](https://img.shields.io/badge/licencia-MIT-green?style=for-the-badge)

*Proyecto realizado durante 2º de ASIR · Curso 2026/2027*

</div>

---

## 📑 Índice

- [📖 Sobre el proyecto](#-sobre-el-proyecto)
- [🎯 Objetivos](#-objetivos)
- [🛠️ Tecnologías](#️-tecnologías)
- [🗺️ Topología / Arquitectura](#️-topología--arquitectura)
- [📂 Estructura del repositorio](#-estructura-del-repositorio)
- [⚙️ Requisitos previos](#️-requisitos-previos)
- [🚀 Instalación y despliegue](#-instalación-y-despliegue)
- [💻 Uso](#-uso)
- [📸 Capturas](#-capturas)
- [🧠 Lo que he aprendido](#-lo-que-he-aprendido)
- [🔐 Seguridad](#-seguridad)
- [🗓️ Roadmap](#️-roadmap)
- [👤 Autor](#-autor)

---

## 📖 Sobre el proyecto

Aquí va una descripción corta y clara de qué hace tu proyecto. Por ejemplo:

> Despliegue automatizado de una infraestructura de servicios en red (DNS, DHCP, web y base de datos) sobre Linux, usando scripts en Bash y contenedores Docker, como parte del módulo de **Administración de Sistemas Operativos / Servicios de Red e Internet**.

**¿Por qué existe este repo?**
Porque hacer las cosas a mano una vez está bien para aprender, pero hacerlas veinte veces es de masocas. Aquí está todo documentado y automatizado. 😎

---

## 🎯 Objetivos

- [x] Montar el entorno base (VMs / contenedores)
- [x] Configurar los servicios de red principales
- [ ] Automatizar el despliegue con scripts
- [ ] Añadir monitorización
- [ ] Documentar todo para que otra persona lo pueda replicar

---

## 🛠️ Tecnologías

| Categoría | Herramientas |
|-----------|--------------|
| 🐧 Sistemas operativos | Debian 12 · Ubuntu Server · Windows Server 2022 |
| 🌐 Servicios de red | Bind9 (DNS) · isc-dhcp-server · Apache / Nginx · OpenSSH |
| 🗄️ Bases de datos | MariaDB · MySQL |
| 📦 Virtualización | VirtualBox · VMware · Proxmox · Docker · Docker Compose |
| 📜 Scripting | Bash · PowerShell |
| 🔒 Seguridad | UFW · iptables · Fail2ban · certificados SSL/TLS |
| 📊 Monitorización | Zabbix · Grafana · Prometheus |
| 🔧 Otros | Git · GitHub · VS Code · Wireshark |

*(Borra lo que no uses, que no cuela.)*

---

## 🗺️ Topología / Arquitectura

```text
                    ┌──────────────┐
                    │   Internet   │
                    └──────┬───────┘
                           │
                    ┌──────┴───────┐
                    │   Router /   │
                    │   Firewall   │
                    └──────┬───────┘
                           │  192.168.10.0/24
        ┌──────────────────┼──────────────────┐
        │                  │                  │
 ┌──────┴──────┐    ┌──────┴──────┐    ┌──────┴──────┐
 │ srv-dns     │    │ srv-web     │    │ srv-db      │
 │ 192.168.10.2│    │192.168.10.3 │    │192.168.10.4 │
 └─────────────┘    └─────────────┘    └─────────────┘
```

| Equipo | SO | IP | Función |
|--------|----|----|---------|
| `srv-dns` | Debian 12 | 192.168.10.2 | DNS + DHCP |
| `srv-web` | Ubuntu Server | 192.168.10.3 | Servidor web |
| `srv-db` | Debian 12 | 192.168.10.4 | Base de datos |
| `cliente` | Windows 11 | DHCP | Pruebas |

---

## 📂 Estructura del repositorio

```text
.
├── 📁 docs/            # Documentación y memoria del proyecto
├── 📁 scripts/         # Scripts de automatización (bash, powershell)
├── 📁 config/          # Ficheros de configuración de los servicios
├── 📁 docker/          # Dockerfiles y docker-compose.yml
├── 📁 img/             # Capturas y diagramas
├── 📄 README.md
└── 📄 LICENSE
```

---

## ⚙️ Requisitos previos

- Linux (probado en Debian 12) o una VM con virtualizador
- `git`
- `docker` y `docker compose` (si usas la parte de contenedores)
- Permisos de `sudo`
- Ganas de romper cosas y arreglarlas 🔧

---

## 🚀 Instalación y despliegue

```bash
# 1. Clona el repositorio
git clone https://github.com/TU-USUARIO/NOMBRE-DEL-PROYECTO.git
cd NOMBRE-DEL-PROYECTO

# 2. Dale permisos de ejecución a los scripts
chmod +x scripts/*.sh

# 3. Ejecuta el script de instalación
sudo ./scripts/install.sh
```

**Con Docker:**

```bash
cd docker
docker compose up -d
```

Para parar todo:

```bash
docker compose down
```

---

## 💻 Uso

```bash
# Comprobar el estado de los servicios
systemctl status bind9 apache2 mariadb

# Probar la resolución DNS
dig @192.168.10.2 miempresa.local

# Ver logs en tiempo real
journalctl -u apache2 -f
```

| Comando | Descripción |
|---------|-------------|
| `./scripts/backup.sh` | Copia de seguridad de configuración y BBDD |
| `./scripts/check.sh` | Comprueba que todos los servicios están levantados |
| `./scripts/clean.sh` | Limpia el entorno |

---

## 📸 Capturas

> Sube tus imágenes a la carpeta `img/` y enlázalas así:

![Captura 1](img/captura1.png)
![Captura 2](img/captura2.png)

---

## 🧠 Lo que he aprendido

- ✅ Configurar y securizar servicios de red en Linux
- ✅ Automatizar tareas repetitivas con Bash
- ✅ Que `chmod 777` **no** es la solución a todo
- ✅ Que casi siempre el problema es el DNS (o el firewall)
- ✅ Documentar bien para que mi yo del futuro no me odie
- ✅ Trabajar con Git sin liarla (demasiado)

---

## 🔐 Seguridad

- Acceso por SSH solo con clave pública
- Firewall activo con política por defecto `DROP`
- Fail2ban contra fuerza bruta
- Contraseñas **nunca** en el repo (se usan variables de entorno / `.env`)

> ⚠️ Este proyecto es **educativo**. Úsalo solo en entornos propios o de laboratorio.

---

## 🗓️ Roadmap

- [ ] Añadir monitorización con Zabbix
- [ ] Implementar copias de seguridad automáticas con cron
- [ ] Montar un servidor VPN (WireGuard / OpenVPN)
- [ ] Pasar la configuración a Ansible
- [ ] Documentación en vídeo

---

## 🤝 Contribuciones

Si ves algo que se puede mejorar, ¡abre un *issue* o un *pull request*! Estoy aprendiendo y cualquier feedback se agradece.

1. Haz un fork del proyecto
2. Crea tu rama (`git checkout -b feature/mejora`)
3. Haz commit (`git commit -m "Añade mejora"`)
4. Haz push (`git push origin feature/mejora`)
5. Abre un Pull Request

---

## 📜 Licencia

Distribuido bajo licencia **MIT**. Consulta el archivo [`LICENSE`](LICENSE) para más información.

---

## 👤 Autor

<div align="center">

**TU NOMBRE**
Estudiante de 2º de ASIR · IES NOMBRE-DEL-INSTITUTO

[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/TU-USUARIO)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/TU-USUARIO)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:tucorreo@ejemplo.com)

⭐ Si te ha servido, ¡déjame una estrella en el repo! ⭐

</div>
