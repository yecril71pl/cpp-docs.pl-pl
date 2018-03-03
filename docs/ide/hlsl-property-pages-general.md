---
title: "Strony właściwości HLSL: Ogólne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EntryPointName
dev_langs:
- C++
ms.assetid: 0e02f2a6-f123-43da-b04b-a0719a7c2b03
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: be548966f6e75afde2c137c8beab38903844667c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="hlsl-property-pages-general"></a>Strony właściwości HLSL: ogólne
Aby skonfigurować następujące właściwości kompilatora HLSL (fxc.exe), użyj jej **ogólne** strony właściwości. Aby uzyskać informacje dotyczące dostępu do **ogólne** zobacz stronę właściwości w folderze HLSL [Praca z właściwościami projektu](../ide/working-with-project-properties.md).  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Dodatkowe katalogi dołączenia**  
 Dodaje co najmniej jeden katalog do ścieżki dołączenia. Użyj średników do oddzielania katalogów.  
  
 Ta właściwość odpowiada **/I [ścieżka]** argumentu wiersza polecenia.  
  
 **Nazwa punktu wejścia**  
 Określa punkt wejścia do programu do cieniowania. Domyślna wartość to **głównego**.  
  
 Ta właściwość odpowiada **/E [nazwa]** argumentu wiersza polecenia.  
  
 **Wyłącz optymalizacje**  
 **Tak (/ Od)** wyłączyć optymalizacje; w przeciwnym razie **nr**. Domyślna wartość to **tak (/ Od)** dla **debugowania** konfiguracji i **nr** dla **wersji** konfiguracji.  
  
 **/Od** argument wiersza polecenia kompilatora HLSL niejawnie stosuje **/gfp** argumentu wiersza polecenia, ale dane wyjściowe może nie być identyczny z danych wyjściowych wytworzonego przez przekazanie zarówno **/Od**  i **/gfp** argumenty wiersza polecenia jawnie.  
  
 **Włącz informacje debugowania**  
 **Tak (/Zi)** informacji debugowania; w przeciwnym razie **nr**. Domyślna wartość to **tak (/Zi)** dla **debugowania** konfiguracji i **nr** dla **wersji** konfiguracji.  
  
 **Typ programu do cieniowania**  
 Określa typ cieniowania. Różne rodzaje programów do cieniowania implementuje różnych części potoku grafiki. Niektóre rodzaje programów do cieniowania są dostępne tylko w bardziej najnowszymi modelami programu cieniującego (które są określone przez **Shader Model** właściwości) — na przykład obliczeniowe programów do cieniowania zostały wprowadzone w modelu cieniowania 5.  
  
 Ta właściwość odpowiada **[typ]** część **_ /T [typ], [model]** argument wiersza polecenia kompilatora HLSL. **Modelami programu cieniującego** właściwość określa **[model]** część argumentu.  
  
 **Model programu do cieniowania**  
 Określa model programu do cieniowania. Modele innego programu do cieniowania mają różne możliwości. Ogólnie rzecz biorąc więcej najnowszymi modelami programu cieniującego oferuje rozszerzone możliwości, ale wymaga więcej nowoczesnego sprzętu grafiki do uruchomienia kodu programu do cieniowania. Niektóre rodzaje programów do cieniowania (określonej przez **programu do cieniowania typu** właściwości) są dostępne tylko w bardziej najnowszymi modelami programu cieniującego — na przykład obliczeniowe programów do cieniowania zostały wprowadzone w modelu cieniowania 5.  
  
 Ta właściwość odpowiada **[model]** część **_ /T [typ], [model]** argument wiersza polecenia kompilatora HLSL. **Programu do cieniowania typu** właściwość określa **[typ]** część argumentu.  
  
 **Definicje preprocesora**  
 Dodaje jednego lub więcej definicji symboli preprocesora do zastosowania do pliku kodu źródłowego HLSL. Użyj średników do oddzielania definicji symbolu.  
  
 Ta właściwość odpowiada **/D [definicje]** argument wiersza polecenia kompilatora HLSL.  
  
## <a name="see-also"></a>Zobacz też  
 [Strony właściwości HLSL](../ide/hlsl-property-pages.md)   
 [Strony właściwości HLSL: Zaawansowane](../ide/hlsl-property-pages-advanced.md)   
 [Strony właściwości HLSL: pliki wyjściowe](../ide/hlsl-property-pages-output-files.md)