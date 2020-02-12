---
title: Odwołanie (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
ms.openlocfilehash: ff7c2b0894a2fa3de7674a72bc93dd3f781398b9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126412"
---
# <a name="reference-c-amp"></a>Odwołanie (C++ AMP)

Ta sekcja zawiera informacje dotyczące C++ przyspieszonego środowiska uruchomieniowego o szybszymC++ obniesieniu (amp).

> [!NOTE]
> Standard C++ języka rezerwuje użycie identyfikatorów, które zaczynają się od znaku podkreślenia (`_`) dla implementacji takich jak biblioteki. Nie należy używać nazw zaczynających się od znaku podkreślenia w kodzie. Zachowanie elementów kodu, których nazwy są zgodne z tą konwencją, nie jest gwarantowane i może ulec zmianie w przyszłych wydaniach. Z tego powodu takie elementy kodu zostały pominięte w tej dokumentacji.

## <a name="in-this-section"></a>W tej sekcji

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)<br/>
Dostarcza klasy i funkcje, które umożliwiają przyspieszenie C++ kodu na urządzeniach równoległych danych.

[Concurrency::direct3d, przestrzeń nazw](concurrency-direct3d-namespace.md)<br/>
Udostępnia funkcje, które obsługują współdziałanie D3D. Pozwala bezproblemowo korzystać z zasobów D3D do obliczeń w kodzie AMP i używania zasobów utworzonych w AMP w kodzie D3D, bez tworzenia nadmiarowych kopii pośrednich. Możesz użyć C++ amp, aby stopniowo przyspieszyć sekcje aplikacji DirectX intensywnie korzystających z mocy obliczeniowej i użyć interfejsu API D3D na danych wyprodukowanych z obliczeń amp.

[Concurrency::fast_math, przestrzeń nazw](concurrency-fast-math-namespace.md)<br/>
Funkcje w przestrzeni nazw `fast_math` nie są zgodne z C99. Udostępniane są tylko wersje o pojedynczej precyzji każdej funkcji. Te funkcje używają funkcji wewnętrznych DirectX, które są szybsze niż odpowiednie funkcje w przestrzeni nazw `precise_math` i nie wymagają rozszerzonej obsługi podwójnej precyzji dla akceleratora, ale są mniej dokładne. Istnieją dwie wersje każdej funkcji dla zgodności na poziomie źródła z kodem C99; Obie wersje pobierają i zwracają wartości pojedynczej precyzji.

[Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)<br/>
Zawiera typy i funkcje, które są przeznaczone do programowania grafiki.

[Concurrency::precise_math, przestrzeń nazw](concurrency-precise-math-namespace.md)<br/>
Funkcje w przestrzeni nazw `precise_math` są zgodne z C99. Dostępne są zarówno wersje o pojedynczej precyzji, jak i podwójnej precyzji każdej funkcji. Te funkcje — obejmuje funkcje o pojedynczej precyzji — wymagają rozszerzonej obsługi podwójnej precyzji dla akceleratora.

## <a name="related-sections"></a>Sekcje pokrewne

[C++ AMP (C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
C++AMP przyspiesza wykonywanie C++ kodu przez skorzystanie z zalet sprzętu równoległego danych, który jest powszechnie obecny jako procesor graficzny (GPU) na dyskretnej karcie graficznej.
