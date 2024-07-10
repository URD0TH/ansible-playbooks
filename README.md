# ansible-playbooks
ansible playbooks


# Mi Repositorio de Ansible

Este repositorio contiene un playbook de Ansible que actualiza los paquetes del sistema y reinicia si es necesario, además de enviar notificaciones a través de `ntfy`. Recientemente, se han agregado mejoras para la gestión de dependencias y la optimización de la eficiencia del proceso de actualización.

## Estructura del repositorio

```bash
ansible-playbooks/
┣ .github/
┃ ┗ workflows/
┃   ┗ deploy.yml
┣ inventory/
┃ ┣ vars/
┃ ┃ ┗ hosts_vars.yml
┃ ┗ host.ini
┣ playbooks/
┃ ┗ upgrade.yml
┣ vault/
┃ ┗ ssh_keys.yml
┣ estructura.tree
┗ README.md
```

- `.github/workflows/deploy.yml`: Configuración de GitHub Actions para ejecutar el playbook automáticamente.
- `inventory/hosts.ini`: Archivo de inventario de Ansible.
- `playbook/playbook.yml`: Playbook de Ansible para actualizar paquetes y reiniciar, con mejoras para la gestión de dependencias y la eficiencia.
- `vault/ssh_keys.yml`: Archivo de claves SSH para la conexión segura con los servidores. estas estan encriptadas por ansible-vars

el formato el cual la genero es 

```bash
ssh_key_{hosname_1}: |
-----BEGIN RSA PRIVATE KEY-----
... resto de la key
-----END RSA PRIVATE KEY-----
ssh_key_{hosname_2}: |
-----BEGIN RSA PRIVATE KEY-----
... resto de la key
-----END RSA PRIVATE KEY-----
# agregar una o varias segun tengas y cambiar {hostname} por el nombre de hostname del host para identificarla
```

```bash
ansible-vault encrypt vault/ssh_keys.yml
```
se te pedira una contraseña segura la cual debes guardar y agregar en secret del repositorio


## Cómo usar

1. Clona el repositorio.
2. Configura tus servidores en `inventory/hosts.ini`.
3. Asegúrate de agregar las siguientes variables de entorno en la configuración de GitHub Actions:
   - `S_NTFY_TOKEN`: Token de notificación para `ntfy`.
   - `TAILSCALE_AUTH_KEY`: Clave de autenticación para Tailscale.
   - `ANSIBLE_VAULT_PASSWORD`: Contraseña para el vault de Ansible.
   - `S_ARK_IP`: Dirección IP del servidor Ark.
   - `S_ARK_HOSTNAME`: Nombre de host del servidor Ark.
   - `S_PRIMAL_IP`: Dirección IP del servidor Primal.
   - `S_PRIMAL_HOSTNAME`: Nombre de host del servidor Primal.
   - `S_RAGE_IP`: Dirección IP del servidor Rage.
   - `S_RAGE_HOSTNAME`: Nombre de host del servidor Rage.
   - `S_B_M_IP`: Dirección IP del servidor Bnds-Media.
   - `S_B_M_HOSTNAME`: Nombre de host del servidor Bnds-Media.
   - `S_ALL_USER`: Usuario para todos los servidores.
   - `S_B_M_USER`: Usuario del servidor Bnds-Media.
4. Agrega las claves SSH a `vault/ssh_keys.yml` para la conexión segura con los servidores.
5. Haz un push a la rama `main` para ejecutar el workflow.
