---
title: Wydajność bibliotek wielowątkowych
description: Przegląd, jak uzyskać największą wydajność z bibliotek wielowątkowych środowiska uruchomieniowego Microsoft C.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- threading [C++], performance
- libraries, multithreaded
- performance, multithreading
- multithreaded libraries
ms.assetid: faa5d808-087c-463d-8f0d-8c478d137296
ms.openlocfilehash: edfbbf3055e9023c74cf0e154577d4b1853f557b
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590202"
---
# <a name="multithreaded-libraries-performance"></a>Wydajność bibliotek wielowątkowych

Jednowątkowy CRT nie jest już dostępny. W tym temacie omówiono, jak uzyskać maksymalną wydajność z bibliotek wielowątkowych.

## <a name="maximizing-performance"></a>Maksymalizowanie wydajności

Wydajność bibliotek wielowątkowych została ulepszona i jest bliska wydajności teraz usuniętych bibliotek jednowątkowych. W tych sytuacjach, gdy wymagana jest jeszcze większa wydajność, istnieje kilka nowych funkcji.

- Niezależne blokowanie strumienia umożliwia zablokowanie strumienia, a następnie użycie [funkcji _nolock](../c-runtime-library/nolock-functions.md) , które uzyskują bezpośredni dostęp do strumienia. Pozwala to na podkluczenie użycia blokady poza pętlą krytyczną.

- Ustawienia regionalne poszczególnych wątków zmniejszają koszt dostępu do ustawień regionalnych dla scenariuszy wielowątkowych (zobacz [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)).

- Funkcje zależne od ustawień regionalnych (z nazwami kończącymi się _l) przyjmują ustawienia regionalne jako parametr, usuwając koszt znaczący (na przykład [printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)).

- Optymalizacje dla wspólnych strony kodowej zmniejszają koszt wielu krótkich operacji.

- Zdefiniowanie [_CRT_DISABLE_PERFCRIT_LOCKS](../c-runtime-library/crt-disable-perfcrit-locks.md) wymusza wszystkie operacje we/wy, aby założyć model we/wy z jednym wątkiem, i użyć _nolock formularzy funkcji. Dzięki temu wysoce wielowątkowe aplikacje korzystające z operacji we/wy mogą uzyskać lepszą wydajność.

- Ekspozycja uchwytu sterty CRT umożliwia włączenie sterty niskiej fragmentacji systemu Windows (LFH) dla sterty CRT, co może znacznie poprawić wydajność w wysoce skalowalnych scenariuszach.

## <a name="see-also"></a>Zobacz też

[Funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md)
