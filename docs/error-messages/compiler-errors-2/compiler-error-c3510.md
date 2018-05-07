---
title: C3510 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3510
dev_langs:
- C++
helpviewer_keywords:
- C3510
ms.assetid: c48387bc-0300-4a4d-97f7-3fb90f82a451
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abb58d8d4fb9008b07579ef7fbc0066d00bcea57
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3510"></a>C3510 błąd kompilatora
Nie można zlokalizować biblioteki typie zależnym "type_lib"  
  
 [no_registry](../../preprocessor/no-registry.md) i [auto_search —](../../preprocessor/auto-search.md) zostały przekazane do `#import` , ale kompilator nie mógł odnaleźć biblioteki typu występującego w odwołaniu.  
  
 Aby rozwiązać ten problem, upewnij się, że wszystkie biblioteki typu i typu występującego w odwołaniu biblioteki są dostępne do kompilatora.  
  
 Poniższy przykład generuje C3510:  
  
 Założono, że zostały zbudowane następujące dwa typy biblioteki i że C3510a.tlb został usunięty lub nie w ścieżce.  
  
```  
// C3510a.idl  
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]  
library C3510aLib  
{  
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12c")]  
   enum E_C3510  
   {  
      one, two, three  
   };  
};  
```  
  
 A następnie kod źródłowy dla drugiego biblioteki typów:  
  
```  
// C3510b.idl  
// post-build command: del /f C3510a.tlb  
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]  
library C3510bLib  
{  
   importlib ("C3510a.tlb");  
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]  
   struct S_C3510 {  
      enum E_C3510 e;  
   };  
};  
```  
  
 A następnie kod klienta:  
  
```  
// C3510.cpp  
#import "c3510b.tlb" no_registry auto_search   // C3510  
int main() {  
   C3510aLib::S_C4336 ccc;  
}  
```