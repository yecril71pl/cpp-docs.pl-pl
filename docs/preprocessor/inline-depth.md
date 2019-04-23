---
title: inline_depth
ms.date: 11/04/2016
f1_keywords:
- inline_depth_CPP
- vc-pragma.inline_depth
helpviewer_keywords:
- pragmas, inline_depth
- inline_depth pragma
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
ms.openlocfilehash: 18d772c8a9f6218ed3afaa385f214445bd0fe8e6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039023"
---
# <a name="inlinedepth"></a>inline_depth
Określa algorytm heurystyczny wbudowane wyszukiwanie głębi, taki sposób, że żadna funkcja nie będzie śródwierszowych, jeśli jest na głębokości (w wykresu wywołań) większy niż *n*.

## <a name="syntax"></a>Składnia

```
#pragma inline_depth( [n] )
```

## <a name="remarks"></a>Uwagi

Kontroluje tej pragmie ze śródwierszowaniem funkcji oznaczone [wbudowane](../cpp/inline-functions-cpp.md) i [__inline](../cpp/inline-functions-cpp.md) lub śródwierszowa automatycznie w ramach `/Ob2` opcji.

*n* może być wartością z zakresu od 0 do 255, gdzie 255 oznacza nieograniczoną głębokość w wykresu wywołań oraz zero powstrzymuje wbudowane rozwijanie.  Gdy *n* nie jest określona, używana jest domyślna (254).

**Inline_depth** pragma Określa, ile razy można rozszerzyć serii wywołań funkcji. Na przykład jeśli głębokość wbudowane to cztery i wywołania B i B, następnie wywołuje C, wszystkich trzech wywołaniach będzie wbudowany rozwinięty. Jednak najbliższego wbudowane rozwijanie jest dwa, są rozszerzane jedynie A i B i C pozostaje jako wywołania funkcji.

Aby użyć tej pragmie, należy ustawić `/Ob` — opcja kompilatora 1 lub 2. Głębi, można ustawić przy użyciu tej pragmie staje się skuteczny przy pierwszym wywołaniu funkcji po pragmy.

Głębokość wbudowanych można zmniejszyć podczas rozszerzania, ale nie zwiększa. Jeśli głębokość wbudowane sześć a podczas rozszerzania napotka preprocesora **inline_depth** pragma z wartością osiem głębokość pozostaje sześć.

**Inline_depth** pragma nie ma wpływu na funkcje oznaczone atrybutem `__forceinline`.

> [!NOTE]
> Funkcje rekursywne może być podstawione wbudowaną, aby maksymalną głębokość wywołań 16.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[inline_recursion](../preprocessor/inline-recursion.md)