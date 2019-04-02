---
title: __super
ms.date: 11/04/2016
f1_keywords:
- __super_cpp
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
ms.openlocfilehash: a69d177bb83ce404a18d50c8f966be5d81f5fa72
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58779654"
---
# <a name="super"></a>__super

**Microsoft Specific**

Można jawnie określać dla funkcji, które są zastępowanie wywołujesz implementacji klasy podstawowej.

## <a name="syntax"></a>Składnia

```
__super::member_function();
```

## <a name="remarks"></a>Uwagi

Wszystkie dostępne metody klasy podstawowej są traktowane jako fazie rozdzielczość przeciążenia, a funkcja, która udostępnia najlepsze dopasowanie jest tą, która jest wywoływana.

**__super** może wystąpić tylko wewnątrz treści funkcji składowej.

**__super** nie można używać z za pomocą deklaracji. Zobacz [użycie — deklaracja](../cpp/using-declaration.md) Aby uzyskać więcej informacji.

Wraz z wprowadzeniem [atrybuty](../windows/attributes/attributes-alphabetical-reference.md) , wstrzyknięcie kodu, Twój kod może zawierać jeden lub więcej klas bazowych, których nazwy, może nie wiesz, ale które zawierają metody, które chcesz wywołać.

## <a name="example"></a>Przykład

```cpp
// deriv_super.cpp
// compile with: /c
struct B1 {
   void mf(int) {}
};

struct B2 {
   void mf(short) {}

   void mf(char) {}
};

struct D : B1, B2 {
   void mf(short) {
      __super::mf(1);   // Calls B1::mf(int)
      __super::mf('s');   // Calls B2::mf(char)
   }
};
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[słowa kluczowe](../cpp/keywords-cpp.md)