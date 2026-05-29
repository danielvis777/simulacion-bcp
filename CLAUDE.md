# CLAUDE.md — simulacion-bcp

## Qué es este proyecto

Simulación educativa de phishing para Banco BCP. Cuando un empleado hace clic en
el correo simulado, llega a una landing que le explica que fue un ejercicio.
Stack: HTML estático puro. Sin frameworks, sin build tools, sin dependencias.
Etapa: inicial / operativo en campañas puntuales.

Archivos:
- `plantilla_email.html` — correo de phishing simulado (se personaliza por destinatario)
- `landing.html` — página que ve el usuario al hacer clic
- `participantes.csv` — lista de participatnes con nombre, correo y hash de rastreo

---

## Cómo encarar las tareas

### Antes de ejecutar cualquier tarea

1. Lee todos los archivos relevantes primero. No preguntes cosas que puedes
   descubrir leyendo el código.
2. Si la tarea toca más de un archivo o cambia la estructura del proyecto,
   escribe un plan numerado y espera confirmación antes de tocar nada.
3. El plan debe decir exactamente: qué archivos se modifican, qué líneas cambian,
   y por qué. Sin ese detalle, el plan no es válido.

### Cómo ejecutar

4. Aplica el cambio mínimo que resuelve el problema. Si la solución cabe en
   5 líneas, no la conviertas en 20.
5. No crees funciones, clases, helpers ni abstracciones que no se pidieron
   explícitamente. Tres líneas repetidas son mejores que una abstracción prematura.
6. No toques líneas que no están relacionadas con el pedido, aunque te parezcan
   mejorables.

### Autonomía (hacer sin pedir permiso)

7. Corrige errores de indentación y espaciado directamente, sin preguntar.
8. Si hay un bug evidente y pequeño (typo, etiqueta HTML mal cerrada, placeholder
   sin reemplazar), corrígelo y menciona qué cambiaste al final.
9. Investiga el problema en el código antes de hacerme cualquier pregunta.
   Solo pregunta si después de investigar sigues sin poder resolverlo.

### Lo que NO debes hacer

10. No agregues comentarios que expliquen qué hace el código. El código bien
    escrito se explica solo.
11. No instales dependencias, no agregues frameworks, no introduzcas npm, vite
    ni ninguna herramienta de build sin que yo lo pida explícitamente.
12. No cambies la estructura de carpetas sin confirmar primero.
13. No uses placeholders genéricos como `TODO` o `FIXME` en el código entregado.

---

## Convenciones de este proyecto

- Indentación: 4 espacios en HTML.
- Placeholders dinámicos usan guillemets: `«Nombre»`, `«Enlace»`. Nunca usar
  `{{nombre}}`, `${nombre}` ni ningún otro formato.
- Colores de marca BCP: azul `#003366`, naranja `#ff6600`. No cambiarlos.
- Todo el texto visible al usuario va en español (es-PE).
- El footer del email y la landing siempre deben incluir la leyenda
  "Ejercicio Educativo". No eliminarla.

---

## Verificación antes de dar algo por terminado

Antes de decir que una tarea está lista, confirma estos puntos:

- [ ] ¿Todos los placeholders `«…»` fueron reemplazados o siguen donde deben?
- [ ] ¿El HTML abre y cierra todas las etiquetas correctamente?
- [ ] ¿La leyenda "Ejercicio Educativo" sigue presente?
- [ ] ¿El cambio no tocó líneas fuera del scope del pedido?
- [ ] ¿La solución es la más simple posible para el problema dado?

Si alguna respuesta es no, corrígelo antes de reportar la tarea como completa.

---

## Ciclo de mejora continua

Cada vez que termines una tarea, anota al final de tu respuesta una línea con
este formato exacto:

```
LECCIÓN: [qué aprendiste o qué harías diferente la próxima vez]
```

Si no hay nada nuevo que aprender, escribe:

```
LECCIÓN: ninguna nueva en esta tarea.
```

Esto permite identificar patrones y mejorar el flujo de trabajo con el tiempo.

---

## Ramas de trabajo

| Rama | Uso |
|------|-----|
| `main` | Solo código estable y revisado |
| `claude/…` | Ramas de trabajo de Claude — siempre mergear via PR |

Nunca hagas push directo a `main`.
