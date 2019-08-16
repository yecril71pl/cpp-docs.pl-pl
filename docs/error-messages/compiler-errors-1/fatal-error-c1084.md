---
title: Błąd krytyczny C1084
ms.date: 11/04/2016
f1_keywords:
- C1084
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
ms.openlocfilehash: b0c8e6a8f8321dccdfd7cee128a4cf06cebda991
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501135"
---
# <a name="fatal-error-c1084"></a>Błąd krytyczny C1084

Nie można odczytać pliku z plikiem, plik: "plik": komunikat

Ten błąd jest zwykle wynikiem wywołania wewnętrznego interfejsu API systemu wykonanego przez kompilator. Komunikat wyświetlany po napotkaniu tego błędu jest często generowany przez [_wcserror_s](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) lub [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage).

Wykonanie poniższych kroków może pomóc w rozwiązaniu C1084:

- Upewnij się, że określony plik istnieje.

- Upewnij się, że odpowiednie uprawnienia są ustawione w celu uzyskania dostępu do określonego pliku.

- Upewnij się, że składnia wiersza polecenia jest zgodna z regułami opisanymi w sekcji [składnia wiersza polecenia kompilatora](../../build/reference/compiler-command-line-syntax.md).

- Upewnij się, że zmienne środowiskowe **tmp** i **temp** są prawidłowo ustawione, a także odpowiednie uprawnienia, aby uzyskać dostęp do katalogów, do których odwołują się te zmienne środowiskowe. Należy również upewnić się, że dyski, do których odwołuje się obiekt **tmp** i **tymczasowe** zmienne środowiskowe, zawierają odpowiednią ilość wolnego miejsca.

- Jeśli komunikat brzmi "zły numer pliku", określony plik mógł zostać zamknięty na pierwszym planie podczas kompilowania w tle.

Po wykonaniu powyższej diagnostyki Wykonaj czystą kompilację.