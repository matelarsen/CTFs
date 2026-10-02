# POCTF — Writeups

**Evento CTF:** Pointer Overflow CTF - 2026 <br>
**Fecha:**  27 Sept. 2026, 14:00 UTC — 06 Dec. 2026, 14:00 UTC <br>
**Plataforma:** https://pointeroverflowctf.com/

## Overview

Durante este CTF completamos exitosamente **3 retos** de diferentes categorías. A continuación se documentan las soluciones y metodologías utilizadas para resolver cada desafío.

## Retos completados

### 1. The Shape of a Query
- **Categoría:** Web
- **Puntos:** 97 points
- **Vulnerabilidad:** Broken Object Level Authorization (BOLA / IDOR)

**Descripción:** Explotación de una API GraphQL de un portal de investigación colaborativa. El control de acceso que restringía ver el perfil de otros usuarios estaba implementado solo en la query de nivel superior `user(id)`, pero no en la ruta anidada `Team.members`, lo que permitió leer el campo `privateNotes` del administrador del equipo.

### 2. Letters Never Sent
- **Categoría:** Cryptography
- **Puntos:** 95 points

**Descripción:** Descifrado de un ciphertext a partir de pistas textuales y visuales incluidas en el propio desafío. Una referencia a Sir Francis Beaufort permitió identificar el algoritmo (cifrado Beaufort clásico), mientras que letras marcadas con estrellas rojas alrededor del desafío revelaron la clave (`NOVENA`) necesaria para el descifrado.

### 3. Everything Left Open
- **Categoría:** Forensics
- **Puntos:** 67 points

**Descripción:** Análisis forense de un perfil de usuario de Mozilla Firefox recuperado de un equipo. La flag se encontraba dentro del archivo de recuperación de sesión `sessionstore-backups/recovery.jsonlz4`, comprimido con LZ4 detrás de la cabecera `mozLz40\0` propia de Firefox.

## Results Summary

- **Total de retos completados:** 3
- **Total de puntos obtenidos:** 259
- **Categorías cubiertas:** Web, Cryptography, Forensics
- **Team:** Jajackers

## Flags Obtenidas

- **The Shape of a Query:** `POCTF{81.570.EYMNJYTMCESGFFGV.ARZPN4FWCTVU6JXSHCD4EFCT5T}`
- **Letters Never Sent:** `POCTF{2.570.PAJIVZIVBRLWGWE7.FD6LFLRNMTDULUNPOY2BSWBTZC}`
- **Everything Left Open:** `POCTF{109.570.XU55BITKMCNUUYXR.BXHYXXRXYKNORE6IZPHJ56UIQX}`

## Scripts incluidos

Cada writeup incluye, junto a su documento, un script de Python que automatiza la cadena de resolución como prueba de concepto reproducible:

- `exploit.py` — automatiza el ataque de **The Shape of a Query** (intercambio de sesión + query GraphQL anidada).
- `decode.py` — automatiza el descifrado Beaufort de **Letters Never Sent**.
- `jsonlz4.py` — automatiza la extracción y búsqueda de la flag en **Everything Left Open**.

---

*Para ver los writeups detallados de cada reto, consultar los archivos individuales en este directorio.*
