---
title: -IMPORTS (DUMPBIN) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /imports
dev_langs: C++
helpviewer_keywords:
- IMPORTS dumpbin option
- /IMPORTS dumpbin option
- -IMPORTS dumpbin option
ms.assetid: 6a296216-2b1b-40f8-8736-cd4553a22456
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e395896c7f595780b1bb6b667d53d4e3eb5fa2ce
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="imports-dumpbin"></a>/IMPORTS (DUMPBIN)
```  
/IMPORTS[:file]  
```  
  
 Ta opcja powoduje wyświetlenie listy bibliotek DLL (zarówno statycznie połączone i [opóźnienie załadować](../../build/reference/linker-support-for-delay-loaded-dlls.md)) który są importowane do pliku wykonywalnego lub biblioteki DLL i wszystkie Importy poszczególnych z każdej z tych bibliotek DLL.  
  
 Opcjonalny `file` specyfikacji umożliwia określenie, będą wyświetlane imports dla tylko tej biblioteki DLL. Na przykład:  
  
```  
dumpbin /IMPORTS:msvcrt.dll  
```  
  
## <a name="remarks"></a>Uwagi  
 Wynik wyświetlany przez ta opcja jest podobny do [/EKSPORTUJE](../../build/reference/dash-exports.md) danych wyjściowych.  
  
 Tylko [/HEADERS](../../build/reference/headers.md) — opcja polecenia DUMPBIN jest dostępny do użytku na pliki tworzone z [/GL](../../build/reference/gl-whole-program-optimization.md) — opcja kompilatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje DUMPBIN](../../build/reference/dumpbin-options.md)