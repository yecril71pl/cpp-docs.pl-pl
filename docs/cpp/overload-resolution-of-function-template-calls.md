---
title: Rozpoznawanie przeciążenia wywołań szablonów funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- function templates overload resolution
ms.assetid: a2918748-2cbb-4fc6-a176-e256f120bee4
ms.openlocfilehash: a736e89565bb7ab6bc49c3c0f65d12fc9508200c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484269"
---
# <a name="overload-resolution-of-function-template-calls"></a>Rozpoznawanie przeciążenia wywołań szablonów funkcji

Szablon funkcji może doprowadzić do przeciążenia funkcji nieszablonu o takiej samej nazwie. W tym scenariuszu wywołania funkcji są rozwiązywane przez pierwszy przy użyciu odliczanie argumentu szablon do tworzenia wystąpienia szablonu funkcji przy użyciu unikatowych specjalizacji. W przypadku niepowodzenia odliczanie argumentu szablon przeciążeń funkcji są traktowane jako wywołanie rozpoznawania. Te inne przeciążenia, zestaw Release candidate, nazywana również obejmują funkcje nieszablonu i innych szablonów wystąpień funkcji. Jeśli odliczanie argumentu szablon zakończy się powodzeniem, generowanej funkcji jest porównywana z innych funkcji, aby określić najlepsze dopasowanie, zgodnie z regułami dla rozwiązania przeciążenia. Aby uzyskać więcej informacji, zobacz [przeciążanie funkcji](function-overloading.md).

## <a name="example"></a>Przykład

Jeśli funkcja nieszablonu jest równie dobre dopasowanie do funkcji szablonu, funkcja nieszablonu zostanie wybrana (chyba że wyraźnie określono argumentów szablonu), ponieważ w wywołaniu `f(1, 1)` w poniższym przykładzie.

```cpp
// template_name_resolution9.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

void f(int, int) { cout << "f(int, int)" << endl; }
void f(char, char) { cout << "f(char, char)" << endl; }

template <class T1, class T2>
void f(T1, T2)
{
   cout << "void f(T1, T2)" << endl;
};

int main()
{
   f(1, 1);   // Equally good match; choose the nontemplate function.
   f('a', 1); // Chooses the template function.
   f<int, int>(2, 2);  // Template arguments explicitly specified.
}
```

```Output
f(int, int)
void f(T1, T2)
void f(T1, T2)
```

## <a name="example"></a>Przykład

W następnym przykładzie pokazano, dokładnie pasujących funkcji szablonu jest preferowana, jeśli funkcja nieszablonu wymaga konwersji.

```cpp
// template_name_resolution10.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

void f(int, int) { cout << "f(int, int)" << endl; }

template <class T1, class T2>
void f(T1, T2)
{
   cout << "void f(T1, T2)" << endl;
};

int main()
{
   long l = 0;
   int i = 0;
   // Call the template function f(long, int) because f(int, int)
   // would require a conversion from long to int.
   f(l, i);
}
```

```Output
void f(T1, T2)
```

## <a name="see-also"></a>Zobacz także

[Rozpoznawanie nazw](../cpp/templates-and-name-resolution.md)<br/>
[typename](../cpp/typename.md)