---
title: jest zgodna z | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- conform_CPP
- vc-pragma.conform
dev_langs:
- C++
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 05b1f9fef458b8c21de9eb3942730ff901d3922e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071235"
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

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)