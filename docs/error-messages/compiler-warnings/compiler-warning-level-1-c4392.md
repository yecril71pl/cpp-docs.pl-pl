---
title: Kompilatora (poziom 1) ostrzeżenie C4392 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4392
dev_langs:
- C++
helpviewer_keywords:
- C4392
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b64159737b9423f3d9ea55489eb28c20a2162d14
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4392"></a>Kompilator C4392 ostrzegawcze (poziom 1)
"sygnatura": Nieprawidłowa liczba argumentów dla wewnętrznej funkcji, oczekiwano "number" argumentów  
  
 Deklaracja funkcji wewnętrznych kompilatora ma złą liczbą argumentów. Obraz wynikowy może nie działać poprawnie.  
  
 Aby usunąć to ostrzeżenie, popraw deklarację albo usuń deklarację i po prostu #include plik odpowiedniego nagłówka.  
  
 Poniższy przykład generuje C4392:  
  
```  
// C4392.cpp  
// compile with: /W1  
// processor: x86  
// uncomment the following line and delete the line that  
// generated the warning to resolve  
// #include "xmmintrin.h"  
  
#ifdef  __cplusplus  
extern "C" {  
#endif  
  
extern void _mm_stream_pd(double *dp);   // C4392  
  
#ifdef  __cplusplus  
}  
#endif  
  
int main()  
{  
}  
```