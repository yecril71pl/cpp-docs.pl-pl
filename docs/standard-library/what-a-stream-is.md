---
title: Czym jest strumień?
ms.date: 11/04/2016
helpviewer_keywords:
- reading data [C++], iostream programming
- data [C++], reading
- streams [C++], in iostream classes
- streams [C++]
ms.assetid: a7e661e9-6cd1-4543-a9a4-c58ee9fd32f3
ms.openlocfilehash: 80f2d17d7de2ddca1ef1501cacdb44f41c06594b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450941"
---
# <a name="what-a-stream-is"></a>Czym jest strumień?

Podobnie jak w C++ przypadku języka C, nie ma wbudowanej możliwości wejścia/wyjścia. Wszystkie C++ kompilatory są jednak powiązane z systematycznym, zorientowanym na obiektem pakietem we/wy, znanym jako klasy iostream. Strumień jest centralną koncepcją klas iostream. Obiekt strumienia można traktować jako plik inteligentny, który działa jako źródło i miejsce docelowe dla bajtów. Charakterystyki strumienia są określane przez klasę i przez niestandardowe operatory wstawiania i wyodrębniania.

W przypadku sterowników urządzeń system operacyjny dysku zajmuje się przy użyciu klawiatury, ekranu, drukarki i portów komunikacyjnych jako plików rozszerzonych. Klasy iostream współpracują z tymi rozszerzonymi plikami. Wbudowane klasy obsługują odczytywanie i zapisywanie w pamięci przy użyciu składni identycznej z tą dla operacji we/wy dysku, co ułatwia wyprowadzanie klas strumienia.

## <a name="in-this-section"></a>W tej sekcji

[Alternatywy wejścia/wyjścia](../standard-library/input-output-alternatives.md)

## <a name="see-also"></a>Zobacz także

[iostream, programowanie](../standard-library/iostream-programming.md)
