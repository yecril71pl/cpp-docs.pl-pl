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
ms.workload: cplusplus
ms.openlocfilehash: 1866c8d522e7482781aa65e58d93ccb09e6b265f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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