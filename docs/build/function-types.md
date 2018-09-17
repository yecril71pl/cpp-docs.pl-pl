---
title: Funkcja typy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7e33d5f4-dabb-406d-afb3-13777b995028
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6dfb36dc9e177fdb9ad196c0e2a8ad0f352d5f2d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709569"
---
# <a name="function-types"></a>Typy funkcji

Istnieją dwa typy funkcji. Funkcja, która wymaga ramki stosu jest wywoływana funkcja ramki. Funkcja, która nie wymaga ramki stosu jest wywoływana funkcja typu liść.

Funkcja ramki jest funkcją, która przydziela miejsce stosu, wywołuje inne funkcje, zapisuje nieulotnej rejestrów lub korzysta z obsługi wyjątków. Wymaga to również wpisu tabeli funkcji. Funkcja ramki wymaga prologu i epilogu. Funkcja ramki mogą dynamicznie przydzielać obszar stosu i mogą stosować wskaźnik ramki. Funkcja ramki ma pełnego zestawu funkcji to wywołanie standardowa swojej dyspozycji.

Jeśli funkcja ramki nie wywołuje inną funkcję, wówczas nie jest wymagane do wyrównania stosu (do których odwołuje się w sekcji [alokacji stosu](../build/stack-allocation.md)).

Funkcja liścia to taki, który nie wymaga wpisu tabeli funkcji. Go nie zmieniać nieulotnej rejestrów, w tym RSP, co oznacza, że nie wywołaniem dowolnej funkcji i przydzielenie miejsca na stosie. Może on być pozostaw niewyrównanych stosu podczas wykonywania.

## <a name="see-also"></a>Zobacz też

[Wykorzystanie stosu](../build/stack-usage.md)
