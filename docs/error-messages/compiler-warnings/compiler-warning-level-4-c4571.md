---
title: Kompilatora (poziom 4) ostrzeżenie C4571 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4571
dev_langs:
- C++
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ecd2223baec2d2ff7e743442d0b44e54c8cb05d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4571"></a>Kompilator C4571 ostrzegawcze (poziom 4)
Informacja: semantyka instrukcji catch(...) została zmieniona od czasu Visual C++ 7.1; Wyjątki strukturalne (SEH) nie są już przechwytywane  
  
 C4571 jest generowany dla każdego bloku instrukcji catch(...) została podczas kompilowania za pomocą **/EHS**.  
  
 Podczas kompilowania za pomocą **/EHS**, blok instrukcji catch(...) została nie będzie przechwytywać wyjątków strukturalnych (dzielenie przez zero, pustego wskaźnika, na przykład); instrukcji catch(...) została bloku będą tylko catch jawnie zgłoszony, wyjątków języka C++.  Aby uzyskać więcej informacji, zobacz [obsługi wyjątków](../../cpp/exception-handling-in-visual-cpp.md).  
  
 To ostrzeżenie jest domyślnie wyłączone.  Wyłącz to ostrzeżenie w celu zapewnienia, że podczas kompilowania z **/EHS** Twojego bloków catch (...) nie jest planowane przechwytują wyjątki strukturalne.  Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
 Można rozwiązać C4571 w jednym z następujących sposobów  
  
-   Kompiluj z użyciem **/eha** Aby nadal korzystać z bloków instrukcji catch(...) została przechwytują wyjątki strukturalne.  
  
-   Nie należy włączać C4571, jeśli nie chcesz, aby Twoje bloki instrukcji catch(...) została przechwytują wyjątki strukturalne, ale nadal chcesz używać bloków instrukcji catch(...) została.  Można nadal catch wyjątków strukturalnych za pomocą obsługi słowa kluczowe wyjątków strukturalnych (**__try**, **__except**, i **__finally**).  Jednak należy pamiętać, że podczas kompilacji **/EHS** destruktory będzie wywoływany tylko, gdy zgłoszony wyjątek języka C++ nie po wystąpieniu wyjątku SEH.  
  
-   Zamień bloku instrukcji catch(...) została bloków catch dla określonych wyjątków C++ i opcjonalnie Dodaj obsługi wokół wyjątków C++, obsługa wyjątków strukturalnych (**__try**, **__except**, i **_ _finally**).  Zobacz [strukturalnych obsługi wyjątków (C/C++)](../../cpp/structured-exception-handling-c-cpp.md) Aby uzyskać więcej informacji.  
  
 Zobacz [/EH (Model obsługi wyjątku)](../../build/reference/eh-exception-handling-model.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4571.  
  
```  
// C4571.cpp  
// compile with: /EHs /W4 /c  
#pragma warning(default : 4571)  
int main() {  
   try {  
      int i = 0, j = 1;  
      j /= i;   // this will throw a SE (divide by zero)  
   }  
   catch(...) {}   // C4571 warning  
}  
```