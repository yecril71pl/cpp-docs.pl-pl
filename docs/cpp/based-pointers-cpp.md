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
ms.openlocfilehash: 0a0435aa89e4cf744a5bc3c6dc72a715ed55f954
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498787"
---
# <a name="based-pointers-c"></a>Wskaźniki bazowe (C++)

**Microsoft Specific**

Słowo kluczowe **__based** umożliwia deklarowanie wskaźników na podstawie wskaźników (wskaźników, które są przesunięciami z istniejących wskaźników).

## <a name="syntax"></a>Składnia

```

type __based( base ) declarator
```

## <a name="remarks"></a>Uwagi

Wskaźniki oparte na adresach wskaźnika są jedyną formą słowa kluczowego **__based** , które są prawidłowe w kompilacjach 32-bitowych lub 64-bitowych. Dla Microsoft 32-bitowego języka C/C++ kompilator wskaźnik oparty jest 32-bitowym przesunięciem w bazie wskaźnika 32-bitowego. Podobne ograniczenie jest przechowywane w środowiskach 64-bitowych, gdzie wskaźnik oparty jest 64-bitowym przesunięciem od 64-bitowego bazy.

Jednym z nich użycia dla wskaźników opartych na wskaźnikach jest dla trwałych identyfikatorów, które zawierają wskaźniki. Lista połączona, która składa się ze wskaźników opartych na wskaźniku, może zostać zapisana na dysku, a następnie ponownie załadowana do innego miejsca w pamięci, przy czym pozostałe wskaźniki są prawidłowe. Przykład:

```cpp
// based_pointers1.cpp
// compile with: /c
void *vpBuffer;
struct llist_t {
   void __based( vpBuffer ) *vpData;
   struct llist_t __based( vpBuffer ) *llNext;
};
```

Do wskaźnika `vpBuffer` przypisano adres pamięci przydzielonej w późniejszym czasie w programie. Połączona lista zostanie przeniesiona względem wartości `vpBuffer`.

> [!NOTE]
>  Identyfikatory utrwalane zawierające wskaźniki można także wykonać przy użyciu [plików mapowanych na pamięć](/windows/win32/Memory/file-mapping).

W przypadku wyłuskania wskaźnika bazowego należy jawnie określić lub niejawnie znany przez deklarację.

Aby zapewnić zgodność z poprzednimi wersjami, **_based** jest synonimem dla **__based** , chyba że jest określona opcja kompilatora [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

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