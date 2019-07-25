---
title: Uruchamianie i kończenie działania programu C++
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, program startup and termination
- terminating execution
- Function Main procedures
- control text streams
- startup code, and C++ program termination
- main function, program startup
ms.assetid: f72c8f76-f507-4ddd-a270-7b60f4fed625
ms.openlocfilehash: e59e8852172a998e4bf4f42f9f919dc29c2ded85
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450651"
---
# <a name="c-program-startup-and-termination"></a>Uruchamianie i kończenie działania programu C++

C++ Program wykonuje te same operacje co program w języku C podczas uruchamiania programu i kończenia działania programu oraz kilka bardziej opisanych tutaj.

Przed wywołaniem funkcji `main`przez środowisko docelowe i po przechowywaniu wszystkich stałych wartości początkowych określonych we wszystkich obiektach, które mają statyczny czas trwania, program wykonuje wszystkie pozostałe konstruktory dla takich obiektów statycznych. Kolejność wykonywania nie jest określona między jednostkami tłumaczenia, ale można jednak założyć, że niektóre obiekty [iostreams](../standard-library/iostreams-conventions.md) są prawidłowo zainicjowane do użytku przez te konstruktory statyczne. Te strumienie tekstu kontrolki są następujące:

- [CIN](../standard-library/iostream.md#cin) — dla standardowych danych wejściowych.

- [cout](../standard-library/iostream.md#cout) — dla wyjścia standardowego.

- [cerr](../standard-library/iostream.md#cerr) — w przypadku niebuforowanego wyjścia błędu standardowego.

- [CLOG](../standard-library/iostream.md#clog) — dla buforowanych standardowych danych wyjściowych błędu.

Można również użyć tych obiektów w destruktorach wywoływanych dla obiektów statycznych podczas kończenia działania programu.

Podobnie jak w przypadku języka C `main` , zwracanie `exit` z lub wywołania `atexit` wywołań wszystkie funkcje zarejestrowane w odwrotnej kolejności rejestru. Zgłoszono wyjątek z takich zarejestrowanych wywołań `terminate`funkcji.

## <a name="see-also"></a>Zobacz także

[C++Omówienie biblioteki standardowej](../standard-library/cpp-standard-library-overview.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
