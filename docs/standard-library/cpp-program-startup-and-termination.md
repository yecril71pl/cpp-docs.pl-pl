---
title: "Uruchamianie programu C++ i kończenie działania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- C++ Standard Library, program startup and termination
- terminating execution
- Function Main procedures
- control text streams
- startup code, and C++ program termination
- main function, program startup
ms.assetid: f72c8f76-f507-4ddd-a270-7b60f4fed625
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 24fda25f0d0766442e05c1661dce5e2f08a01b09
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-program-startup-and-termination"></a>Uruchamianie i kończenie działania programu C++
Program w języku C++ wykonuje te same operacje, jak C program w momencie uruchamiania programu i kończenie działania programu, a także kilka więcej opisana w tym temacie.  
  
 Przed elementem docelowym środowisko wywołuje funkcję `main`, a po przechowuje stałej wartości początkowe Określ wszystkich obiektów, które ma statyczny czasu trwania, program wykonuje wszelkie pozostałe konstruktory takie obiekty statyczne. Nie określono kolejność wykonywania między jednostek tłumaczenia, ale można jednak założyć, że niektóre [iostream](../standard-library/iostreams-conventions.md) obiekty zostały poprawnie zainicjowane do użytku przez te konstruktory statyczne. Te strumienie tekstu formantu są:  
  
-   [CIN](../standard-library/iostream.md#cin) — dla standardowe dane wejściowe.  
  
-   [Cout](../standard-library/iostream.md#cout) — do wyjścia standardowego.  
  
-   [cerr](../standard-library/iostream.md#cerr) — Niebuforowane błędów w danych wyjściowych.  
  
-   [clog —](../standard-library/iostream.md#clog) — dla buforowane dane wyjściowe błędów.  
  
 Umożliwia także te obiekty w ramach destruktory wywołana dla statycznych obiektów podczas Kończenie działania programu.  
  
 Podobnie jak w przypadku C, zwracanie z `main` lub wywoływania `exit` wywołuje wszystkich funkcji w zarejestrowany `atexit` w odwrotnej kolejności z rejestru. Wywołuje funkcję zarejestrowanych wyjątek zgłoszony z takiego `terminate`.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd biblioteki C++ Standard](../standard-library/cpp-standard-library-overview.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)


