---
title: Kompilator ostrzeżenie (poziom 1) C4789
ms.date: 11/04/2016
f1_keywords:
- C4789
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
ms.openlocfilehash: f489915f07eefd0909cbcd806a590f93f674c258
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677399"
---
# <a name="compiler-warning-level-1-c4789"></a>Kompilator ostrzeżenie (poziom 1) C4789

> bufor "*identyfikator*" o rozmiarze *N* bajtów zostanie przepełniony; *M* bajtów zostanie zapisane zaczynając od przesunięcia *L*

## <a name="remarks"></a>Uwagi

Ostrzega o buforu przepełnienia, gdy są używane określone funkcje (CRT) środowiska wykonawczego języka C, parametry są przekazywane i przydziały są wykonywane, taki sposób, że rozmiary danych są znane w czasie kompilacji. Ostrzeżenie jest wyświetlane w sytuacjach, które mogą elude wykrywania typowych niezgodność rozmiaru danych.

Ostrzeżenie jest wyświetlane, gdy danych, którego długość jest znany w czas kompilacji, jest kopiowany i umieścić w bloku danych, której rozmiar jest znany w czasie kompilacji będzie zbyt mała dla danych. Kopia musi odbywać się za pomocą formularza wewnętrzne jednego z następujących funkcji CRT:

- [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)

- [memset](../../c-runtime-library/reference/memset-wmemset.md)

- [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md), [wmemcpy —](../../c-runtime-library/reference/memcpy-wmemcpy.md)

Ostrzeżenie jest wyświetlane, gdy typu danych parametru jest niezgodny przy użyciu rzutowania, a następnie jest podejmowana próba przypisania kopiowania, z odwołaniem lvalue.

Visual C++ może wygenerować tego ostrzeżenia dla ścieżki kodu, który nigdy nie jest wykonywane. Ostrzeżenie można tymczasowo wyłączyć za pomocą `#pragma`, jak pokazano w poniższym przykładzie:

```cpp
#pragma(push)
#pragma warning ( disable : 4789 )
// unused code that generates compiler warning C4789`
#pragma(pop)
```

Dzięki temu Visual C++ na generowanie ostrzeżenia dla tego określonego bloku kodu. `#pragma(push)` Zachowuje istniejące stan przed wykonaniem `#pragma warning(disable: 4789)` ją zmieni. `#pragma(pop)` Przywraca stan wypychanie i usuwa skutki `#pragma warning(disable:4789)`. Aby uzyskać więcej informacji na temat dyrektywy preprocesora języka C++ `#pragma`, zobacz [ostrzeżenie](../../preprocessor/warning.md) i [dyrektywy Pragma i słowo kluczowe __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

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