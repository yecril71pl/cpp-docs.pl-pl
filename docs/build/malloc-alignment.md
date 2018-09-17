---
title: malloc, wyrównanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a8d1d1b4-5122-456f-9a64-a50e105e55a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa6e2748691eeb8a11834bcf8e6962252be7ab3f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712065"
---
# <a name="malloc-alignment"></a>Wyrównanie — funkcja malloc

[malloc](../c-runtime-library/reference/malloc.md) gwarancję zwracania pamięci, który jest odpowiednio wyrównana do przechowywania dowolnego obiektu, który ma podstawowe wyrównanie i który może zmieścić ilość przydzielonej pamięci. A *podstawowe wyrównanie* jest wyrównanie, które jest mniejsze niż lub równe największemu wyrównaniu, która jest obsługiwana przez implementację bez specyfikacji wyrównania. (W programie Visual C++ to wyrównania, która jest wymagana dla `double`, lub 8 bajtów. W kodzie, który jest przeznaczony dla platform 64-bitowy to 16 bajtów.) Na przykład alokacja Czterobajtowa byłaby wyrównana do granicy, który obsługuje dowolny obiekt obiekty czterobajtowe lub mniejsze.

Visual C++ pozwala na typy, które mają *rozszerzone wyrównanie*, które są również nazywane *nadmiernie wyrównanych* typów. Na przykład typy SSE [__m128](../cpp/m128.md) i `__m256`oraz typy, które są zadeklarowane za pomocą `__declspec(align( n ))` gdzie `n` jest większa niż 8, mają rozszerzone wyrównanie. Wyrównanie pamięci na granicy, która jest odpowiednia dla obiektu, który wymaga rozszerzonego wyrównania, nie jest zagwarantowana przez `malloc`. Aby przydzielić pamięć dla typów nadmiernie wyrównanych, użyj [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md) i pokrewnych funkcji.

## <a name="see-also"></a>Zobacz też

[Wykorzystanie stosu](../build/stack-usage.md)<br/>
[align](../cpp/align-cpp.md)<br/>
[__declspec](../cpp/declspec.md)