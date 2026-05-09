# Deploy del sitio web tocaycobra.com.mx

Sitio listo para deploy en **Cloudflare Pages** (gratis ilimitado).

## Pasos para deploy (15 minutos)

### 1. Crear cuenta GitHub (si no tienes) — 3 min

1. Ve a [github.com/signup](https://github.com/signup)
2. Crea cuenta con tu email (recomendado: usar `soporte@tocaycobra.club` para mantener todo en la marca)
3. Verifica email

### 2. Subir el código a GitHub — 5 min

**Opción A — Upload directo desde la web (más fácil):**

1. En GitHub, click en **"+ New repository"** (esquina superior derecha)
2. Nombre: `tocaycobra-web`
3. Privado (puedes hacerlo público después)
4. Click "Create repository"
5. En la página del repo nuevo, click **"uploading an existing file"**
6. Arrastra los archivos de la carpeta `tocaycobra-web` (`index.html`, `_redirects`, `robots.txt`)
7. Commit message: "Initial commit"
8. Click "Commit changes"

**Opción B — Con git (si ya manejas):**

```bash
cd tocaycobra-web
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/TUUSUARIO/tocaycobra-web.git
git push -u origin main
```

### 3. Crear cuenta Cloudflare — 3 min

1. Ve a [dash.cloudflare.com/sign-up](https://dash.cloudflare.com/sign-up)
2. Crea cuenta con email + contraseña
3. Verifica email

### 4. Conectar Cloudflare Pages al repo — 4 min

1. En Cloudflare Dashboard, lateral izquierdo: **Workers & Pages**
2. Click **"Create application"** → tab **"Pages"** → **"Connect to Git"**
3. Autoriza GitHub → selecciona tu repo `tocaycobra-web`
4. Configuración del build:
   - Production branch: `main`
   - Framework preset: **None**
   - Build command: (déjalo vacío)
   - Build output directory: `/`
5. Click **"Save and Deploy"**

En 30-60 segundos tu sitio está LIVE en una URL tipo `tocaycobra-web.pages.dev`.

### 5. Apuntar tu dominio personalizado — 5 min

#### En Cloudflare Pages:

1. En tu proyecto recién creado, ve a tab **"Custom domains"**
2. Click **"Set up a custom domain"**
3. Ingresa: `tocaycobra.com.mx`
4. Cloudflare te va a dar 2 nameservers. Anótalos.

#### En GoDaddy:

1. Inicia sesión en GoDaddy → **Mis productos** → **Dominios**
2. Click en `tocaycobra.com.mx` → **Configuración DNS**
3. Cambia los nameservers a los que te dio Cloudflare:
   - Eg. `xxx.ns.cloudflare.com`
   - Eg. `yyy.ns.cloudflare.com`
4. Guardar

**Propagación DNS:** 5-30 minutos. Después `tocaycobra.com.mx` apunta a tu sitio.

### 6. Repetir para los otros 5 dominios (opcional)

Si quieres que `.net`, `.xyz`, `.store`, `.info`, `.club` redirijan a `.com.mx`:

1. Misma instrucción de cambiar nameservers en GoDaddy.
2. En Cloudflare, agrega los dominios secundarios y configura redirección 301 a `.com.mx`.

---

## Costos

- Hosting Cloudflare Pages: **$0** (gratis ilimitado para sitios estáticos)
- Hosting Cloudflare Workers (futuro): **$0** hasta 100K requests/día
- Cloudflare D1 (futuro): **$0** hasta 5GB
- SSL/HTTPS: **$0** (automático)
- CDN global: **$0** (automático)
- Bandwidth: **$0** ilimitado

**Total mensual: $0** hasta tener miles de visitas.

---

## Cómo actualizar el sitio después

Cualquier cambio que hagas:
1. Commit + push a la rama `main` en GitHub
2. Cloudflare detecta el cambio automáticamente
3. Re-deploy automático en 30-60 segundos
4. Cambios en vivo

Sin tocar servidor, sin SSH, sin nada técnico.

---

## Próximos pasos del sitio

Cuando este básico funcione, agregamos:

1. **Backend de lista de espera** — guardar emails en Cloudflare D1 en lugar de localStorage
2. **Email automático** de bienvenida con Cloudflare Email Workers
3. **Página de pricing detallada** con comparativa de tiers
4. **Blog/recursos** para SEO orgánico
5. **Integración con WhatsApp Business** para CTA "Háblanos por WhatsApp"
6. **Analytics** con Cloudflare Web Analytics (gratis, sin cookies, GDPR-safe)
7. **Open Graph + Twitter Cards** mejorados (imágenes, etc.)
8. **Versión inglés** si planeas expandir
