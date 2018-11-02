---
title: Typy funkcji
ms.date: 11/04/2016
ms.assetid: 7e33d5f4-dabb-406d-afb3-13777b995028
ms.openlocfilehash: 22778f3eaefa6dbcf5f85e54c0940867ef52ab72
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526405"
---
# <a name="function-types"></a>Typy funkcji

Istnieją dwa typy funkcji. Funkcja, która wymaga ramki stosu jest wywoływana funkcja ramki. Funkcja, która nie wymaga ramki stosu jest wywoływana funkcja typu liść.

Funkcja ramki jest funkcją, która przydziela miejsce stosu, wywołuje inne funkcje, zapisuje nieulotnej rejestrów lub korzysta z obsługi wyjątków. Wymaga to również wpisu tabeli funkcji. Funkcja ramki wymaga prologu i epilogu. Funkcja ramki mogą dynamicznie przydzielać obszar stosu i mogą stosować wskaźnik ramki. Funkcja ramki ma pełnego zestawu funkcji to wywołanie standardowa swojej dyspozycji.

Jeśli funkcja ramki nie wywołuje inną funkcję, wówczas nie jest wymagane do wyrównania stosu (do których odwołuje się w sekcji [alokacji stosu](../build/stack-allocation.md)).

Funkcja liścia to taki, który nie wymaga wpisu tabeli funkcji. Go nie zmieniać nieulotnej rejestrów, w tym RSP, co oznacza, że nie wywołaniem dowolnej funkcji i przydzielenie miejsca na stosie. Może on być pozostaw niewyrównanych stosu podczas wykonywania.

## <a name="see-also"></a>Zobacz też

[Wykorzystanie stosu](../build/stack-usage.md)
