---
title: "Wyrównanie — funkcja malloc | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: a8d1d1b4-5122-456f-9a64-a50e105e55a5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d9acaf1c8912e1b563bb5d05ae600d1430049e6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="malloc-alignment"></a>Wyrównanie — funkcja malloc
[malloc](../c-runtime-library/reference/malloc.md) może zwracać odpowiednio wyrównania przechowywania dowolny obiekt wyrównanie podstawowych i który może pasować ilości pamięci przydzielonej pamięci. A *podstawowych wyrównanie* jest wyrównania, która jest mniejsza niż największa wyrównania, która jest obsługiwana przez implementację bez wyrównania. (W programie Visual C++, to wyrównania, która jest wymagana dla `double`, lub 8 bajtów. W kodzie, przeznaczonego dla platformy 64-bitowych jest 16 bajtów). Na przykład alokacji 4 bajtowych może być wyrównany na granicy obsługuje dowolny obiekt 4 bajtowych lub mniejszy.  
  
 Visual C++ pozwala na typy, które mają *rozszerzony wyrównanie*, które są nazywane również *nadmiernie wyrównane* typów. Na przykład typy SSE [__m128](../cpp/m128.md) i `__m256`oraz typy, które są zadeklarowane za pomocą `__declspec(align( n ))` gdzie `n` jest większa niż 8, rozszerzony wyrównania. Wyrównanie pamięci na granicy, które jest odpowiednie dla obiekt, który wymaga rozszerzonej wyrównanie nie jest gwarantowana przez `malloc`. Aby przydzielić pamięci dla typów nadmiernie wyrównane, użyj [_aligned_malloc —](../c-runtime-library/reference/aligned-malloc.md) i powiązane funkcje.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykorzystanie stosu](../build/stack-usage.md)   
 [Dopasuj](../cpp/align-cpp.md)   
 [__declspec](../cpp/declspec.md)