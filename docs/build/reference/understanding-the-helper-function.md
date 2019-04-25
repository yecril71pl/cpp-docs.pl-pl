---
title: Ogólne informacje funkcji Pomocnik
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, helper function
- __delayLoadHelper2 function
- delayimp.lib
- __delayLoadHelper function
- delayhlp.cpp
- delayimp.h
- helper functions
ms.assetid: 6279c12c-d908-4967-b0b3-cabfc3e91d3d
ms.openlocfilehash: 3ad193d0101507f43145c6af9f8e6200ab6fcdb5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317669"
---
# <a name="understanding-the-helper-function"></a>Ogólne informacje funkcji Pomocnik

Funkcja pomocnika dla obsługiwanych przez program łączący opóźnionego ładowania to, co faktycznie ładuje bibliotekę DLL, w czasie wykonywania. Można zmodyfikować funkcji pomocnika, aby dostosować jego zachowanie własną funkcję zapisywania i łącząc go do programu, zamiast korzystać z funkcji pomocnika podane w Delayimp.lib. Jedna funkcja pomocnika służy wszystkie biblioteki DLL ładowane z opóźnieniem.

Możesz podać własnej wersji funkcji pomocnika, aby wykonywać określone przetwarzanie na podstawie nazw biblioteki DLL lub importów.

Funkcja pomocnika wykonuje następujące czynności:

- Sprawdza, czy przechowywane uchwyt do biblioteki, aby zobaczyć, jeśli już został załadowany

- Wywołania **LoadLibrary** prób podczas ładowania biblioteki dll

- Wywołania **GetProcAddress** próby pobierania adresu procedury

- Powrót do Opóźnij importowanie ładowania thunk wywołać punkt wejścia załadowane teraz

Funkcja pomocnika wywołania zwrotnego do zaczepienia powiadomień w programie po każdym z następujących czynności:

- Po uruchomieniu funkcji Pomocnik

- Tuż przed **LoadLibrary** jest wywoływana w funkcji Pomocnik

- Tuż przed **GetProcAddress** jest wywoływana w funkcji Pomocnik

- Jeśli wywołanie **LoadLibrary** w funkcji pomocnika nie powiodło się

- Jeśli wywołanie **GetProcAddress** w funkcji pomocnika nie powiodło się

- Po pomocnika odbywa się funkcja przetwarzania

Każda z tych punktów utworzenie punktu zaczepienia może zwrócić wartość, która będzie zastępowania normalnego przetwarzania procedury pomocnika w jakikolwiek sposób, z wyjątkiem zwraca thunk obciążenia importu opóźnienia.

Domyślny kod pomocnika można znaleźć w Delayhlp.cpp i Delayimp.h (w vc\include) i jest skompilowany w Delayimp.lib (w vc\lib). Należy uwzględnić tę bibliotekę w Twojej kompilacji, chyba że napisany został własnej funkcji Pomocnik.

Funkcja pomocnika można znaleźć w następujących tematach:

- [Zmiany w funkcjach pomocnika opóźnionego załadunku bibliotek DLL po Visual C++ 6.0](changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)

- [Konwencje wywoływania, parametry oraz zwracany typ](calling-conventions-parameters-and-return-type.md)

- [Struktura i stała, definicje](structure-and-constant-definitions.md)

- [Obliczanie niezbędnych wartości](calculating-necessary-values.md)

- [Zwalnianie bibliotek DLL załadowanych z opóźnieniem](explicitly-unloading-a-delay-loaded-dll.md)

## <a name="see-also"></a>Zobacz także

[Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](linker-support-for-delay-loaded-dlls.md)
