---
title: -Fx (Scalaj wprowadzony kod) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExpandAttributedSource
- /Fx
- VC.Project.VCCLCompilerTool.ExpandAttributedSource
dev_langs: C++
helpviewer_keywords:
- Fx compiler option [C++]
- -Fx compiler option [C++]
- injected code
- merging injected code
- /Fx compiler option [C++]
ms.assetid: 14f0e301-3bab-45a3-bbdf-e7ce66f20560
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 344d9ded0cdb77abfc2fa53ab4180f2e484b7dc9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fx-merge-injected-code"></a>/Fx (Scalaj wprowadzony kod)
Tworzy kopię każdego pliku źródłowego z wprowadzony kod scalone w źródle.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Fx  
```  
  
## <a name="remarks"></a>Uwagi  
 Aby odróżnić plik źródłowy scalone z oryginalnego pliku źródłowego, **/Fx** dodaje rozszerzenie .mrg między nazwę pliku i rozszerzenie pliku. Na przykład plik o nazwie MyCode.cpp oparte na atrybutach kodem i skompilowanej za pomocą **/Fx** tworzy plik o nazwie MyCode.mrg.cpp zawierający następujący kod:  
  
```  
//+++ Start Injected Code  
[no_injected_text(true)];      // Suppress injected text, it has   
                               // already been injected  
#pragma warning(disable: 4543) // Suppress warnings about skipping   
                               // injected text  
#pragma warning(disable: 4199) // Suppress warnings from attribute   
                               // providers  
//--- End Injected Code  
```  
  
 W pliku .mrg kod, który zostało spowodowane z powodu atrybut będzie przecinkami w następujący sposób:  
  
```  
//+++ Start Injected Code  
...  
//--- End Injected Code  
```  
  
 [No_injected_text](../../windows/no-injected-text.md) atrybutu jest osadzony w pliku .mrg, dzięki czemu dla kompilacji pliku .mrg bez tekstu jest reinjected.  
  
 Należy pamiętać, że plik źródłowy .mrg ma być reprezentację kodu źródłowego wstrzyknięte przez kompilator. Plik .mrg nie może skompilować lub uruchom dokładnie jako oryginalnego pliku źródłowego.  
  
 Makra nie zostaną rozwinięte w pliku .mrg.  
  
 Jeśli program zawiera nagłówek pliku, która używa wprowadzony kod **/Fx** generuje. plik mrg.h dla tego nagłówka. **/FX** scalania nie ma plików, które nie korzystają z wprowadzony kod.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **pliki wyjściowe** strony właściwości.  
  
4.  Modyfikowanie **Rozwiń źródło przypisanych** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExpandAttributedSource%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Plik wyjściowy (/ F) opcje](../../build/reference/output-file-f-options.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)