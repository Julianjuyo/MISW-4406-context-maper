![Context Mapper](https://raw.githubusercontent.com/wiki/ContextMapper/context-mapper-dsl/logo/cm-logo-github-small.png)
## Context Maps: Alpes Partners

### Integrantes

| Nombre                                 | Correo                       |
|----------------------------------------|------------------------------|
| Miguel Fernando Padilla Espino         | m.padillae@uniandes.edu.co   |
| Johann Sebastian Páez Campos           | js.paezc1@uniandes.edu.co    |
| Julián Esteban Oliveros Forero         | je.oliverosf@uniandes.edu.co |

---

### Estructura
```
📦 Alpes Partners
├── 📁 .devcontainer # Configuración para correr el proyecto en Codespaces o en local usando Codespaces.
├── 📁 gradle/wrapper # Archivos de configuración de Gradle Wrapper.
├── 📁 src-gen # Imágenes de los modelos generados (AS-IS y TO-BE).
├── 📁 src/main/cml # Modelos en CML (AS-IS y TO-BE).
├── 📄 .gitignore # Archivo para excluir ficheros del control de versiones.
├── 📄 README.md # Documento de documentación del proyecto (usted está aquí).
├── 📄 build.gradle # Archivo de configuración principal de Gradle.
├── 📄 gradle.properties # Propiedades de Gradle.
├── 📄 gradlew # Script de Gradle Wrapper para Unix.
├── 📄 gradlew.bat # Script de Gradle Wrapper para Windows.
└── 📄 settings.gradle # Configuración de Gradle para el proyecto.
```

---

### Instrucciones
1. asdasd
2. asdasd

---

### AS-IS
En el estado actual (AS-IS), el dominio **Gestión de Asociaciones Estratégicas** está compuesto por cuatro subdominios núcleo. Actualmente, existe acoplamiento mediante **Shared Kernel** entre algunos contextos, lo que puede generar problemas de escalabilidad y evolución.

**Archivo:** `src/main/cml/Alpes_Partners_AS-IS.cml`

#### Dominio
- **Gestión de Asociaciones Estratégicas**  
  **Vision Statement:** "Consolidar la plataforma líder a nivel global para conectar, gestionar y escalar relaciones estratégicas entre marcas y socios, maximizando el valor mutuo y el retorno de inversión."

#### Subdominios

| Subdominio                  | Líneas  | Tipo   | Vision Statement |
|-----------------------------|---------|--------|------------------|
| MarketingAfiliados          | 3-6     | Núcleo | Impulsar las ventas y el reconocimiento de marca mediante la automatización y optimización de programas de afiliación altamente medibles. |
| MarketingInfluencers        | 7-10     | Núcleo | Facilitar conexiones auténticas entre marcas y audiencias a través de creadores verificados, maximizando el impacto y la relevancia. |
| ProgramasLealtad            | 11-14    | Núcleo | Transformar clientes y empleados en embajadores activos, amplificando la voz de la marca con testimonios y recomendaciones genuinas. |
| GestionAlianzas   | 15-18   | Núcleo | Proveer un hub centralizado para administrar el ciclo de vida completo de las relaciones comerciales, desde la negociación hasta el pago y cumplimiento. |

#### Contextos acotados
- **ContextoAfiliados** → Implementa *MarketingAfiliados* (líneas 20-21)  
- **ContextoInfluencers** → Implementa *MarketingInfluencers* (líneas 22-23)  
- **ContextoLealtad** → Implementa *ProgramasLealtad* (líneas 24-25)  
- **ContextoAlianzas** → Implementa *GestionAlianzas* (líneas 26-27)  

#### Relaciones (Context Map)
**Líneas:** 35-38 
- ContextoAfiliados [SK] ↔ [SK] ContextoInfluencers  
- ContextoLealtad [D] ← [U] ContextoAlianzas  
- ContextoAfiliados [D] ← [U] ContextoAlianzas  
- ContextoInfluencers [D] ← [U] ContextoAlianzas  

#### Imagen del modelo AS-IS
<img width="2000" height="1029" alt="image" src="https://github.com/user-attachments/assets/511708dd-16ce-48f7-a9c4-16de0ac5a0ee" />

---

### TO-BE
En el estado futuro (TO-BE), se refina el lenguaje ubicuo y se eliminan anti-patrones como el **Shared Kernel**. Las relaciones usan **OHS**, **PL** y **ACL** para garantizar comunicación clara y modelos internos desacoplados.

**Archivo:** `src/main/cml/Alpes_Partners_TO-BE.cml`

#### Dominio
- **Gestión de Asociaciones Estratégicas**  
  **Vision Statement:** "Plataforma flexible que conecta marcas con socios estratégicos para gestionar programas de afiliación, marketing con influencers, lealtad y alianzas, con integraciones claras y sin confusiones."

#### Subdominios

| Subdominio              | Líneas  | Tipo   | Vision Statement |
|-------------------------|---------|--------|------------------|
| AfiliacionDigital       | 3-6     | Núcleo | Automatizar el reclutamiento, seguimiento y pago de afiliados con métricas precisas y procesos estandarizados. |
| InfluencerEngagement    | 7-10     | Núcleo | Conectar marcas con creadores relevantes mediante flujos de campaña claros, seguimiento de impacto y pagos transparentes. |
| ProgramasLealtad         | 11-14    | Núcleo | Potenciar a clientes y empleados como embajadores, maximizando su contribución mediante incentivos y contenido auténtico. |
| GestionAlianzas      | 15-18   | Núcleo | Orquestar contratos, términos, cumplimiento y pagos para cualquier tipo de socio estratégico. |

#### Contextos acotados
- **BC_Afiliacion** → Implementa *AfiliacionDigital* (líneas 20-21)  
- **BC_Influencers** → Implementa *InfluencerEngagement* (líneas 22-23)  
- **BC_Lealtad** → Implementa *ProgramasLealtad* (líneas 24-25)  
- **BC_Alianzas** → Implementa *GestionAlianzas* (líneas 26-27)  

#### Relaciones (Context Map)
**Líneas:** 35-39  
- BC_Afiliacion [OHS, PL] → BC_Alianzas  
- BC_Influencers [OHS, PL] → BC_Alianzas  
- BC_Lealtad [ACL] ← BC_Alianzas  
- BC_Afiliacion [ACL] ← BC_Alianzas  
- BC_Influencers [ACL] ← BC_Alianzas  

#### Imagen del modelo TO-BE
<img width="2000" height="1311" alt="image" src="https://github.com/user-attachments/assets/40c473eb-50dd-4639-86be-9ec31d31605d" />


