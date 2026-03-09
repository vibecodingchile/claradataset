# 🚀 TUTORIAL COMPLETO — Deploy DataCL en datacl.cl
## Todo desde el celular o PC, gratis con GitHub Pages

---

## 📦 ARCHIVOS QUE TIENES (en el ZIP `datacl-deploy.zip`)

```
datacl/
├── index.html          ← LANDING (la página de ventas)
├── CNAME               ← Le dice a GitHub cuál es tu dominio
├── .nojekyll           ← Necesario para GitHub Pages
├── _config.yml         ← Config básica
└── catalogo/
    ├── index.html      ← El marketplace con los 30 datasets
    ├── css/main.css
    ├── js/app.js
    └── js/datasets.js
```

**Resultado final:**
- `datacl.cl` → Landing de ventas
- `datacl.cl/catalogo/` → Catálogo con los 30 datasets

---

## PASO 1 — Crear cuenta en GitHub (5 minutos)

1. Ve a **github.com**
2. Clic en **Sign up**
3. Email, contraseña, username → elige algo como `vibecodingchile` o `datacl-io`
4. Confirma el email que te llega
5. Plan gratuito es suficiente ✅

---

## PASO 2 — Crear el repositorio (3 minutos)

1. Una vez dentro de GitHub, clic en el **+** (arriba derecha) → **New repository**
2. Repository name: `datacl` (importante: exactamente así, minúscula)
3. Description: `DataCL — Marketplace de datos chilenos`
4. Marcar como **Public** (GitHub Pages gratis solo funciona en público)
5. ✅ Marcar **Add a README file**
6. Clic **Create repository**

---

## PASO 3 — Subir los archivos (10 minutos)

### Opción A: Desde el navegador (sin instalar nada)

1. Abre el repositorio que creaste
2. Clic en **Add file** → **Upload files**
3. **Descomprime el ZIP** `datacl-deploy.zip` en tu computador
4. Arrastra **todos los archivos y carpetas** de dentro del ZIP al recuadro de GitHub
   - `index.html`
   - `CNAME`
   - `.nojekyll`
   - `_config.yml`
   - La carpeta `catalogo/` completa con todo su contenido
5. Abajo en **Commit changes**:
   - Mensaje: `feat: DataCL MVP inicial`
   - Clic **Commit changes**

> ⚠️ **OJO con los archivos ocultos**: `.nojekyll` empieza con punto. 
> En Windows puede que no aparezca. Si no lo ves, créalo manualmente: 
> clic **Add file** → **Create new file** → escribe `.nojekyll` → deja el contenido vacío → commit.

### Opción B: Desde terminal (si tienes Git instalado)

```bash
# En tu computador, descomprime el ZIP y entra a la carpeta
cd datacl

# Inicializar git
git init
git add .
git commit -m "feat: DataCL MVP inicial"

# Conectar con GitHub (cambia TU_USUARIO por tu username)
git remote add origin https://github.com/TU_USUARIO/datacl.git
git branch -M main
git push -u origin main
```

---

## PASO 4 — Activar GitHub Pages (2 minutos)

1. En tu repositorio, clic en **Settings** (el engranaje, arriba)
2. En el menú lateral izquierdo → **Pages**
3. En **Source** → selecciona **Deploy from a branch**
4. En **Branch** → selecciona `main` y `/` (root)
5. Clic **Save**

GitHub te mostrará: 
> ✅ *"Your site is published at https://TU_USUARIO.github.io/datacl"*

**En 2-5 minutos ya está online.** Puedes entrar a esa URL para verificar que todo se ve bien antes de conectar el dominio.

---

## PASO 5 — Comprar el dominio (datacl.cl u otro)

### En DonWeb (más barato)
1. Ve a **donweb.com**
2. Busca `datacl.cl` → si está disponible, agregar al carrito
3. En el checkout fíjate en el **precio de renovación** año 2
4. Paga con Webpay o tarjeta

### En NIC Chile (más directo)
1. Ve a **nic.cl**
2. Clic **Inscribe tu dominio**
3. Busca `datacl.cl`
4. Si está libre → sigue el proceso con tu RUT chileno
5. Paga con Webpay (~$10.000–12.000 CLP/año)

### Alternativas si datacl.cl está tomado
Prueba en nic.cl:
- `datacl.cl` → primera opción
- `datoscl.cl`
- `dataset.cl`
- `datoschile.cl`

---

## PASO 6 — Conectar dominio con GitHub Pages (15 minutos)

