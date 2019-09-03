---
title: conform, pragma
ms.date: 08/29/2019
f1_keywords:
- conform_CPP
- vc-pragma.conform
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
ms.openlocfilehash: 816ff85bb19f549c6ea072073bd89fcd503545f2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220500"
---
# <a name="conform-pragma"></a>conform, pragma

**C++Specjalne**

Określa zachowanie w czasie wykonywania dla opcji kompilatora [/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) .

## <a name="syntax"></a>Składnia

> **#pragma zgodności (** *Nazwa* [ **, show** ] [ **,** { **on** | **off** }] [[ **,** { **push** | **pop** }] [ **,** *Identyfikator* [ **,** { **on** **wyłączone}** ]  |  ] ] **)**

### <a name="parameters"></a>Parametry

*Nazwij*\
Określa nazwę opcji kompilatora, która ma zostać zmodyfikowana. Jedyną prawidłową *nazwą* jest `forScope`.

**wskazują**\
Obowiązkowe Powoduje, że bieżące ustawienie *nazwy* (true lub false) będzie wyświetlane przy użyciu komunikatu ostrzegawczego podczas kompilacji. Na przykład `#pragma conform(forScope, show)`.

**włączone**, **wyłączone**\
Obowiązkowe Ustawienie *Nazwa* na **włączone** włącza opcję kompilatora [/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) . Wartość domyślna to **off**.

**wydajności**\
Obowiązkowe Wypchnij bieżącą wartość *nazwy* do wewnętrznego stosu kompilatora. **W** przypadku określenia *identyfikatora*można określić wartość Włącz lub **Wyłącz** dla *nazwy* do wypchnięcia na stosie. Na przykład `#pragma conform(forScope, push, myname, on)`.

**skakując**\
Obowiązkowe Ustawia wartość *Nazwa* na wartość w górnej części wewnętrznego stosu kompilatora, a następnie umieszcza stos. Jeśli identyfikator jest określony za pomocą **pop**, stos zostanie zdjęte z powrotem do momentu znalezienia rekordu z *identyfikatorem*, który również będzie zdjęte; Bieżąca wartość *nazwy* w następnym rekordzie na stosie zmieni się na nową wartość dla *nazwy*. Jeśli określisz **pop** z *identyfikatorem* , który nie znajduje się w rekordzie na stosie, **pop** zostanie zignorowany.

*identyfikatora*\
Obowiązkowe Mogą być dołączone do polecenia **push** lub **pop** . Jeśli jest używany *Identyfikator* , można również użyć specyfikatora **on** lub **off** .

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

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
