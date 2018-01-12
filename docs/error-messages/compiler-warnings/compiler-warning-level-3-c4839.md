---
title: "Kompilatora (poziom 3) ostrzeżenie C4839 | Dokumentacja firmy Microsoft"
ms.date: 10/25/2017
ms.technology: cpp-tools
ms.topic: error-reference
f1_keywords: C4839
dev_langs: C++
helpviewer_keywords: C4839
ms.assetid: f4f99066-9258-4330-81a8-f4a75a1d95ee
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aee1e564ffd72b9b08d883c94311c2bca72b5aef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4839"></a>Kompilator C4839 ostrzegawcze (poziom 4)

> Użycie niestandardowej klasy*typu*"jako argument do funkcji ze zmienną liczbą argumentów

W programie Visual Studio 2017 r, klasy lub struktury, które są przekazywane do ze zmienną liczbą argumentów funkcji takich jak `printf` musi być trivially copyable. Podczas przekazywania takie obiekty, kompilator po prostu tworzy kopię bitowe i nie mogą wywoływać konstruktora lub destruktora.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4839:

```cpp
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function
                        // note: the constructor and destructor will not be called; 
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function

    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);
    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                      // as an argument to a variadic function
}
```

Aby naprawić błąd, można wywołać funkcji członkowskiej zwracającej typu trivially copyable

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

Możesz też wykonać rzutowania statycznego, aby przekonwertować obiekt przed przekazaniem go:

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

Ciągi wbudowane i zarządzane przy użyciu `CStringW`, dostępnego `operator LPCWSTR()` powinien być używany do rzutowania `CStringW` obiektu na wskaźnik C oczekiwany przez ciąg formatu.

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```