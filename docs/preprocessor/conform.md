---
title: conform
ms.date: 11/04/2016
f1_keywords:
- conform_CPP
- vc-pragma.conform
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
ms.openlocfilehash: 35c3b06106779a9056f682ff76c6ed4b4ab1ab41
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59026581"
---
# <a name="conform"></a>conform
**Określonego język C++**

Określa zachowanie środowiska wykonawczego [/Zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) — opcja kompilatora.

## <a name="syntax"></a>Składnia

> **#pragma są zgodne (** *nazwa* [**, Pokaż** ] [**,** { **na** | **poza** }] [[**,** { **wypychania** | **pop** }] [**,** *identyfikator* ]] **)**

### <a name="parameters"></a>Parametry

*Nazwa*<br/>
Określa nazwę opcję kompilatora, który ma zostać zmodyfikowana. Jedyne prawidłowe *nazwa* jest `forScope`.

**Pokaż**<br/>
(Opcjonalnie) Powoduje, że bieżące ustawienie *nazwa* (true lub false), który ma być wyświetlany za pomocą komunikatu ostrzegawczego podczas kompilacji. Na przykład `#pragma conform(forScope, show)`.

**na**, **wyłączone**<br/>
(Opcjonalnie) Ustawienie *nazwa* do **na** umożliwia [/Zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) — opcja kompilatora. Wartość domyślna to **poza**.

**push**<br/>
(Opcjonalnie) Wypychanie bieżącej wartości *nazwa* na wewnętrznym stosie kompilatora. Jeśli określisz *identyfikator*, można określić **na** lub **poza** wartość *nazwa* ma zostać wypchnięty na stos. Na przykład `#pragma conform(forScope, push, myname, on)`.

**POP**<br/>
(Opcjonalnie) Ustawia wartość *nazwa* wartość u góry wewnętrznego stosu kompilatora, a następnie POP stosu. Jeśli identyfikator jest określany za pomocą **pop**, stos będzie zostać zdjęte ze stosu wstecz, aż znajdzie rekord z *identyfikator*, który będzie również zostać zdjęte ze stosu; bieżąca wartość dla *nazwa* w Następny rekord na stosie staje się nową wartość dla *nazwa*. Jeśli określisz **pop** z *identyfikator* nie jest w rekordzie na stosie, **pop** jest ignorowana.

*Identyfikator*<br/>
(Opcjonalnie) Można włączyć **wypychania** lub **pop** polecenia. Jeśli *identyfikator* jest używany, a następnie **na** lub **poza** specyfikator może również służyć.

## <a name="example"></a>Przykład

```cpp
// pragma_directive_conform.cpp
// compile with: /W1
// C4811 expected
#pragma conform(forScope, show)
#pragma conform(forScope, push, x, on)
#pragma conform(forScope, push, x1, off)
#pragma conform(forScope, push, x2, off)
#pragma conform(forScope, push, x3, off)
#pragma conform(forScope, show)
#pragma conform(forScope, pop, x1)
#pragma conform(forScope, show)

int main() {}
```

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)