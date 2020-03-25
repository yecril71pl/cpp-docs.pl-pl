---
title: Ostrzeżenie kompilatora (poziomy 2 i 4) — od C4200
ms.date: 11/04/2016
f1_keywords:
- C4200
helpviewer_keywords:
- C4200
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
ms.openlocfilehash: 4b0750fe50e18214e0841eff6b3459438e9a6aec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197954"
---
# <a name="compiler-warning-levels-2-and-4-c4200"></a>Ostrzeżenie kompilatora (poziomy 2 i 4) — od C4200

użyto niestandardowego rozszerzenia: tablica o rozmiarze zerowym w strukturze/Unii

Wskazuje, że struktura lub Unia zawiera tablicę o rozmiarze zerowym.

Deklaracja tablicy o rozmiarze zerowym jest rozszerzeniem firmy Microsoft. Powoduje to wyświetlenie ostrzeżenia poziomu 2 podczas kompilowania C++ pliku oraz ostrzeżenia poziomu 4 podczas kompilowania pliku języka C. C++Kompilacja daje również następujące ostrzeżenie: "nie można wygenerować operatora Copy-ctor lub Copy-przypisania, gdy UDT zawiera tablicę o rozmiarze zerowym". Ten przykład generuje ostrzeżenie — od C4200:

```cpp
// C4200.cpp
// compile by using: cl /W4 c4200.cpp
struct A {
    int a[0];  // C4200
};
int main() {
}
```

To niestandardowe rozszerzenie jest często używane do interfejsu kodu z zewnętrznymi strukturami danych o zmiennej długości. Jeśli ten scenariusz ma zastosowanie do kodu, można wyłączyć Ostrzeżenie:

## <a name="example"></a>Przykład

```cpp
// C4200b.cpp
// compile by using: cl /W4 c4200a.cpp
#pragma warning(disable : 4200)
struct A {
    int a[0];
};
int main() {
}
```
