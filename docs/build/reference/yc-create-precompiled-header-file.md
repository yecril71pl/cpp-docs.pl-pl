---
title: "-Yc (Utwórz prekompilowany plik nagłówka) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.UsePrecompiledHeader
- /yc
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough
- VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader
- VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough
dev_langs: C++
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- .pch files, creating
- -Yc compiler option [C++]
- /Yc compiler option [C++]
- Yc compiler option [C++]
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 865b5e0fa7039a0b60f524c2f13a367569757d92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="yc-create-precompiled-header-file"></a>/Yc (Utwórz prekompilowany plik nagłówka)
Instruuje kompilator, aby utworzyć plik prekompilowanego nagłówka (.pch), który reprezentuje stan kompilacji w określonym punkcie.  
  
## <a name="syntax"></a>Składnia  
  
> __/Yc__
> __/Yc__*filename*  
  
  
## <a name="arguments"></a>Argumenty  
*Nazwa pliku*  
 Określa plik nagłówków (.h). Jeśli ten argument jest używany, kompilator kompiluje całego kodu, w tym pliku .h.  
  
## <a name="remarks"></a>Uwagi  
 Gdy **/Yc** został określony bez argumentu, kompilator kompiluje cały kod do końca pliku źródłowego podstawowej lub do punktu w pliku podstawowego gdzie [hdrstop](../../preprocessor/hdrstop.md) występuje dyrektywy. Wynikowy plik .pch ma taką samą nazwę podstawowej jako pliku źródłowego podstawowej, chyba że zostanie określony, nazwa inny plik za pomocą **hdrstop** pragma lub **/FP** opcji.  
  
 Prekompilowany kod jest zapisywany w pliku o nazwie utworzone z podstawowej nazwy pliku określony za pomocą **/Yc** opcja i rozszerzenia .pch. Można również użyć [/Fp (nazwa. Plik pch)](../../build/reference/fp-name-dot-pch-file.md) opcję, aby określić nazwę dla prekompilowanego pliku nagłówkowego.  
  
 Jeśli używasz __/Yc__*filename*, kompilator kompiluje całego kodu, w tym określony plik dla kolejnych [/Yu (Użyj Prekompilowanego pliku nagłówka)](../../build/reference/yu-use-precompiled-header-file.md) opcji.  
  
 Jeśli opcje __/Yc__*filename* i __/Yu__*filename* występować w jednym wierszu polecenia i oba odwołania lub oznaczać taką samą nazwę, __/Yc__*filename* pierwszeństwo. Ta funkcja ułatwia zapisywanie pliki reguł programu make.  
  
 Aby uzyskać więcej informacji o prekompilowanych nagłówków zobacz:  
  
-   [/Y (Prekompilowane nagłówki)](../../build/reference/y-precompiled-headers.md)  
  
-   [Tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Wybierz plik .cpp. Plik .cpp może #include pliku .h, który zawiera informacje o prekompilowanego nagłówka. Projektu **/Yc** ustawienie można zastąpić na poziomie plików.  
  
2.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
3.  Otwórz **właściwości konfiguracji**, **C/C++**, **prekompilowanych nagłówków** strony właściwości.  
  
4.  Modyfikowanie **Prekompilowanego nagłówka** właściwości.  
  
5.  Aby ustawić nazwę pliku, należy zmodyfikować **Prekompilowanego pliku nagłówka** właściwości.
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.  
  
## <a name="example"></a>Przykład  
 Rozważmy następujący kod:  
  
```cpp  
// prog.cpp
// compile with: cl /c /Ycmyapp.h prog.cpp
#include <afxwin.h>   // Include header for class library  
#include "resource.h" // Include resource definitions  
#include "myapp.h"    // Include information specific to this app  
// ...  
```  
  
Gdy ten kod jest skompilowana przy użyciu polecenia `CL /YcMYAPP.H PROG.CPP`, kompilator zapisuje wszystkie przetwarzania wstępnego dla AFXWIN.h, RESOURCE.h, i MYAPP.h w pliku prekompilowany nagłówek o nazwie MYAPP.pch.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md) [tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md)