---
title: Na podstawie wskaźników (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __based
- _based
- __based_cpp
dev_langs:
- C++
helpviewer_keywords:
- __based keyword [C++]
- based pointers
- pointers, based
ms.assetid: 1e5f2e96-c52e-4738-8e14-87278681205e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4465cb2965983c37ac9d758e424b58b5ed3304fd
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163611"
---
# <a name="based-pointers-c"></a>Wskaźniki bazowe (C++)

**Microsoft Specific**

**__Based** — słowo kluczowe służy do deklarowania wskaźników oparte na wskaźnikach (wskaźników, które są przesunięcia od istniejących wskaźniki).

## <a name="syntax"></a>Składnia

```

type __based( base ) declarator
```

## <a name="remarks"></a>Uwagi

Wskaźniki oparte wskaźnikiem adresów są jedynymi **__based** — słowo kluczowe prawidłowy w kompilacjach kodu 32-bitową lub 64-bitowych. Dla kompilatora Microsoft 32-bitowa C/C++ wskaźnik bazowy jest 32-bitowego przesunięcia z podstawowego wskaźnika 32-bitowych. Podobnych ograniczeń przechowywane dla 64-bitowego środowiska, gdy wskaźnik bazowy przesunięcie 64-bitowych, od base 64-bitowych.

Jednym z zastosowań wskaźniki oparte na wskaźnikach jest trwały identyfikatorów, które zawierają wskaźniki. Połączonej listy, która składa się z wskaźniki oparte na wskaźnik może można zapisywany na dysku, a następnie ponownie załadowany do innego miejsca w pamięci, za pomocą wskaźników pozostałe prawidłowe. Na przykład:

```cpp
// based_pointers1.cpp
// compile with: /c
void *vpBuffer;
struct llist_t {
   void __based( vpBuffer ) *vpData;
   struct llist_t __based( vpBuffer ) *llNext;
};
```

Wskaźnik `vpBuffer` ma przypisany adres pamięci przydzielonej w pewnym momencie później w programie. Połączonej listy jest przenoszony z uwzględnieniem wartości `vpBuffer`.

> [!NOTE]
>  Utrwalanie identyfikatory zawierające wskaźniki może być również wykonywane przy użyciu [pliki mapowane w pamięci](/windows/desktop/Memory/file-mapping).

Gdy wyłuskaniem wskaźnika zależności, base musi być albo określone jawnie lub niejawnie znany za pośrednictwem deklaracji.

W celu zgodności z poprzednimi wersjami **_oparte** jest synonimem dla **__based** chyba że — opcja kompilatora [/Za \(Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md) jest określona.

## <a name="example"></a>Przykład

Poniższy przykład demonstruje zmiana wskaźnik bazowy, zmieniając jej podstawy.

```cpp
// based_pointers2.cpp
// compile with: /EHsc
#include <iostream>

int a1[] = { 1,2,3 };
int a2[] = { 10,11,12 };
int *pBased;

typedef int __based(pBased) * pBasedPtr;

using namespace std;
int main() {
   pBased = &a1[0];
   pBasedPtr pb = 0;

   cout << *pb << endl;
   cout << *(pb+1) << endl;

   pBased = &a2[0];

   cout << *pb << endl;
   cout << *(pb+1) << endl;
}
```

```Output
1
2
10
11
```

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[alloc_text](../preprocessor/alloc-text.md)