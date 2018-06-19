---
title: Kompilatora (poziom 1) ostrzeżenie C4391 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4391
dev_langs:
- C++
helpviewer_keywords:
- C4391
ms.assetid: 95c6182c-fae9-4174-8f7b-98aa352e68ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0152d6e04d40e3e0389cf51ba7bdf71de4cd4791
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277871"
---
# <a name="compiler-warning-level-1-c4391"></a>Kompilator C4391 ostrzegawcze (poziom 1)
"sygnatura": nieprawidłowy typ zwracany dla wewnętrznej funkcji, oczekiwano "type"  
  
 Deklaracja funkcji wewnętrznych kompilatora ma niewłaściwy typ zwracany. Obraz wynikowy może nie działać poprawnie.  
  
 Aby usunąć to ostrzeżenie, popraw deklarację albo usuń deklarację i po prostu #include plik odpowiedniego nagłówka.  
  
 Poniższy przykład generuje C4391:  
  
```  
// C4391.cpp  
// compile with: /W1  
// processor: x86  
// uncomment the following line and delete the line that  
// generated the warning to resolve  
// #include "xmmintrin.h"  
  
#ifdef  __cplusplus  
extern "C" {  
#endif  
  
extern void _mm_load_ss(float *p);   // C4391  
  
#ifdef  __cplusplus  
}  
#endif  
  
int main()  
{  
}  
```