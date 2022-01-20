# PS4 9.00 Kernel Exploit
---
## Resumen
En este proyecto encontrarás una implementación que intenta hacer uso de un error del sistema de archivos para Playstation 4 en el firmware 9.00.
El error se encontró al comparar los kernels 9.00 y 9.03. Requerirá una unidad con un sistema de archivos exfat modificado. Activarlo con éxito le permitirá ejecutar código arbitrario como kernel, para permitir el jailbreak y las modificaciones a nivel de kernel en el sistema, lanzará el lanzador de carga útil habitual (en el puerto 9020).

ESTE REPOSITORIO ES UNA PERSONALIZACIÓN DEL HOST DE KARO REALIZADO PARA NANOSPEEDGAMERYT.

## Patches Included
The following patches are applied to the kernel:
1) Allow RWX (read-write-execute) memory mapping (mmap / mprotect)
2) Syscall instruction allowed anywhere
3) Dynamic Resolving (`sys_dynlib_dlsym`) allowed from any process
4) Custom system call #11 (`kexec()`) to execute arbitrary code in kernel mode
5) Allow unprivileged users to call `setuid(0)` successfully. Works as a status check, doubles as a privilege escalation.
6) (`sys_dynlib_load_prx`) patch
7) Disables sysVeri

## Parches incluidos
Los siguientes parches se aplican al kernel:
1) Permitir mapeo de memoria RWX (lectura-escritura-ejecución) (mmap / mprotect)
2) Instrucción Syscall permitida
3) Resolución dinámica (`sys_dynlib_dlsym`) permitida desde cualquier proceso
4) Llamada al sistema personalizada #11 (`kexec()`) para ejecutar código arbitrario en modo kernel
5) Permitir que los usuarios sin privilegios llamen a `setuid(0)` con éxito. Funciona como una verificación de estado, se duplica como una escalada de privilegios.
6) (`sys_dynlib_load_prx`) parche
7) Desactiva sysVeri

## Cómo funciona
Este exploit es diferente a los anteriores en los que se basaban únicamente en el software. Activar la vulnerabilidad requiere conectar un dispositivo USB con formato especial en el momento justo. En el repositorio encontrarás un archivo .img. Puede escribir este .img en un USB usando algo como Win32DiskImager.

**Nota: Esto borrará la unidad USB, asegúrese de seleccionar la unidad correcta y de que está de acuerdo con eso antes de hacer esto**

![](https://i.imgur.com/qpiVQGo.png)

Cuando ejecutas el exploit en la PS4, espera hasta que llegue una alerta de "Inserte el USB ahora. no cierre el diálogo hasta que aparezca la notificación, retire el usb después de cerrarlo". Tal y como indica el diálogo, inserta el USB, y espera hasta que aparezca la notificación "formato de disco no soportado", entonces cierra la alerta con "OK".


## Notas Extra
- Desenchufa el USB antes de un ciclo de (re)arranque o te arriesgarás a corromper archivos del kernel.
- No cierres el navegador mientras lanzas el exploit.
- El círculo de carga podría congelarse mientras se activa el exploit, esto no significa que el exploit haya fallado.
- El bug es anterior al firmware 1.00, por lo que el 1.00-9.00 debería ser explotable usando la misma estrategia (necesitarás un exploit de userland diferente y gadgets).
- Puedes sustituir el cargador por un payload específico para cargar cosas directamente en lugar de hacerlo a través de sockets.
- Este bug funciona en ciertos firmwares de PS5, sin embargo no se conoce ningún exploit por ahora. 
- No se aconseja utilizar este fallo contra la PS5 a ciegas.
- Este repositorio no proporciona nada más allá de los parches iniciales del kernel que permiten ejecutar payloads.
- Como se ha dicho antes, este fallo se encontró al diferenciar los kernels 9.00 y 9.03, lo que implica que el fallo fue corregido en la 9.03.


## Créditos

- laureeeeeee
- [Specter](https://twitter.com/SpecterDev)
- [Znullptr](https://twitter.com/Znullptr)

## Agradecimientos
- [Andy Nguyen](https://twitter.com/theflow0)
- [sleirsgoevy](https://twitter.com/sleirsgoevy) - [9.00 Webkit exploit](https://github.com/sleirsgoevy/bad_hoist/tree/9.00)
- Karo218 Sharifi
