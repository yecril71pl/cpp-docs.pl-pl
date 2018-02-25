---
title: "Odwołanie (C++ AMP) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
dev_langs:
- C++
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 005b25fa44f229e9d9e2b59b0a20c41a661ed6c3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="reference-c-amp"></a>Odwołanie (C++ AMP)
Ta sekcja zawiera informacje dotyczące środowiska uruchomieniowego C++ Accelerated Massive Parallelism (C++ AMP).  
  
> [!NOTE]
>  Standard języka C++ rezerwuje Użyj identyfikatorów, które zaczynają się od znaku podkreślenia (`_`) znaków dla wdrożeń, takich jak biblioteki. Nie używaj nazwy rozpoczynające się od znaku podkreślenia w kodzie. Zachowanie kodu elementów, których nazwy wykonaj tę Konwencję nie ma gwarancji i mogą ulec zmianie w przyszłych wersjach. Z tego powodu takie elementy kodu zostały pominięte w niniejszej dokumentacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)  
 Zawiera klasy i funkcje, które włączyć przyspieszenie kod w języku C++ na sprzęcie równoległych danych.  
  
 [Concurrency::direct3d, przestrzeń nazw](concurrency-direct3d-namespace.md)  
 Udostępnia funkcje, które obsługują współdziałanie D3D. Umożliwia bezproblemowe na użytek D3D zasobów obliczeniowych w kodzie AMP i korzystania z zasobów utworzone w AMP w kodzie D3D bez tworzenia nadmiarowe kopie pośrednich. C++ AMP umożliwia przyrostowo przyspieszenia sekcje obliczeniowych aplikacji DirectX i na podstawie obliczenia AMP danych za pomocą interfejsu API D3D.  
  
 [Concurrency::fast_math, przestrzeń nazw](concurrency-fast-math-namespace.md)  
 Funkcje w `fast_math` nie są zgodnych C99 przestrzeni nazw. Podano tylko pojedynczej precyzji wersje każdej funkcji. Funkcje wewnętrzne DirectX, które są szybsze niż w odpowiednie funkcje używać tych funkcji `precise_math` przestrzeni nazw i nie wymagają rozszerzoną obsługę podwójnej precyzji na akceleratora, ale są mniej dokładne. Istnieją dwie wersje każdej funkcji poziomu zgodności z kodem C99; obie wersje przyjmować i zwracać wartości o pojedynczej precyzji.  
  
 [Concurrency::graphics, przestrzeń nazw](concurrency-graphics-namespace.md)  
 Zawiera typy i funkcje, które są przeznaczone do programowania grafiki.  
  
 [Concurrency::precise_math, przestrzeń nazw](concurrency-precise-math-namespace.md)  
 Funkcje w `precise_math` zgodnych C99 są przestrzeni nazw. Zarówno pojedynczej precyzji, jak i podwójnej precyzji wersje każdej funkcji są uwzględniane. Te funkcje — dotyczy to również funkcje pojedynczej precyzji — wymagają rozszerzoną obsługę podwójnej precyzji na akceleratora.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)  
 C++ AMP przyspiesza wykonywania kodu C++, wykorzystując sprzętu równoległe danych, która najczęściej występuje jako jednostka przetwarzania graficznych (GPU) na karcie odrębne grafika.





