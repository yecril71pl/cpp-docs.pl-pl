---
title: Kompilator ostrzeżenie (poziom 1) C4838 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- C4838
dev_langs:
- C++
helpviewer_keywords:
- C4838
ms.assetid: fea07924-5feb-4ed4-99b5-1a8c41d28db6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1335d9c36f6764b54689a8334a91f11275ee3265
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025454"
---
# <a name="compiler-warning-level-1-c4838"></a>Kompilator ostrzeżenie (poziom 1) C4838

Konwersja z 'typ_1' na 'typ_2' wymaga konwersji zawężającej

Niejawna konwersja zawężająca został znaleziony podczas przy użyciu inicjowania agregacji lub listy.

Niejawne konwersje zawężające przypisania i inicjowania zezwala na języka C i C++ następuje koloru, nawet jeśli nieoczekiwane zawężanie jest przyczyna wielu błędów kodu. Aby wprowadzić kod bezpieczniejsze, C++ standard wymaga komunikat diagnostyczny, gdy konwersja zawężająca występuje na liście inicjowania. W programie Visual C++ jest diagnostyczne [błąd kompilatora C2397](../../error-messages/compiler-errors-1/compiler-error-c2397.md) podczas przy użyciu składni jednolite inicjowanie obsługiwane począwszy od programu Visual Studio 2015. Kompilator generuje ostrzeżenie C4838, korzystając z listy lub inicjowania agregacji przypadki składni obsługiwanej przez program Visual Studio 2013.

Konwersja zawężająca może być akceptowalne, gdy wiesz, że zakres możliwych wartości przekonwertowanego mieści się w elemencie docelowym. W takim przypadku możesz dowiedzieć się więcej niż kompilator. Jeśli konwersja zawężająca celowo, tworzyć zamiaru jawne przy użyciu rzutowania statycznego. W przeciwnym razie ten komunikat ostrzegawczy prawie zawsze oznacza, że usterka w kodzie. Możesz ją naprawić, upewniając się, że obiekty, które należy zainicjować mają typy, które są wystarczająco duży, aby obsługiwać dane wejściowe.

Poniższy przykład generuje C4838 i pokazano jeden ze sposobów, aby rozwiązać ten problem:

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