---
title: Rozpoznawanie przeciążenia wywołań szablonów funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- function templates overload resolution
ms.assetid: a2918748-2cbb-4fc6-a176-e256f120bee4
ms.openlocfilehash: d96046c629e812e342ce86b850b6d52a57094997
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188444"
---
# <a name="overload-resolution-of-function-template-calls"></a>Rozpoznawanie przeciążenia wywołań szablonów funkcji

Szablon funkcji może przeciążać nieszablonowe funkcje o tej samej nazwie. W tym scenariuszu wywołania funkcji są rozwiązywane przez pierwsze użycie odliczania argumentu szablonu w celu utworzenia wystąpienia szablonu funkcji z unikatową specjalizacją. Jeśli potrącenie argumentu szablonu nie powiedzie się, inne przeciążenia funkcji są brane pod uwagę w celu rozpoznania wywołania. Te inne przeciążenia, znane także jako zestaw kandydatów, obejmują funkcje nieszablonowe i inne szablony funkcji z utworzonymi wystąpieniami. Jeśli potrącenie argumentu szablonu powiedzie się, wygenerowana funkcja jest porównywana z innymi funkcjami w celu określenia najlepszego dopasowania, zgodnie z regułami dotyczącymi rozpoznawania przeciążenia. Aby uzyskać więcej informacji, zobacz [przeciążanie funkcji](function-overloading.md).

## <a name="example"></a>Przykład

Jeśli funkcja niebędąca szablonem jest równie dobre dopasowanie do funkcji szablonu, wybierana jest funkcja niebędąca szablonem (chyba że argumenty szablonu zostały jawnie określone), podobnie jak w przypadku wywołania `f(1, 1)` w poniższym przykładzie.

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

W następnym przykładzie pokazano, że preferowana jest dokładna funkcja szablonu, jeśli funkcja niebędąca szablonem wymaga konwersji.

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

## <a name="see-also"></a>Zobacz też

[Rozpoznawanie nazw](../cpp/templates-and-name-resolution.md)<br/>
[typename](../cpp/typename.md)
