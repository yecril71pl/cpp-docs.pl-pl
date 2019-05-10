---
title: auto — słowo kluczowe
ms.date: 05/07/2019
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
ms.openlocfilehash: a695c33ab55601bb8d81b00f963646f6a48f09d5
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222246"
---
# <a name="auto-keyword"></a>auto — słowo kluczowe

**Automatycznie** — słowo kluczowe jest Specyfikator deklaracji. Jednak C++ standard definiuje oryginału i poprawione znaczenie słowa kluczowego. Przed Visual Studio 2010 **automatycznie** — słowo kluczowe deklaruje zmienną w *automatyczne* klasę magazynu, czyli zmiennej, która ma lokalne okresy istnienia. Począwszy od programu Visual Studio 2010, **automatycznie** — słowo kluczowe deklaruje zmienną, którego typ jest ustalić na podstawie wyrażenia inicjowania w jego deklaracji. [/Zc: Auto&#91;-&#93; ](../build/reference/zc-auto-deduce-variable-type.md) — opcja kompilatora kontroluje znaczenie **automatycznie** — słowo kluczowe.

## <a name="syntax"></a>Składnia

```cpp
auto declarator ;
auto declarator initializer;
```

## <a name="remarks"></a>Uwagi

Definicja **automatycznie** zmiany słów kluczowych w języku programowania C++, ale nie w języku programowania C.

W poniższych tematach opisano **automatycznie** — słowo kluczowe i odpowiadające opcje kompilatora:

- [automatyczne](../cpp/auto-cpp.md) opisuje nową definicję **automatycznie** — słowo kluczowe.

- [/ Zc: Auto (dedukuj typ zmiennej)](../build/reference/zc-auto-deduce-variable-type.md) opisuje opcję kompilatora, która informuje kompilator, która definicja **automatycznie** — słowo kluczowe do użycia.

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)