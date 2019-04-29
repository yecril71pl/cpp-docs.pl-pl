---
title: Opcje łącz
ms.date: 11/04/2016
helpviewer_keywords:
- nothrownew.obj
- newmode.obj
- noenv.obj
- psetargv.obj
- loosefpmath.obj
- smallheap.obj
- fp10.obj
- nochkclr.obj
- chkstk.obj
- pcommode.obj
- pnoenv.obj
- link options [C++]
- invalidcontinue.obj
- pnothrownew.obj
- pwsetargv.obj
- pinvalidcontinue.obj
- wsetargv.obj
- binmode.obj
- setargv.obj
- noarg.obj
- pnewmode.obj
- commode.obj
- pthreadlocale.obj
- pbinmode.obj
- threadlocale.obj
- pnoarg.obj
ms.assetid: 05b5a77b-9dd1-494b-ae46-314598c770bb
ms.openlocfilehash: 8cd5513acd2617e784b2ec9fa203614b752e6076
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62342929"
---
# <a name="link-options"></a>Opcje łącz

W katalogu lib CRT obejmuje pewną liczbę plików małych obiektów, które umożliwiają określonych funkcji CRT, bez zmian kodu. Są one nazywane "Opcje łącza", ponieważ wystarczy dodać je do wiersza polecenia konsolidatora z nich korzystać.

Wersje pure tryb czysty CLR te obiekty są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017. Użyj wersji regularne dla kodu macierzystego i/CLR.

|Natywne i/CLR|Pure tryb czysty|Opis|
|----------------------|---------------|-----------------|
|binmode.obj|pbinmode.obj|Ustawia domyślny tryb translacji plików binarnych. Zobacz [_fmode](../c-runtime-library/fmode.md).|
|chkstk.obj|n/d|Umożliwia obsługę sprawdzeniem stosu i alloca bez korzystania z CRT.|
|commode.obj|pcommode.obj|Ustawia globalną flagę zatwierdzania do "commit". Zobacz [fopen —, _wfopen —](../c-runtime-library/reference/fopen-wfopen.md) i [fopen_s —, _wfopen_s —](../c-runtime-library/reference/fopen-s-wfopen-s.md).|
|exe_initialize_mta.lib|n/d|Inicjuje apartamentu MTA podczas uruchamiania EXE, który umożliwia korzystanie z obiektów COM w globalnych inteligentnych wskaźników. Ponieważ ta opcja przecieków odwołanie typu apartment MTA podczas zamykania systemu, nie jest używana dla bibliotek DLL. Łączenie z tym odpowiada tym combase.h i definiowanie _EXE_INITIALIZE_MTA. |
|fp10.obj|n/d|Zmienia domyślny formant precyzji 64-bitowy. Zobacz [Obsługa modelu zmiennoprzecinkowego](../c-runtime-library/floating-point-support.md).|
|invalidcontinue.obj|pinvalidcontinue.obj|Ustawia domyślną nieprawidłowy parametr uchwytu, które nie robi nic, co oznacza, że nieprawidłowe parametry przekazywane do funkcji CRT, będą po prostu ustawiają mechanizm errno i zwraca wynik błędu.|
|loosefpmath.obj|n/d|Zapewnia, że kod punktu zmiennoprzecinkowego zaakceptować wartości denormal.|
|newmode.obj|pnewmode.obj|Powoduje, że [— funkcja malloc](../c-runtime-library/reference/malloc.md) może wywołać nowy program obsługi błędów. Zobacz [_set_new_mode](../c-runtime-library/reference/set-new-mode.md), [_set_new_handler](../c-runtime-library/reference/set-new-handler.md), [calloc](../c-runtime-library/reference/calloc.md), i [realloc](../c-runtime-library/reference/realloc.md).|
|noarg.obj|pnoarg.obj|Wyłącza wszystkie przetwarzania argc — i argv.|
|nochkclr.obj|n/d|Nic nie robi. Usuń z projektu.|
|noenv.obj|pnoenv.obj|Wyłącza tworzenie pamięci podręcznej środowiska CRT.|
|nothrownew.obj|pnothrownew.obj|Umożliwia niezgłaszające wersję w CRT. Zobacz [nowych i delete — operatory](../cpp/new-and-delete-operators.md).|
|setargv.obj|psetargv.obj|Umożliwia rozwijanie symbolu wieloznacznego argument wiersza polecenia. Zobacz [rozszerzanie argumentów z symbolami wieloznacznymi](../c-language/expanding-wildcard-arguments.md).|
|threadlocale.obj|pthreadlocale.obj|Włącza na wątek ustawienia regionalne dla wszystkich nowych wątków domyślnie.|
|wsetargv.obj|pwsetargv.obj|Umożliwia rozwijanie symbolu wieloznacznego argument wiersza polecenia. Zobacz [rozszerzanie argumentów z symbolami wieloznacznymi](../c-language/expanding-wildcard-arguments.md).|

## <a name="see-also"></a>Zobacz także

- [Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)
