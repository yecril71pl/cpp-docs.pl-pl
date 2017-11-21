---
title: "-Zc: forScope (Wymuszaj zgodność w zakresie pętli for) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.ForceConformanceInForLoopScope
- VC.Project.VCCLWCECompilerTool.ForceConformanceInForLoopScope
- /zc:forScope
dev_langs: C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: 3031f02d-3b14-4ad0-869e-22b0110c3aed
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 72595581e5054630e761f214c1a30c139fb7b69b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="zcforscope-force-conformance-in-for-loop-scope"></a>/Zc:forScope (Wymuszaj zgodność w zakresie pętli For)
Używane do implementowania standardowego zachowania C++ dla [dla](../../cpp/for-statement-cpp.md) pętle z rozszerzeniami firmy Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).  **/ Zc: forscope** jest domyślnie włączone.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Zc:forScope[-]  
```  
  
## <a name="remarks"></a>Uwagi  
 **/Zc:forScope-** opcja jest przestarzała i zostanie usunięta w przyszłej wersji. Użycie **/Zc:forScope-** generuje ostrzeżenie D9035 wycofywanie.  
  
 Standardowe zachowanie jest umożliwienie **dla** inicjatora pętli się znaleźć poza zakresem po **dla** pętli. W obszarze **/Zc:forScope-** i [/Ze](../../build/reference/za-ze-disable-language-extensions.md), **dla** inicjatora pętli pozostaje w zakresie do czasu zakończenia zakresu lokalnego.  
  
 Kompiluje następujący kod pod **/Ze** , ale nie w obszarze **/Za**:  
  
```cpp  
// zc_forScope.cpp  
// compile by using: cl /Zc:forScope- /Za zc_forScope.cpp  
// C2065, D9035 expected  
int main() {  
    // Compile by using cl /Zc:forScope- zc_forScope.cpp  
    // to compile this non-standard code as-is.  
    // Uncomment the following line to resolve C2065 for /Za.  
    // int i;  
    for (int i = 0; i < 1; i++)  
        ;  
    i = 20;   // i has already gone out of scope under /Za  
}  
```  
  
 Jeśli używasz **/Zc:forScope-**, ostrzeżenie C4288 (domyślnie wyłączone) jest generowany, gdy zmienna znajduje się w zakresie z powodu deklaracji, która została wprowadzona w poprzednim zakresu. Aby to wykazać, Usuń `//` znaków w przykładowym kodzie Aby zadeklarować `int i`.  
  
 Można zmodyfikować zachowanie środowiska wykonawczego **/Zc: forscope** za pomocą [jest zgodna z](../../preprocessor/conform.md) pragma.  
  
 Jeśli używasz **/Zc:forScope-** w projekcie ma istniejącego pliku .pch, ostrzeżenie jest generowany, **/Zc:forScope-** jest ignorowany i kompilacji będzie kontynuowane przy użyciu istniejących .pch — pliki. Jeśli chcesz wygenerować nowy plik .pch użyj [/Yc (Utwórz prekompilowany plik nagłówka)](../../build/reference/yc-create-precompiled-header-file.md).  
  
 Aby uzyskać więcej informacji na temat problemów zgodności w programie Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  W okienku nawigacji otwórz **właściwości konfiguracji**, **C/C++**, **języka** strony właściwości.  
  
3.  Modyfikowanie **Wymuszaj zgodność w dla zakresu pętli** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForceConformanceInForLoopScope%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/Zc (zgodność)](../../build/reference/zc-conformance.md)   
 [/ Za, /Ze (Wyłącz rozszerzenia językowe)](../../build/reference/za-ze-disable-language-extensions.md)