Este paso tiene **DOS partes**: configurar DNS en el registrador, y configurar GitHub.

### Parte A: En tu registrador (DonWeb / NIC Chile)

Entra al panel de control de tu dominio y busca **"Configuración DNS"** o **"Zona DNS"**.

Agrega estos registros:

| Tipo | Nombre | Valor |
|------|--------|-------|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | TU_USUARIO.github.io |

> Los 4 registros A son las IPs de GitHub Pages. Son siempre las mismas.
> El CNAME para `www` hace que `www.datacl.cl` también funcione.

### Parte B: En GitHub

1. Ve a tu repositorio → **Settings** → **Pages**
2. En **Custom domain** escribe: `datacl.cl`
3. Clic **Save**
4. ✅ Activa **Enforce HTTPS** (aparece después de un momento)

### Verificar que funcionó

El DNS puede tardar entre **10 minutos y 24 horas** en propagarse.
Puedes verificar en: **whatsmydns.net** → escribe `datacl.cl` → tipo A.
Cuando veas las IPs de GitHub (185.199.xxx.xxx) en todo el mundo, ya está.

---

## PASO 7 — Verificar que todo se ve bien ✅

Una vez que el dominio esté activo:

| URL | Qué deberías ver |
|-----|-----------------|
| `https://datacl.cl` | Landing de ventas (fondo negro, título grande) |
| `https://datacl.cl/catalogo/` | Catálogo con los 30 datasets |
| `https://www.datacl.cl` | Redirige a la landing |

---

## PASO 8 — Actualizar el número de WhatsApp en la landing

En el archivo `datacl/index.html`, busca esta línea:

```
https://wa.me/56912345678
```

Cámbiala por tu número real:
```
https://wa.me/569XXXXXXXXX
```

Para editar directamente en GitHub:
1. Abre el archivo `index.html` en el repositorio
2. Clic en el **lápiz** (Edit this file)
3. Busca `56912345678` → reemplaza por tu número
4. Commit changes

---

## PROBLEMAS COMUNES Y SOLUCIONES

**❌ "La página se ve sin estilos / todo blanco"**
→ Verifica que subiste la carpeta `catalogo/css/main.css`. 
→ En GitHub, entra a `catalogo/css/` y confirma que `main.css` está ahí.

**❌ ".nojekyll no aparece en el ZIP"**
→ Es un archivo oculto. Créalo manualmente en GitHub: Add file → Create new file → nombre: `.nojekyll` → contenido vacío → commit.

**❌ "El dominio no carga después de configurar DNS"**
→ Espera hasta 24 horas. El DNS es lento. Verifica en whatsmydns.net.

**❌ "GitHub Pages dice 'Page not found'"**
→ Revisa que en Settings → Pages la fuente sea `main` branch y `/` (root), no `/docs`.

**❌ "El catálogo carga pero está vacío"**
→ Verifica que `catalogo/js/datasets.js` y `catalogo/js/app.js` subieron correctamente.

---

## CHECKLIST FINAL ✅

- [ ] Cuenta GitHub creada
- [ ] Repositorio `datacl` creado (público)
- [ ] Todos los archivos subidos (index.html + catalogo/ + CNAME + .nojekyll)
- [ ] GitHub Pages activado en Settings → Pages → main / root
- [ ] Landing se ve en `TU_USUARIO.github.io/datacl`
- [ ] Dominio comprado (datacl.cl u otro)
- [ ] DNS configurado (4 registros A + 1 CNAME)
- [ ] Custom domain configurado en GitHub Pages
- [ ] HTTPS activado
- [ ] Número de WhatsApp actualizado en index.html
- [ ] `datacl.cl` → Landing ✅
- [ ] `datacl.cl/catalogo/` → Catálogo ✅

---

## DESPUÉS DEL DEPLOY — Primeros pasos para vender

1. **Postea en LinkedIn** una screenshot de la landing con el link
2. **Busca "data engineer Chile"** en LinkedIn → manda el dataset de establecimientos de salud con GPS como muestra gratuita
3. **Busca "sustainability manager Chile"** → manda el factor de emisión SEN como demo del valor
4. **Precio de entrada**: ofrece el primer dataset individual a $25.000 para los primeros 5 clientes
5. **WhatsApp Business**: crea perfil con foto, nombre DataCL y descripción del negocio

---

*Hecho con ⚡ VibeCodingChile & 🤖 ClaudioCode*
*Última actualización: Marzo 2026*
