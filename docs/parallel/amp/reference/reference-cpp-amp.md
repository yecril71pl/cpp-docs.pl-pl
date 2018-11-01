---
title: Odwołanie (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
ms.openlocfilehash: 5e6905adee6e6cad0c0c49488352f4a039aa27eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630072"
---
# <a name="reference-c-amp"></a>Odwołanie (C++ AMP)

Ta sekcja zawiera informacje dotyczące środowiska uruchomieniowego C++ Accelerated Massive Parallelism (C++ AMP).

> [!NOTE]
>  Standard języka C++ zastrzega stosowanie identyfikatorów, które zaczynają się od znaku podkreślenia (`_`) znak do implementacji takich jak biblioteki. Nie należy używać nazwy rozpoczynające się od znaku podkreślenia w kodzie. Zachowanie kodu, elementy, które stosują taką konwencję nazw, których nie jest gwarantowane i mogą ulec zmianie w przyszłych wersjach. Z tego względu takie elementy kodu zostały pominięte w tej dokumentacji.

## <a name="in-this-section"></a>W tej sekcji

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)<br/>
Zawiera klasy i funkcje, które umożliwiają przyspieszenie kodu C++ na urządzeniach równoległych danych.

[Concurrency::direct3d, przestrzeń nazw](concurrency-direct3d-namespace.md)<br/>
Oferuje funkcje, które obsługują współdziałanie D3D. Umożliwia bezproblemowe korzystanie z zasobów D3D dla obliczeń w kodzie AMP i wykorzystanie zasobów utworzonych w AMP, w kodzie D3D, bez tworzenia nadmiarowych kopii pośrednich. Można użyć C++ AMP, aby stopniowo przyspieszyć sekcje intensywnych obliczeń aplikacji DirectX i użyć interfejsu API D3D na danych wyprodukowanych z obliczeń AMP.

[Concurrency::fast_math, przestrzeń nazw](concurrency-fast-math-namespace.md)<br/>
Funkcje w `fast_math` przestrzeni nazw nie są zgodne z C99. Podano tylko pojedynczej precyzji wersje każdej funkcji. Te funkcje używają wewnętrznych funkcji DirectX, które są szybsze od odpowiednich funkcji w `precise_math` przestrzeni nazw i nie wymagają rozszerzonego wsparcia podwójnej precyzji na akceleratorze, ale są mniej dokładne. Istnieją dwie wersje każdej funkcji dla zgodności poziomu źródła z kodem C99; obie wersje przyjmują i zwracają wartości pojedynczej precyzji.

[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)<br/>
Zawiera typy i funkcje, które są przeznaczone do programowania grafiki.

[Concurrency::precise_math, przestrzeń nazw](concurrency-precise-math-namespace.md)<br/>
Funkcje w `precise_math` przestrzeni nazw są zgodne z C99. Uwzględniono pojedynczej precyzji, jak i podwójną precyzją wersje każdej funkcji. Te funkcje — w tym funkcje pojedynczej precyzji — wymagają rozszerzonej obsługi podwójnej precyzji na akceleratorze.

## <a name="related-sections"></a>Sekcje pokrewne

[C++ AMP (C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
C++ AMP przyspiesza wykonywanie kodu C++ wykorzystując sprzęt danych równoległych powszechnie występujący jako jednostka przetwarzania grafiki (GPU) na dyskretną kartę graficzną.

