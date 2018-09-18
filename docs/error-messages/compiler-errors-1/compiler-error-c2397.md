---
title: Błąd kompilatora C2397 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: e3e76384ca2509663398fd7abd7badfd4057e8c3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115102"
---
# <a name="compiler-error-c2397"></a>Błąd kompilatora C2397

Konwersja z 'typ_1' na 'typ_2' wymaga konwersji zawężającej

Niejawna konwersja zawężająca został znaleziony, korzystając z jednolite inicjowanie.

Niejawne konwersje zawężające przypisania i inicjowania zezwala na języka C i C++ następuje koloru, nawet jeśli nieoczekiwane zawężanie jest przyczyna wielu błędów kodu. Aby wprowadzić kod bezpieczniejsze, C++ standard wymaga komunikat diagnostyczny, gdy konwersja zawężająca występuje na liście inicjowania. W programie Visual C++ diagnostyczne jest błąd kompilatora C2397 podczas jednolite inicjowanie początku składnia obsługiwana w programie Visual Studio 2015. Kompilator generuje [ostrzeżenie kompilatora (poziom 1) C4838](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md) podczas korzystania z listy lub inicjowania agregacji przypadki składni obsługiwanej przez program Visual Studio 2013.

Konwersja zawężająca może być akceptowalne, gdy wiesz, że zakres możliwych wartości przekonwertowanego mieści się w elemencie docelowym. W takim przypadku możesz dowiedzieć się więcej niż kompilator. Jeśli konwersja zawężająca celowo, tworzyć zamiaru jawne przy użyciu rzutowania statycznego. W przeciwnym razie ten komunikat o błędzie prawie zawsze wskazuje, że masz usterki w kodzie. Możesz ją naprawić, upewniając się, że obiekty, które należy zainicjować mają typy, które są wystarczająco duży, aby obsługiwać dane wejściowe.

Poniższy przykład generuje C2397 i pokazano jeden ze sposobów, aby rozwiązać ten problem:

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