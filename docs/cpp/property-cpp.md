---
title: właściwość (C++)
ms.date: 11/04/2016
f1_keywords:
- property_cpp
helpviewer_keywords:
- property __declspec keyword
- __declspec keyword [C++], property
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
ms.openlocfilehash: 03f71739698fd20a01fd72567ce5b9babc176327
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179305"
---
# <a name="property-c"></a>właściwość (C++)

**Specyficzne dla firmy Microsoft**

Ten atrybut może być stosowany do niestatycznych "wirtualnych elementów członkowskich danych" w definicji klasy lub struktury. Kompilator traktuje te "wirtualne elementy członkowskie danych" jako składowe danych, zmieniając ich odwołania na wywołania funkcji.

## <a name="syntax"></a>Składnia

```
   __declspec( property( get=get_func_name ) ) declarator
   __declspec( property( put=put_func_name ) ) declarator
   __declspec( property( get=get_func_name, put=put_func_name ) ) declarator
```

## <a name="remarks"></a>Uwagi

Gdy kompilator widzi składową danych zadeklarowaną z tym atrybutem po prawej stronie operatora wyboru elementu członkowskiego (" **.** " lub " **->** "), konwertuje operację na funkcję `get` lub `put`, w zależności od tego, czy takie wyrażenie jest wartością l lub r-Value. W bardziej skomplikowanych kontekstach, takich jak "`+=`", wielokrotne pisanie odbywa się przez wykonanie obu `get` i `put`.

Ten atrybut może być również używany w deklaracji pustej tablicy w definicji klasy lub struktury. Na przykład:

```cpp
__declspec(property(get=GetX, put=PutX)) int x[];
```

Powyższa instrukcja wskazuje, że `x[]` mogą być używane z co najmniej jednym indeksem tablicy. W takim przypadku `i=p->x[a][b]` zostanie włączona do `i=p->GetX(a, b)`, a `p->x[a][b] = i` zostanie włączona `p->PutX(a, b, i);`

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="example"></a>Przykład

```cpp
// declspec_property.cpp
struct S {
   int i;
   void putprop(int j) {
      i = j;
   }

   int getprop() {
      return i;
   }

   __declspec(property(get = getprop, put = putprop)) int the_prop;
};

int main() {
   S s;
   s.the_prop = 5;
   return s.the_prop;
}
```

## <a name="see-also"></a>Zobacz też

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
