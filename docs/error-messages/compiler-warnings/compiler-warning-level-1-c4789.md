---
title: Ostrzeżenie kompilatora (poziom 1) C4789
ms.date: 03/25/2019
f1_keywords:
- C4789
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
ms.openlocfilehash: 36278615631d017db1d1c2fc4eecf8c1612892de
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518403"
---
# <a name="compiler-warning-level-1-c4789"></a>Ostrzeżenie kompilatora (poziom 1) C4789

> bufor "*Identyfikator*" o rozmiarze *N* bajtów zostanie przepełniony; *M* bajtów zostanie zapisany, rozpoczynając od przesunięcia *L*

## <a name="remarks"></a>Uwagi

**C4789** ostrzega o przepełnieniu buforów, gdy używane są określone funkcje środowiska uruchomieniowego C (CRT). Może również zgłosić niezgodność rozmiaru, gdy parametry są przekazywane lub są wykonywane przypisania. Ostrzeżenie jest możliwe, jeśli rozmiary danych są znane w czasie kompilacji. To ostrzeżenie dotyczy sytuacji, w których może być elude typowe wykrywanie niezgodności rozmiaru danych.

**C4789** ostrzega, gdy dane są kopiowane do bloku danych, który jest znany jako za mały w czasie kompilacji.

Ostrzeżenie występuje, jeśli kopia używa wewnętrznej formy jednej z następujących funkcji CRT:

- [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)

- [memset](../../c-runtime-library/reference/memset-wmemset.md)

- [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md), [wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)

Ostrzeżenie jest również wyświetlane w przypadku rzutowania parametru na większy typ danych, a następnie przypisywania kopii z odwołania lvalue.

Wizualizacja C++ może generować to ostrzeżenie dla ścieżki kodu, która nigdy nie jest wykonywana. Możesz tymczasowo wyłączyć ostrzeżenie przy użyciu `#pragma`, jak pokazano w tym przykładzie:

```cpp
#pragma warning( push )
#pragma warning( disable : 4789 )
// unused code that generates compiler warning C4789`
#pragma warning( pop )
```

Ta idiom uniemożliwia wizualizację C++ generowanie ostrzeżenia dla określonego bloku kodu. `#pragma warning(push)` zachowuje istniejący stan przed zmianą `#pragma warning(disable: 4789)`. `#pragma warning(pop)` przywraca stan pushd i usuwa efekty `#pragma warning(disable:4789)`. Aby uzyskać więcej informacji na C++ temat dyrektywy preprocesora `#pragma`, zobacz dyrektywy [Warning](../../preprocessor/warning.md) i [pragma oraz słowo kluczowe __pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C4789.

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

int main()
{
   int * p = (int *)&G;
   *p = 3;   // C4789 - writes an int through a pointer to short
}
```
