---
title: inline_depth | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inline_depth_CPP
- vc-pragma.inline_depth
dev_langs:
- C++
helpviewer_keywords:
- pragmas, inline_depth
- inline_depth pragma
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 672ea8c36b794683dca0ab50af0bda75d73f9a68
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081446"
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

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[inline_recursion](../preprocessor/inline-recursion.md)