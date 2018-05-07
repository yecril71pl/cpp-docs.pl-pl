---
title: C2397 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- C2397
dev_langs:
- C++
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9d080450368618cc874de0ae96209e547847f8c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2397"></a>C2397 błąd kompilatora
Konwersja z "type_1" na "type_2" wymaga konwersji zawężającej  
  
 Znaleziono niejawnej konwersji zawężającej przy użyciu jednolite inicjowanie.  
  
 Niejawnych konwersji zawężającej przydziałów i inicjowania umożliwia języka C i C++ następuje koloru, nawet jeśli nieoczekiwany zawężanie jest przyczyną wiele błędów kodu. Aby wprowadzić kod bezpieczniejsze, C++ standard wymaga komunikatów diagnostycznych podczas konwersji zawężającej występuje na liście inicjowania. W programie Visual C++ Diagnostyka jest C2397 błąd kompilatora, używając jednolite inicjowanie początku składni obsługiwane w programie Visual Studio 2015. Kompilator generuje [C4838 ostrzeżenie kompilatora (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md) podczas korzystania z listy lub składnia inicjalizacji agregacji obsługiwane przez Visual Studio 2013.  
  
 Konwersji zawężającej mogą być poprawny, gdy wiesz, że możliwej wartości przekonwertowane zmieści się w celu. W takim przypadku możesz dowiedzieć się więcej niż kompilatora. Jeśli dokonujesz konwersji zawężającej celowo, wprowadzać zamiaru jawne za pomocą rzutowania statycznego. W przeciwnym razie ten komunikat o błędzie prawie zawsze wskazuje, że masz usterki w kodzie. Można go rozwiązać, upewniając się, że obiekty, które należy zainicjować mają typy, które są wystarczająco duża do obsługi danych wejściowych.  
  
 Poniższy przykład generuje C2397 i przedstawia sposób rozwiązywanie problemu:  
  
```  
// C2397.cpp -- C++ narrowing conversion diagnostics  
// Compile by using: cl /EHsc C2397.cpp  
#include <vector>   
  
struct S1 {  
    int m1;  
    double m2, m3;  
};  
  
void function_C2397(double d1) {  
    char c1 { 127 };          // OK  
    char c2 { 513 };          // error C2397  
  
    std::vector<S1> vS1;  
    vS1.push_back({ d1, 2, 3 }); // error C2397  
  
    // Possible fix if you know d1 always fits in an int  
    vS1.push_back({ static_cast<int>(d1), 2, 3 });   
}  
```