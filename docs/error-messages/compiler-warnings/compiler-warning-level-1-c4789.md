---
title: Kompilator ostrzeżenie (poziom 1) C4789
ms.date: 03/25/2019
f1_keywords:
- C4789
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
ms.openlocfilehash: 36a5032098c5caabb1b050833e487fd58679a782
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187234"
---
# <a name="compiler-warning-level-1-c4789"></a>Kompilator ostrzeżenie (poziom 1) C4789

> bufor "*identyfikator*" o rozmiarze *N* bajtów zostanie przepełniony; *M* bajtów zostanie zapisane zaczynając od przesunięcia *L*

## <a name="remarks"></a>Uwagi

**C4789** ostrzega o przepełnienia buforu, stosowania określonych funkcji wykonawczej (CRT) C. Można również raporty niezgodności rozmiar gdy parametry są przekazywane lub przypisania zostały wprowadzone. To ostrzeżenie jest możliwe w przypadku ilości danych, są znane w czasie kompilacji. Ostrzeżenie jest wyświetlane w sytuacjach, które mogą elude wykrywania typowych niezgodność rozmiaru danych.

**C4789** ostrzega, gdy dane są kopiowane do bloku danych, który jest znany będzie zbyt mała w czasie kompilacji.

To ostrzeżenie występuje, gdy kopii używa wewnętrznej postaci jednej z tych funkcji CRT:

- [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)

- [memset](../../c-runtime-library/reference/memset-wmemset.md)

- [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md), [wmemcpy —](../../c-runtime-library/reference/memcpy-wmemcpy.md)

Ostrzeżenie jest wyświetlane, gdy rzutować parametru na większych typ danych, a następnie dokonaj przydzieleniu kopii, z odwołaniem lvalue.

Visual C++ może wygenerować tego ostrzeżenia dla ścieżki kodu, który nigdy nie jest wykonywany. Ostrzeżenie można tymczasowo wyłączyć za pomocą `#pragma`, jak pokazano w poniższym przykładzie:

```cpp
#pragma warning( push )
#pragma warning( disable : 4789 )
// unused code that generates compiler warning C4789`
#pragma warning( pop )
```

Tego idiomu przechowuje Visual C++ z wygenerowane ostrzeżenie dla tego określonego bloku kodu. `#pragma warning(push)` Zachowuje istniejące stan przed wykonaniem `#pragma warning(disable: 4789)` ją zmieni. `#pragma warning(pop)` Przywraca stan wypychanie i usuwa skutki `#pragma warning(disable:4789)`. Aby uzyskać więcej informacji na temat C++ dyrektywy preprocesora `#pragma`, zobacz [ostrzeżenie](../../preprocessor/warning.md) i [dyrektywy Pragma i słowo kluczowe __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4789.

```cpp
// C4789.cpp
// compile with: /Oi /W1 /c
#include <string.h>
#include <stdio.h>

int main()
{
    char a[20];
    strcpy(a, "0000000000000000000000000\n");   // C4789

    char buf2[20];
    memset(buf2, 'a', 21);   // C4789

    char c;
    wchar_t w = 0;
    memcpy(&c, &w, sizeof(wchar_t));
}
```

## <a name="example"></a>Przykład

Poniższy przykład generuje również C4789.

```cpp
// C4789b.cpp
// compile with: /W1 /O2 /c
// processor: x86
short G;

void main()
{
   int * p = (int *)&G;
   *p = 3;   // C4789 - writes an int through a pointer to short
}
```