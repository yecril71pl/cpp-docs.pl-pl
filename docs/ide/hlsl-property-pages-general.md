---
title: 'Strony właściwości HLSL: Ogólne'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EntryPointName
ms.assetid: 0e02f2a6-f123-43da-b04b-a0719a7c2b03
ms.openlocfilehash: cc7c0837def7628414d017a660453915a472318e
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751443"
---
# <a name="hlsl-property-pages-general"></a>Strony właściwości HLSL: Ogólne

Aby skonfigurować następujące właściwości kompilator HLSL (fxc.exe), użyj jej **ogólne** stronę właściwości. Aby uzyskać informacje o tym, jak uzyskać dostęp do **ogólne** zobacz stronę właściwości w folderze HLSL [Praca z właściwościami projektu](../ide/working-with-project-properties.md).

## <a name="uielement-list"></a>Lista elementów UI

- **Dodatkowe katalogi dyrektywy Include**

   Dodaje jeden lub więcej katalogów do ścieżki dołączania. Użyj średników do oddzielenia katalogów.

Ta właściwość odnosi się do **/I [ścieżka]** argument wiersza polecenia.

- **Nazwa punktu wejścia**

   Określa punkt wejścia dla programu do cieniowania. Domyślna wartość to **głównego**.

Ta właściwość odnosi się do **/E [name]** argument wiersza polecenia.

- **Wyłącz optymalizacje**

   **Tak (/ Od)** wyłączyć optymalizacje; w przeciwnym razie **nie**. Domyślna wartość to **tak (/ Od)** dla **debugowania** konfiguracje i **nie** dla **wersji** konfiguracje.

**/Od** stosuje niejawnie argument wiersza polecenia kompilatora HLSL **/gfp** argument wiersza polecenia, ale dane wyjściowe nie może być identyczny z danych wyjściowych, który jest wytwarzany przez przekazanie zarówno **/Od**  i **/gfp** argumenty wiersza poleceń jawnie.

- **Włącz informacje debugowania**

   **Tak (/Zi)** włączyć informacje debugowania; w przeciwnym razie **nie**. Domyślna wartość to **tak (/Zi)** dla **debugowania** konfiguracje i **nie** dla **wersji** konfiguracje.

- **Typ programu do cieniowania**

   Określa typ programu do cieniowania. Różne rodzaje programów do cieniowania implementowania różnych części potoku grafiki. Niektóre rodzaje programów do cieniowania są dostępne tylko w bardziej najnowszymi modelami cieniowania (określonych przez **Model cieniowania** właściwość) — na przykład obliczenia programów do cieniowania zostały wprowadzone w modelu programu do cieniowania 5.

   Ta właściwość odnosi się do  **\[typ]** część **/t \[typ] _\[modelu]** argument wiersza polecenia kompilatora HLSL. **Modelami programów do cieniowania** właściwość określa **[model]** część argumentu.

- **Model cieniowania**

   Określa model cieniowania. Modele innego programu do cieniowania mają różne możliwości. Ogólnie rzecz biorąc bardziej najnowszymi modelami cieniowania oferują rozszerzone możliwości, ale wymagają bardziej nowoczesnego sprzętu grafiki do uruchomienia kodu programu do cieniowania. Niektóre rodzaje programów do cieniowania (określonych przez **typ programu do cieniowania** właściwość) są dostępne tylko w bardziej najnowszymi modelami cieniowania — na przykład obliczenia programów do cieniowania zostały wprowadzone w modelu programu do cieniowania 5.

   Ta właściwość odnosi się do  **\[modelu]** część **/t \[typ] _\[modelu]** argument wiersza polecenia kompilatora HLSL. **Typ programu do cieniowania** właściwość określa **[type]** część argumentu.

- **Definicje preprocesora**

   Dodaje jedną lub więcej definicji symboli preprocesora Aby zastosować do pliku kodu źródłowego języka HLSL. Użyj średników do oddzielenia definicje symbolu.

   Ta właściwość odnosi się do **/D \[definicje]** argument wiersza polecenia kompilatora HLSL.

## <a name="see-also"></a>Zobacz także

[Strony właściwości HLSL](../ide/hlsl-property-pages.md)<br>
[Strony właściwości HLSL: Zaawansowane](../ide/hlsl-property-pages-advanced.md)<br>
[Strony właściwości HLSL: Pliki wyjściowe](../ide/hlsl-property-pages-output-files.md)
