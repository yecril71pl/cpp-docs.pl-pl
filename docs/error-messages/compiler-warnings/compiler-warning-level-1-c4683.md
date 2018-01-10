---
title: "Kompilatora (poziom 1) ostrzeżenie C4683 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4683
dev_langs: C++
helpviewer_keywords: C4683
ms.assetid: e6e77364-dba1-46dd-ae1d-03da23070bce
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e0a8ca498a3c95a1b37229f6ac973cf74a8e28ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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