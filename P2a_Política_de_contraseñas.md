# Política de contraseñas

## Contexto
Por defecto, la mayoría de sistemas operativos, vienene con una política de contraseña muy laxa, una contraseña segura presenta una barrera más al atacante, que en su intento de acceder al sistema, indudablemete dejará más rastro y en algunos casos a provocar el abandondo de ataque.

## Objetivos
* Entender el sistema de contraseñas del sistema operativo linux
* Entender el PAM (Plugable authentication Module)
* Instalar y configurar la libreria _pwquality_
* Comprobar y verificar que se ha llevado la práctica de forma correcta
* Documentar la práctica.


# Instalación
Para instalar la libreria.
```bash
sudo apt install libpam-pwquality
```
el archivo de configuración
```bash
vim /etc/security/pwquality.conf
```
Para comprobar que la librería está en funcionamiento, hay que entrar en el fichero /etc/pam.d/common-password y ver que está la línea siguiente:
```bash
password        requisite                       pam_pwquality.so retry=3

```

|   | Score  | L min  | Ejemplos| 
|---|---|---|---|
| No valido | <35  | - | vinicio  |
| Débil  | 35-50  |  6 |  H37@kl|
| Media  | 50-80 | 8  |  KRop301.,rt |  
| Extrema  | >80 | 10  |  .@45DlpFR?¿6 |   

### Politica debil
```bash
minlen = 6
ucredit = -1
dcredit = -2
ocredit = -1
```
### Politica media
```bash
minlen = 8
ucredit = -2
dcredit = -3
ocredit = -2
```
### Politica extrema
```bash
minlen = 12
dcredit = -3
ucredit = -3
lcredit = -2
ocredit = -4
```

