# ansible-playbooks
ansible playbooks


# My Ansible Repo

Este repositorio contiene un playbook de Ansible que actualiza los paquetes del sistema y reinicia si es necesario, además de enviar notificaciones a través de `ntfy`.

## Estructura del repositorio

- `.github/workflows/deploy.yml`: Configuración de GitHub Actions para ejecutar el playbook automáticamente.
- `inventory/hosts.ini`: Archivo de inventario de Ansible.
- `playbook/playbook.yml`: Playbook de Ansible para actualizar paquetes y reiniciar.

## Cómo usar

1. Clona el repositorio.
2. Configura tus servidores en `inventory/hosts.ini`.
3. Asegúrate de añadir el secreto `NTFY_TOKEN` en la configuración del repositorio en GitHub.
4. Haz un push a la rama `main` para ejecutar el workflow.

