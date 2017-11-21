---
title: "Kompilatora (poziom 1) ostrzeżenie C4838 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4838
dev_langs: C++
helpviewer_keywords: C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 227af1840fe5aee63545e35456fe09749f00de1d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4838"></a>Kompilator C4838 ostrzegawcze (poziom 1)
Konwersja z "type_1" na "type_2" wymaga konwersji zawężającej  
  
 Niejawnej konwersji zawężającej został znaleziony, gdy przy użyciu inicjowania agregacji lub na liście.  
  
 Niejawnych konwersji zawężającej przydziałów i inicjowania umożliwia języka C i C++ następuje koloru, nawet jeśli nieoczekiwany zawężanie jest przyczyną wiele błędów kodu. Aby wprowadzić kod bezpieczniejsze, C++ standard wymaga komunikatów diagnostycznych podczas konwersji zawężającej występuje na liście inicjowania. W programie Visual C++, Diagnostyka jest [C2397 błąd kompilatora](../../error-messages/compiler-errors-1/compiler-error-c2397.md) Jeśli używana jest składnia jednolite inicjowanie obsługiwane począwszy od programu Visual Studio 2015. Kompilator generuje ostrzeżenie C4838, korzystając z listy lub składnia inicjalizacji agregacji obsługiwane przez Visual Studio 2013.  
  
 Konwersji zawężającej mogą być poprawny, gdy wiesz, że możliwej wartości przekonwertowane zmieści się w celu. W takim przypadku możesz dowiedzieć się więcej niż kompilatora. Jeśli dokonujesz konwersji zawężającej celowo, wprowadzać zamiaru jawne za pomocą rzutowania statycznego. W przeciwnym razie ten komunikat ostrzegawczy prawie zawsze oznacza, że usterki w kodzie. Można go rozwiązać, upewniając się, że obiekty, które należy zainicjować mają typy, które są wystarczająco duża do obsługi danych wejściowych.  
  
 Poniższy przykład generuje C4838 i przedstawia sposób rozwiązywanie problemu:  
  
```  
// C4838.cpp -- C++ narrowing conversion diagnostics  
// Compile by using: cl /EHsc C4838.cpp  
  
struct S1 {  
    int m1;  
    double m2, m3;  
};  
  
void function_C4838(double d1) {  
    double ad[] = { 1, d1 }; // OK  
    int ai[] = { 1, d1 };    // warning C4838  
    S1 s11 = { 1, 2, d1 };   // OK  
    S1 s12 { d1, 2, 3 };     // warning C4838  
    S1 s13 { static_cast<int>(d1), 2, 3 }; // possible fix for C4838  
}  
```