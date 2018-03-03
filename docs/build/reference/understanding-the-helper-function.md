---
title: Opis funkcji Pomocnik | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, helper function
- __delayLoadHelper2 function
- delayimp.lib
- __delayLoadHelper function
- delayhlp.cpp
- delayimp.h
- helper functions
ms.assetid: 6279c12c-d908-4967-b0b3-cabfc3e91d3d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c3a013cf584c37f84331a5ab5dfe74eaa213c851
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="understanding-the-helper-function"></a>Ogólne informacje funkcji Pomocnik
Funkcja pomocnika służąca do ładowania opóźnionego obsługiwane konsolidatora to, co faktycznie ładuje bibliotekę DLL w czasie wykonywania. Funkcja pomocnika, aby dostosować zachowanie przy jego własnej funkcji zapisywania i łącząc go do programu zamiast przy użyciu funkcji pomocnika podany w Delayimp.lib można modyfikować. Jedna funkcja pomocnika służy wszystkie opóźnienie załadować biblioteki dll.  
  
 Musisz podać wersji funkcji pomocnika, jeśli chcesz zrobić przetwarzania specyficznego dla opartych na nazwach biblioteki DLL lub importowania.  
  
 Funkcja pomocnika wykonuje następujące czynności:  
  
-   Sprawdza dojście przechowywanych w bibliotece, aby zobaczyć, jeśli jego został już załadowany  
  
-   Wywołania **LoadLibrary** próby ładowania biblioteki dll  
  
-   Wywołania **GetProcAddress** próby uzyskiwania adresu procedury  
  
-   Zwraca do zaimportowania opóźnienie załadować thunk do wywołania punktu wejścia załadować teraz  
  
 Funkcja pomocnika można wywołania zwrotnego punktu zaczepienia powiadomień w programie po każdej z następujących czynności:  
  
-   Po uruchomieniu funkcji Pomocnik  
  
-   Tuż przed **LoadLibrary** jest wywoływana w funkcji pomocnika  
  
-   Tuż przed **GetProcAddress** jest wywoływana w funkcji pomocnika  
  
-   Jeśli wywołanie **LoadLibrary** w funkcji pomocnika nie powiodło się  
  
-   Jeśli wywołanie **GetProcAddress** w funkcji pomocnika nie powiodło się  
  
-   Po pomocnika odbywa się funkcja przetwarzania  
  
 Każdy z tych punktów utworzenie punktu zaczepienia może zwrócić wartość, która będzie zastępowania normalnego przetwarzania procedury pomocnika w jakikolwiek sposób, z wyjątkiem powrotu do thunk obciążenia importu opóźnienia.  
  
 Domyślny kod pomocnika można znaleźć w Delayhlp.cpp i Delayimp.h (w vc\include) i jest skompilowana w Delayimp.lib (w vc\lib). Należy do uwzględnienia w kompilacji z tej biblioteki, chyba że zapisu własnej funkcji Pomocnik.  
  
 Funkcja pomocnika można znaleźć w następujących tematach:  
  
-   [Zmiany w funkcjach pomocnika opóźnionego załadunku bibliotek DLL po Visual C++ 6.0](../../build/reference/changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)  
  
-   [Konwencje wywoływania, parametry oraz zwracany typ](../../build/reference/calling-conventions-parameters-and-return-type.md)  
  
-   [Struktura i stała, definicje](../../build/reference/structure-and-constant-definitions.md)  
  
-   [Obliczanie niezbędnych wartości](../../build/reference/calculating-necessary-values.md)  
  
-   [Zwalnianie bibliotek DLL załadowanych z opóźnieniem](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/linker-support-for-delay-loaded-dlls.md)