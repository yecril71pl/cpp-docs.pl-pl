---
title: Opcje łącz
ms.date: 11/04/2016
helpviewer_keywords:
- nothrownew.obj
- newmode.obj
- noenv.obj
- psetargv.obj
- legacy_stdio_float_rounding.obj
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
ms.openlocfilehash: ea71faab639a8c0a09d6e332618dd7e09159a4e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351100"
---
# <a name="link-options"></a>Opcje łącz

Katalog lib CRT zawiera szereg małych plików obiektów, które umożliwiają określone funkcje CRT bez zmiany kodu. Są one nazywane "opcje łącza", ponieważ wystarczy dodać je do wiersza polecenia konsolidatora, aby z nich korzystać.

Wersje trybu czystego CLR tych obiektów są przestarzałe w programie Visual Studio 2015 i nieobsługiwały w programie Visual Studio 2017. Użyj zwykłych wersji dla kodu macierzystego i /clr.

|Natywne i /clr|Tryb czysty|Opis|
|----------------------|---------------|-----------------|
|binmode.obj|pbinmode.obj|Ustawia domyślny tryb tłumaczenia plików na binarny. Zobacz [_fmode](../c-runtime-library/fmode.md).|
|chkstk.obj|Nie dotyczy|Zapewnia obsługę sprawdzania stosu i alloca, gdy nie jest używany CRT.|
|commode.obj|pcommode.obj|Ustawia globalną flagę zatwierdzania na "commit". Zobacz [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md) i [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md).|
|exe_initialize_mta.lib|Nie dotyczy|Inicjuje mieszkanie MTA podczas uruchamiania EXE, co umożliwia korzystanie z obiektów COM w globalnych inteligentnych wskaźnikach. Ponieważ ta opcja wycieka odwołanie do mieszkania MTA podczas zamykania, nie należy używać go do bibliotek DLL. Łączenie z tym jest równoważne z uwzględnieniem combase.h i definiowania _EXE_INITIALIZE_MTA. |
|fp10.obj|Nie dotyczy|Zmienia domyślną kontrolę precyzji na 64 bity. Zobacz [Obsługa zmiennoprzecinek](../c-runtime-library/floating-point-support.md).|
|invalidcontinue.obj|pinvalidcontinue.obj|Ustawia domyślny nieprawidłowy program obsługi parametrów, który nic nie robi, co oznacza, że nieprawidłowe parametry przekazywane do funkcji CRT po prostu ustawi errno i zwróci wynik błędu.|
|legacy_stdio_float_rounding.obj|Nie dotyczy|Poprawiono drukowanie wartości zmiennoprzecinkowych (na przykład podczas korzystania z [printf)](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)za pomocą uniwersalnego środowiska wykonawczego systemu Windows 10 19041. Teraz prawidłowo zaokrągla dokładnie reprezentowane liczby zmiennoprzecinające i respektuje zaokrąglanie zmiennoprzecinkowe wymagane przez [fesetenv](../c-runtime-library/reference/fesetenv1.md). Ta aktualizacja zachowania jest dostępna w programie Visual Studio 2019 w wersji 16.2 i nowszej. Starsze zachowanie jest używane we wcześniejszych wersjach programu Visual Studio lub przez podanie tej opcji łącza.|
|loosefpmath.obj|Nie dotyczy|Zapewnia, że kod zmiennoprzecinkowy toleruje wartości denormal.|
|newmode.obj|pnewmode.obj|Powoduje [malloc](../c-runtime-library/reference/malloc.md) wywołać nowy program obsługi na niepowodzenie. Zobacz [_set_new_mode](../c-runtime-library/reference/set-new-mode.md), [_set_new_handler](../c-runtime-library/reference/set-new-handler.md), [calloc](../c-runtime-library/reference/calloc.md)i [realloc](../c-runtime-library/reference/realloc.md).|
|noarg.obj|pnoarg.obj|Wyłącza wszystkie przetwarzanie argc i argv.|
|nochkclr.obj|Nie dotyczy|Nic nie robi. Usuń z projektu.|
|noenv.obj|pnoenv.obj|Wyłącza tworzenie środowiska buforowanego dla CRT.|
|nothrownew.obj|pnothrownew.obj|Włącza nierzucając wersji nowego w CRT. Zobacz [nowe i usuń operatory](../cpp/new-and-delete-operators.md).|
|setargv.obj|psetargv.obj|Włącza rozszerzenie symboli wieloznacznych argumentu wiersza polecenia. Zobacz [Rozwijanie argumentów symboli wieloznacznych](../c-language/expanding-wildcard-arguments.md).|
|threadlocale.obj|pthreadlocale.obj|Domyślnie włącza ustawienia regionalne dla wszystkich nowych wątków.|
|wsetargv.obj|pwsetargv.obj|Włącza rozszerzenie symboli wieloznacznych argumentu wiersza polecenia. Zobacz [Rozwijanie argumentów symboli wieloznacznych](../c-language/expanding-wildcard-arguments.md).|

## <a name="see-also"></a>Zobacz też

- [Funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md)
