---
title: Uruchamianie programu C++ i kończenie działania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- C++ Standard Library, program startup and termination
- terminating execution
- Function Main procedures
- control text streams
- startup code, and C++ program termination
- main function, program startup
ms.assetid: f72c8f76-f507-4ddd-a270-7b60f4fed625
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f781df914384b553c53e5c42fe16d4c74c9ef99d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="c-program-startup-and-termination"></a>Uruchamianie i kończenie działania programu C++

Program w języku C++ wykonuje te same operacje, jak C program w momencie uruchamiania programu i kończenie działania programu, a także kilka więcej opisana w tym temacie.

Przed elementem docelowym środowisko wywołuje funkcję `main`, a po przechowuje stałej wartości początkowe Określ wszystkich obiektów, które ma statyczny czasu trwania, program wykonuje wszelkie pozostałe konstruktory takie obiekty statyczne. Nie określono kolejność wykonywania między jednostek tłumaczenia, ale można jednak założyć, że niektóre [iostream](../standard-library/iostreams-conventions.md) obiekty zostały poprawnie zainicjowane do użytku przez te konstruktory statyczne. Te strumienie tekstu formantu są:

- [CIN](../standard-library/iostream.md#cin) — dla standardowe dane wejściowe.

- [Cout](../standard-library/iostream.md#cout) — do wyjścia standardowego.

- [cerr](../standard-library/iostream.md#cerr) — Niebuforowane błędów w danych wyjściowych.

- [clog —](../standard-library/iostream.md#clog) — dla buforowane dane wyjściowe błędów.

Umożliwia także te obiekty w ramach destruktory wywołana dla statycznych obiektów podczas Kończenie działania programu.

Podobnie jak w przypadku C, zwracanie z `main` lub wywoływania `exit` wywołuje wszystkich funkcji w zarejestrowany `atexit` w odwrotnej kolejności z rejestru. Wywołuje funkcję zarejestrowanych wyjątek zgłoszony z takiego `terminate`.

## <a name="see-also"></a>Zobacz także

[Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
