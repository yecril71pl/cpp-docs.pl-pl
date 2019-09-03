---
title: inline_recursion, pragma
ms.date: 08/29/2019
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
ms.openlocfilehash: 0169e06e8e47f7b0a7b3f73e809ddc988bcf1e95
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220951"
---
# <a name="inline_recursion-pragma"></a>inline_recursion, pragma

Kontroluje wbudowane rozwijanie bezpośrednich lub wzajemnie cyklicznych wywołań funkcji.

## <a name="syntax"></a>Składnia

> **#pragma inline_recursion (** [{ **on** | **off** }] **)**

## <a name="remarks"></a>Uwagi

Użyj tej dyrektywy pragma, aby kontrolować [](../cpp/inline-functions-cpp.md) funkcje oznaczone jako inline i [__inline](../cpp/inline-functions-cpp.md) lub funkcje, które kompilator automatycznie `/Ob2` rozszerza w obszarze opcji. Użycie tej dyrektywy pragma wymaga ustawienia opcji kompilatora [/ob](../build/reference/ob-inline-function-expansion.md) o wartości 1 lub 2. Domyślny stan dla **inline_recursion** jest wyłączony. Ta pragma jest skuteczna przy pierwszym wywołaniu funkcji po pojawieniu się dyrektywy pragma i nie ma wpływu na definicję funkcji.

**Inline_recursion** pragma kontroluje sposób rozszerzania funkcji cyklicznych. Jeśli **inline_recursion** jest wyłączona, a jeśli Wbudowana funkcja wywołuje siebie bezpośrednio lub pośrednio, funkcja zostanie rozwinięta tylko jeden raz. Jeśli **inline_recursion** jest włączona, funkcja jest rozszerzana wiele razy, dopóki nie osiągnie wartości ustawionej za pomocą [inline_depth](../preprocessor/inline-depth.md) pragma, wartość domyślna funkcji cyklicznych, która jest `inline_depth` definiowana przez pragma lub limit pojemności.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[inline_depth](../preprocessor/inline-depth.md)\
[/Ob (Rozszerzenie funkcji wbudowanej)](../build/reference/ob-inline-function-expansion.md)
