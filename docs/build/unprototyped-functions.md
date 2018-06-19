---
title: Funkcje bez Pierwowzoru | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df159942832479807b2dfe2679e709292ff3f44b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380475"
---
# <a name="unprototyped-functions"></a>Funkcje bez pierwowzoru
Nie w pełni prototypowanych funkcji wywołujący przechodzą wartości całkowitych jako liczb całkowitych i zmiennoprzecinkowych wartości jako podwójnej precyzji. Tylko wartości zmiennoprzecinkowych, zarówno rejestru całkowitą i zmiennoprzecinkowa rejestr będzie zawierał wartości typu float w przypadku, gdy wywoływany oczekuje, że wartość w rejestrach liczby całkowitej.  
  
```  
func1();  
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7  
   func1(2, 1.0, 7);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencja wywoływania](../build/calling-convention.md)