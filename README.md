# pbPdfFillFormFields — Rellenar formularios PDF 📝📄

![PowerBuilder](https://img.shields.io/badge/PowerBuilder-2025-orange?style=flat-square)
![.NET](https://img.shields.io/badge/.NET-10-512BD4?style=flat-square&logo=dotnet&logoColor=white)
![itext7](https://img.shields.io/badge/itext7-9.6.0-2C8EBB?style=flat-square)
![Blog](https://img.shields.io/badge/blog-rsrsystem-FF5722?style=flat-square&logo=blogger&logoColor=white)

## 📋 ¿Qué es esto?

Un ejemplo de PowerBuilder para **rellenar los campos de un formulario PDF** (los típicos **AcroForms**). Le dais un PDF con campos editables, una lista de nombres de campo y sus valores, y os genera el PDF ya cumplimentado. En la carpeta tenéis un caso real muy reconocible: el **`Modelo145.pdf`** de Hacienda.

Y otra vez la idea de fondo: el que sabe de PDFs es una **librería .NET** (`PdfFillFormFields`), que PowerBuilder 2025 importa con el **.NET DLL Importer** y usa como un `dotnetobject`. Creáis la clase `PdfFill` y llamáis a sus métodos directamente desde PB:

- `GetFormFields(string inputFile, ref string[] fieldNames)` → os descubre **qué campos tiene** el PDF (muy útil para no ir a ciegas).
- `FillFormFields(string inputFile, string outputFile, string[] fieldNames, string[] dataField)` → **rellena** esos campos con los datos indicados y guarda el PDF resultante.

El flujo didáctico es claro: primero preguntas al PDF qué campos tiene, luego le mandas los valores. Nada de adivinar nombres.

## 🔗 Motor .NET

El motor es la librería **`PdfFillFormFields`**, desplegada en `DotNet\PdfFillFormFields\` y consumida desde PowerBuilder como `dotnetobject`.

- **Código fuente .NET:** `C:\proyecto pw2025\Blog\Net10\PdfFillFormFields` (antes en `Net8`).
- **Repo .NET (Visual Studio 2022):** <https://github.com/rasanfe/PdfFillFormFields>
- **Despliegue:** se publica y se copia a `DotNet\PdfFillFormFields\` con el script `desplegar_dotnet.bat` (hace `dotnet publish` y espeja las DLLs al ejemplo).

> 💡 **Dato didáctico:** el ejemplo arrancó con **iTextSharp 5**, hoy **abandonada**. Al pasarlo a **.NET 10** se ha migrado a **itext7 9.6.0**, la versión moderna y mantenida. Mismo objetivo (rellenar AcroForms), pero con la librería puesta al día.

## 🛠️ Requisitos

- **PowerBuilder 2025** (con el .NET DLL Importer).
- **.NET 10 Runtime** instalado en la máquina que ejecuta el ejemplo.
- Las DLLs de `DotNet\PdfFillFormFields\` (itext7 y dependencias).

## ▶️ Cómo probarlo

1. Clona el repo "en modo solución" y abre el workspace en PowerBuilder 2025.
2. Compila y ejecuta `pbpdffillformfields`.
3. Carga el `Modelo145.pdf` incluido y usa `GetFormFields` para ver sus campos.
4. Asigna valores a los campos y lanza `FillFormFields` para generar el PDF relleno.

## 🔗 Repo PowerBuilder

- **Ejemplo PB (modo solución):** <https://github.com/rasanfe/pbPdfFillFormFields>
- **Motor .NET:** <https://github.com/rasanfe/PdfFillFormFields>

---

> ¡Nos vemos en el próximo artículo! Y recuerda: en PowerBuilder, los límites solo están en nuestra imaginación. 🚀

📨 **Blog:** <https://rsrsystem.blogspot.com/>
