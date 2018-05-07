---
title: Kompilatora (poziom 1) ostrzeżenie C4683 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4683
dev_langs:
- C++
helpviewer_keywords:
- C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 418bf25d565c616d5bc4aaf58361c4f28df298ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4683"></a>Kompilator C4683 ostrzegawcze (poziom 1)
**'**   
 ***Funkcja* ": źródło zdarzenia ma"out"-parametru; wskazana jest ostrożność podczas podłączania wielu obsług zdarzeń**  
  
 Jeśli więcej niż jeden obiekt sink zdarzenia nasłuchuje źródło zdarzenia COM, wartość parametru wyjściowego można zignorować.  
  
 Należy pamiętać, że przeciek pamięci będą podejmowane w następującej sytuacji:  
  
1.  Jeśli metoda ma parametr wyjściowy przydzielonej wewnętrznie, na przykład BSTR *.  
  
2.  Jeśli zdarzenie ma więcej niż jednej procedury obsługi (jest to zdarzenie multiemisji)  
  
 Przyczyną przecieku jest aby parametr out zostanie ustawione przez więcej niż jednej procedury obsługi, ale zwracany do wywołania przez ostatnich obsługi.  
  
 Poniższy przykład generuje C4683:  
  
```  
// C4683.cpp  
// compile with: /W1 /LD  
#define _ATL_ATTRIBUTES 1  
#include "atlbase.h"  
#include "atlcom.h"  
  
[ module(name="xx") ];  
  
[ object ]  
__interface I {  
   HRESULT f([out] int* pi);  
   // try the following line instead  
   // HRESULT f(int* pi);  
};  
  
[ coclass, event_source(com) ]  
struct E {  
   __event __interface I;   // C4683  
};  
```