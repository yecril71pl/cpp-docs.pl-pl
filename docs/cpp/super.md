---
title: __super
ms.date: 11/04/2016
f1_keywords:
- __super_cpp
helpviewer_keywords:
- __super keyword [C++]
ms.assetid: f0957c31-9256-405b-b402-cad182404b5f
ms.openlocfilehash: b6f6a7e108224ab4c97893104c5d6c38d325fa42
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160830"
---
# <a name="__super"></a>__super

**Specyficzne dla firmy Microsoft**

Umożliwia jawne określenie, że wywoływana jest implementacja klasy bazowej dla zastępowanej funkcji.

## <a name="syntax"></a>Składnia

```
__super::member_function();
```

## <a name="remarks"></a>Uwagi

Wszystkie dostępne metody klasy podstawowej są brane pod uwagę podczas fazy rozpoznawania przeciążenia, a funkcja, która zapewnia najlepszą zgodność, jest wywoływana.

**__super** może występować tylko w treści funkcji składowej.

nie można użyć **__super** z deklaracją using. Aby uzyskać więcej informacji, zobacz [Używanie deklaracji](../cpp/using-declaration.md) .

Wprowadzając [atrybuty](../windows/attributes/attributes-alphabetical-reference.md) , które wprowadzają kod, kod może zawierać co najmniej jedną klasę bazową, której nazwy mogą nie być znane, ale zawierają metody, które chcesz wywołać.

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

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)
