---
title: "-Gm (minimalna ponowna kompilacja Włącz) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- /FD
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
dev_langs: C++
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8bc9ff065de2b83d50b6fa905fcc6d1123dbe829
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (Włącz minimalną ponowną kompilację)
Umożliwia minimalną ponowną kompilację, która określa, czy pliki źródłowe C++, które zawierają zmienione definicje klas C++ (przechowywane w plikach nagłówków (.h)) muszą być ponownie kompilowane.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Gm  
```  
  
## <a name="remarks"></a>Uwagi  
 Kompilator przechowuje informacje o zależnościach między pliki źródłowe i definicje klas w pliku projektu .idb podczas pierwszej kompilacji. (Informacje o zależnościach Określa, że plik źródłowy, który jest zależny od definicji klasy, które, a które .h pliku definicji znajduje się w). Kolejne kompiluje umożliwia ustalenie, czy plik źródłowy powinno zostać skompilowane, nawet wtedy, gdy plik .h zmodyfikowane informacje przechowywane w pliku .idb.  
  
> [!NOTE]
>  Minimalna ponowna kompilacja zależy od klasy definicje nie zmienia się między pliki dołączane. Definicje klas musi być globalne dla projektu (powinien istnieć tylko jedna definicja danej klasy), ponieważ informacje o zależnościach w pliku .idb jest tworzone dla całego projektu. Jeśli masz więcej niż jedną definicję klasy w projekcie, wyłącz minimalna ponowna kompilacja.  
  
 Ponieważ konsolidatora przyrostowego nie obsługuje metadanych systemu Windows, uwzględniane w plikach .obj przy użyciu [/ZW (kompilacja środowiska uruchomieniowego systemu Windows)](../../build/reference/zw-windows-runtime-compilation.md) opcji **/GM ponowną** opcja jest niezgodna z  **/Zw**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **generowania kodu** strony właściwości.  
  
4.  Modyfikowanie **włączyć minimalnego odbudować** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)