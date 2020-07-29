---
title: Wskaźniki bazowe (C++)
ms.date: 10/09/2018
f1_keywords:
- __based
- _based
- __based_cpp
helpviewer_keywords:
- __based keyword [C++]
- based pointers
- pointers, based
ms.assetid: 1e5f2e96-c52e-4738-8e14-87278681205e
ms.openlocfilehash: a76fe56e0e6bd0501bbc3e23e138cb2e75055c73
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229145"
---
# <a name="based-pointers-c"></a>Wskaźniki bazowe (C++)

**`__based`** Słowo kluczowe umożliwia deklarowanie wskaźników na podstawie wskaźników (wskaźników, które są przesunięte z istniejących wskaźników). **`__based`** Słowo kluczowe jest specyficzne dla firmy Microsoft.

## <a name="syntax"></a>Składnia

```
type __based( base ) declarator
```

## <a name="remarks"></a>Uwagi

Wskaźniki oparte na adresach wskaźnika są jedyną formą **`__based`** słowa kluczowego, które są prawidłowe w kompilacjach 32-bitowych lub 64-bitowych. W przypadku kompilatora Microsoft 32-bitowego C/C++ wskaźnik oparty jest 32-bitowym przesunięciem z bazy wskaźnika 32-bitowego. Podobne ograniczenie jest przechowywane w środowiskach 64-bitowych, gdzie wskaźnik oparty jest 64-bitowym przesunięciem od 64-bitowego bazy.

Jednym z nich użycia dla wskaźników opartych na wskaźnikach jest dla trwałych identyfikatorów, które zawierają wskaźniki. Lista połączona, która składa się ze wskaźników opartych na wskaźniku, może zostać zapisana na dysku, a następnie ponownie załadowana do innego miejsca w pamięci, przy czym pozostałe wskaźniki są prawidłowe. Na przykład:

```cpp
// based_pointers1.cpp
// compile with: /c
void *vpBuffer;
struct llist_t {
   void __based( vpBuffer ) *vpData;
   struct llist_t __based( vpBuffer ) *llNext;
};
```

Do wskaźnika `vpBuffer` przypisano adres pamięci przydzielonej w późniejszym czasie w programie. Połączona lista zostanie przeniesiona względem wartości `vpBuffer` .

> [!NOTE]
> Identyfikatory utrwalane zawierające wskaźniki można także wykonać przy użyciu [plików mapowanych na pamięć](/windows/win32/Memory/file-mapping).

W przypadku wyłuskania wskaźnika bazowego należy jawnie określić lub niejawnie znany przez deklarację.

W celu zapewnienia zgodności z poprzednimi wersjami **_based** jest synonimem, **`__based`** Jeśli nie określono opcji kompilatora [/za \( disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="example"></a>Przykład

Poniższy kod demonstruje zmianę wskaźnika bazowego, zmieniając jego podstawę.

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
