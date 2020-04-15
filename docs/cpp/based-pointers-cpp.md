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
ms.openlocfilehash: 24c3a7f85c4ea05c38f3ab1d3f637ea0ab24d4c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363746"
---
# <a name="based-pointers-c"></a>Wskaźniki bazowe (C++)

**__based** słowo kluczowe umożliwia deklarowanie wskaźników na podstawie wskaźników (wskaźników, które są odsunięcia od istniejących wskaźników). Słowo kluczowe **__based** jest specyficzne dla firmy Microsoft.

## <a name="syntax"></a>Składnia

```
type __based( base ) declarator
```

## <a name="remarks"></a>Uwagi

Wskaźniki oparte na adresach wskaźników są jedyną formą słowa kluczowego **__based** prawidłowego w kompilacjach 32-bitowych lub 64-bitowych. W przypadku 32-bitowego kompilatora C/C++ firmy Microsoft wskaźnik oparty jest 32-bitowym przesunięciem od podstawy wskaźnika 32-bitowego. Podobne ograniczenie dotyczy środowisk 64-bitowych, w których wskaźnik oparty jest przesunięciem 64-bitowym od podstawy 64-bitowej.

Jednym z zastosowań wskaźników opartych na wskaźnikach jest trwałe identyfikatory, które zawierają wskaźniki. Połączona lista, która składa się ze wskaźników opartych na wskaźniku, może zostać zapisana na dysku, a następnie ponownie załadowana do innego miejsca w pamięci, przy czym wskaźniki pozostają prawidłowe. Przykład:

```cpp
// based_pointers1.cpp
// compile with: /c
void *vpBuffer;
struct llist_t {
   void __based( vpBuffer ) *vpData;
   struct llist_t __based( vpBuffer ) *llNext;
};
```

Wskaźnikowi `vpBuffer` jest przypisywany adres pamięci przydzielonej w późniejszym punkcie programu. Połączona lista zostanie przeniesiona względem `vpBuffer`wartości .

> [!NOTE]
> Utrwalanie identyfikatorów zawierających wskaźniki można również wykonać za pomocą [plików mapowanych w pamięci.](/windows/win32/Memory/file-mapping)

Podczas dereferencing wskaźnik oparty, podstawa musi być jawnie określony lub niejawnie znany za pośrednictwem deklaracji.

W przypadku zgodności z poprzednimi wersjami **_based** jest synonimem **__based** chyba że określono opcję kompilatora [/Za \(Wyłącz rozszerzenia języka).](../build/reference/za-ze-disable-language-extensions.md)

## <a name="example"></a>Przykład

Poniższy kod demonstruje zmianę wskaźnika opartego przez zmianę jego podstawy.

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

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[alloc_text](../preprocessor/alloc-text.md)
