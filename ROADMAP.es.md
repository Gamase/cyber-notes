# Plan de aprendizaje en Ciberseguridad

🌐 [English](ROADMAP.md) · **Español**

**Enfoque:** Blue Team / seguridad de infraestructura (hipótesis que se confirma en la Fase 3).
**Ritmo:** ~6–7 horas por semana, pensado para que dure, no para quemarse.
**Inicio:** noviembre 2026 · Volver al [tablero](README.es.md)

---

## 1. Reglas del hábito

1. **Misma hora, mismo lugar.** Un horario fijo (por ejemplo, después de cenar) que no se negocia cada día.
2. **Mínimo viable: 20 minutos.** En un día malo (exámenes, cansancio), 20 minutos cuentan como día cumplido: un nivel de Bandit, un video o repasar flashcards.
3. **Nunca fallar dos veces seguidas.** Faltar un día es normal. Faltar dos ya es el inicio de dejarlo.
4. **Descanso obligatorio.** Viernes y domingo libres. El descanso también es parte del plan.
5. **La escuela va primero.** En semanas de exámenes o de entregas de la residencia, pasar a "modo mínimo" (20 minutos al día) sin culpa.
6. **Sesiones con pausas.** Bloques de 25–50 minutos con descanso entre ellos. Nada de desvelarse para "avanzar más".
7. **Documentar todo** en este repo. Sirve para repasar y además es portafolio.

---

## 2. Semana tipo (~6.5 h)

| Día | Tiempo | Qué toca |
|---|---|---|
| Lunes | 60 min | **Linux**: teoría (Linux Journey → luego *How Linux Works*) |
| Martes | 60 min | **Redes**: 1–2 videos de Jeremy's IT Lab + su lab en Packet Tracer |
| Miércoles | 60 min | **Linux práctica**: OverTheWire Bandit / scripts de Bash |
| Jueves | 60 min | **Redes**: labs + flashcards de Anki (Jeremy's IT Lab incluye mazos) |
| Viernes | — | Descanso |
| Sábado | 2 h | **Práctica libre**: TryHackMe + un proyecto en el servidor de casa |
| Domingo | 15 min (opcional) | **Revisión semanal**: qué aprendí, qué sigue, actualizar notas |

Todos los días, 10 minutos de Anki cuentan dentro de la sesión.

---

## 3. Fases (tiempos aproximados a este ritmo)

### Fase 1 — Bases (meses 1–4)
- **Linux:** terminar Linux Journey y Bandit (~30+ niveles).
- **Redes:** primera mitad de Jeremy's IT Lab (CCNA): OSI/TCP-IP, subnetting, switching, VLANs.
- **Seguridad:** TryHackMe *Pre Security* (los sábados).
- **Lectura:** *Reflections on Trusting Trust* (Ken Thompson).
- **Servidor en casa:** asegurarlo (SSH solo con llaves, firewall, actualizaciones automáticas, revisar logs de acceso).

**Meta:** moverme en la terminal sin buscar comandos básicos y hacer subnetting a mano.

### Fase 2 — Programación + Redes avanzadas (meses 4–7)
- **Python:** *Automate the Boring Stuff* (lunes y miércoles pasan a ser de Python).
- **Redes:** segunda mitad del CCNA (routing, ACLs, NAT, seguridad) + **Wireshark**.
- **Bash:** scripts reales para el servidor (respaldos, alertas, revisión de logs).
- **Decidir:** ¿presentar el examen CCNA? Solo con presupuesto o descuento por NetAcad.

**Meta:** un script en Python que procese un log y detecte algo sospechoso.

### Fase 3 — Seguridad (meses 7–10)
- **Security+ (SY0-801):** curso de Professor Messer + práctica. Usar el **descuento de estudiante**.
- **Prueba de rama (2 semanas):** una semana de *SOC Level 1* y otra de *Jr Penetration Tester* en TryHackMe.
- **Servidor en casa:** montar **Wazuh** (SIEM) y monitorear mis propios equipos.
- **Bonus:** *Black Hat Python*.

**Meta:** Security+ presentado y una rama confirmada.

### Fase 4 — Especialización (mes 10 en adelante)
- **Si es Blue Team:** SOC Level 1 completo → CySA+ o BTL1, ingeniería de detección y PowerShell.
- **Si es Red Team:** Jr Pentester → HTB Starting Point / Academy → PNPT u OSCP más adelante.
- **Ambos:** Go, AWS Cloud Practitioner (revisar vouchers de AWS Educate) y luego seguridad en la nube.
- **Para después:** *The Design and Implementation of the FreeBSD OS*.

---

## 4. Primeras 4 semanas

| Semana | Linux (lun/mié) | Redes (mar/jue) | Sábado |
|---|---|---|---|
| 1 | Linux Journey: *Grasshopper* · Bandit 0–5 | Jeremy's IT Lab días 1–3 (dispositivos, OSI) · instalar Packet Tracer | Cuenta en TryHackMe · Pre Security: intro |
| 2 | Linux Journey: *Command Line* · Bandit 6–10 | Días 4–6 (Ethernet, switching) | Pre Security: Network Fundamentals |
| 3 | Linux Journey: *Text-Fu*, *Permissions* · Bandit 11–14 | Días 7–9 (IPv4, inicio de subnetting) | Pre Security: cont. · leer *Trusting Trust* |
| 4 | Linux Journey: *Processes* · Bandit 15–18 | Días 10–12 (subnetting a fondo) | Endurecer SSH en el servidor · revisión del mes |

**Revisión mensual** (último domingo de cada mes, 30 minutos): ¿voy al ritmo?, ¿me está gustando?, ¿ajusto algo? Si voy atrasado, se extiende la fase. No se recorta el descanso.
