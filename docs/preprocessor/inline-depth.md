---
title: inline_depth, pragma
ms.date: 08/29/2019
f1_keywords:
- inline_depth_CPP
- vc-pragma.inline_depth
helpviewer_keywords:
- pragmas, inline_depth
- inline_depth pragma
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
ms.openlocfilehash: be57178280e278683b85db1413ff5724b5260aef
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220986"
---
# <a name="inline_depth-pragma"></a>inline_depth, pragma

Określa głębokość wyszukiwania wbudowanej heurystycznej. Funkcja na głębokości wykresu wywołań większa niż określona wartość nie jest wbudowana.

## <a name="syntax"></a>Składnia

> **#pragma inline_depth (** [ *n* ] **)**

## <a name="remarks"></a>Uwagi

Ta pragma kontroluje sposób wykreślania funkcji [](../cpp/inline-functions-cpp.md) oznaczonych jako inline i [__inline](../cpp/inline-functions-cpp.md)albo w sposób `/Ob` automatyczny w obszarze opcji.

*n* może być wartością z przedziału od 0 do 255, gdzie 255 oznacza nieograniczoną głębokość w grafie wywołań. Wartość 0 wstrzymuje rozwijanie wbudowane. Gdy *n* nie jest określony, zostanie użyta wartość domyślna 254.

**Inline_depth** pragma kontroluje liczbę wywołań funkcji, które mogą być rozwinięte. Załóżmy na przykład, że głębokość wbudowana to 4. Jeśli wywołania B i B następnie wywoła C, wszystkie trzy wywołania są rozwinięte wbudowane. Jeśli jednak najbliższe rozwinięcie głębokości jest 2, tylko a i B są rozwinięte, a C pozostanie jako wywołanie funkcji.

Aby użyć tej dyrektywy pragma, należy ustawić `/Ob` opcję kompilatora na 1 lub wyższą. Zestaw głębokości korzystający z tej dyrektywy pragma obowiązuje przy pierwszym wywołaniu funkcji po pragmie.

Głębokość wbudowana może zostać zmniejszona podczas rozszerzania, ale nie jest zwiększana. Jeśli głębokość wbudowana to 6, a podczas rozszerzania preprocesor napotka **inline_depth** pragma o wartości 8, Głębokość pozostanie 6.

Dyrektywa pragma **inline_depth** nie ma wpływu na funkcje oznaczone `__forceinline`atrybutem.

> [!NOTE]
> Funkcje cykliczne mogą zostać zastąpione w wierszu do maksymalnej głębokości 16 wywołań.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[inline_recursion](../preprocessor/inline-recursion.md)
