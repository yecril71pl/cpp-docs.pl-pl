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
ms.openlocfilehash: 2246e50c81da9eb505fd30cfa31f9f24e3fe4703
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459192"
---
# <a name="c-program-startup-and-termination"></a>Uruchamianie i kończenie działania programu C++

Program w języku C++ wykonuje te same operacje co C program w momencie uruchamiania programu i kończenie działania programu, a także kilka więcej opisana w tym temacie.

Przed docelowego środowiska wywołuje funkcję `main`, i po przechowuje stałej wartości początkowe określisz we wszystkich obiektach, które mają statyczny czas trwania, program wykonuje wszystkie pozostałe konstruktory takich obiektów statycznych. Kolejność wykonywania nie jest określony w zakresie od jednostki translacji, ale można jednak założyć, że niektóre [iostreams](../standard-library/iostreams-conventions.md) obiekty zostały poprawnie zainicjowane do użytku przez te konstruktorów statycznych. Te strumienie tekstu formantu są następujące:

- [CIN](../standard-library/iostream.md#cin) — Aby uzyskać standardowe dane wejściowe.

- [Cout](../standard-library/iostream.md#cout) — do wyjścia standardowego.

- [cerr](../standard-library/iostream.md#cerr) — dla Niebuforowane standardowe dane wyjściowe błędów.

- [clog —](../standard-library/iostream.md#clog) — dla buforowanych standardowe dane wyjściowe błędów.

Można również użyć tych obiektów w ramach destruktory wywoływana dla obiektów statycznych podczas Kończenie działania programu.

Podobnie jak w przypadku C, zwracanie z `main` lub wywoływania `exit` wywołuje funkcje wszystkie zarejestrowane w usłudze `atexit` w odwrotnej kolejności z rejestru. Wyjątek zgłoszony z takiego zarejestrowanych funkcja wywołuje `terminate`.

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
