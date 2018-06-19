---
title: Kompilatora (poziom 1) ostrzeżenie C4186 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4186
dev_langs:
- C++
helpviewer_keywords:
- C4186
ms.assetid: caf3f7d8-f305-426b-8d4e-2b96f5c269ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc40d2b9f43d041c7b04ba2bc77a0aba0630274c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277595"
---
# <a name="compiler-warning-level-1-c4186"></a>Kompilator C4186 ostrzegawcze (poziom 1)
\#Atrybut import "attribute" wymaga argumentów, liczba; ignorowane  
  
 A `#import` atrybut ma nieprawidłową liczbę argumentów.  
  
## <a name="example"></a>Przykład  
  
```  
// C4186.cpp  
// compile with: /W1 /c  
#import "stdole2.tlb" no_namespace("abc") rename("a","b","c")  // C4186  
```  
  
 `no_namespace` Atrybutu nie przyjmuje żadnych argumentów. **Zmienić** atrybut przyjmuje tylko dwa argumenty.