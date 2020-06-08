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
ms.openlocfilehash: 146722fb0dd3a4fc774ede692808b1e6bfb1e5c7
ms.sourcegitcommit: fe146adb3a02872538637196bb3c45aeeeaaf5c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84506861"
---
# <a name="link-options"></a>Opcje łącz

Katalog CRT lib zawiera wiele plików obiektów małych, które umożliwiają korzystanie z określonych funkcji CRT bez żadnej zmiany kodu. Są one nazywane "opcjami łączy", ponieważ wystarczy dodać je do wiersza polecenia konsolidatora, aby je użyć.

Wersje trybu czystego środowiska CLR tych obiektów są przestarzałe w programie Visual Studio 2015 i nie są obsługiwane w programie Visual Studio 2017. Użyj zwykłych wersji kodu natywnego i/CLR.

|Natywne i/CLR|Tryb czysty|Opis|
|----------------------|---------------|-----------------|
|binmode.obj|pbinmode.obj|Ustawia domyślny tryb tłumaczenia plików na wartość binarną. Zobacz [_fmode](../c-runtime-library/fmode.md).|
|chkstk.obj|nie dotyczy|Zapewnia obsługę sprawdzania stosu i alloca, gdy nie jest używany CRT.|
|commode.obj|pcommode.obj|Ustawia globalną flagę zatwierdzania na "zatwierdzenie". Zobacz [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md) i [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md).|
|exe_initialize_mta. lib|nie dotyczy|Inicjuje Apartament komórki MTA podczas uruchamiania programu EXE, co umożliwia korzystanie z obiektów COM w globalnych wskaźnikach inteligentnych. Ponieważ ta opcja powoduje przeciek odwołania do komórki MTA podczas zamykania, nie należy używać go dla bibliotek DLL. Łączenie z tym jest równoważne z uwzględnieniem współdziałania. h i definiowania _EXE_INITIALIZE_MTA. |
|fp10.obj|nie dotyczy|Zmienia domyślny formant dokładności na 64 bitów. Zobacz [obsługę zmiennoprzecinkową](../c-runtime-library/floating-point-support.md).|
|invalidcontinue.obj|pinvalidcontinue.obj|Ustawia domyślną procedurę obsługi nieprawidłowego parametru, która nic nie robi, co oznacza, że nieprawidłowe parametry przesłane do funkcji CRT tylko ustawi errno i zwróci wynik błędu.|
|legacy_stdio_float_rounding. obj|nie dotyczy|Drukowanie wartości zmiennoprzecinkowych (na przykład podczas korzystania z [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)) przy użyciu uniwersalnego środowiska uruchomieniowego języka C systemu Windows 10 19041 zostało naprawione. Teraz prawidłowo zaokrągla dokładne wartości liczbowe zmiennoprzecinkowe i szanuje zaokrąglenie zmiennoprzecinkowe wymagane przez [fesetround](../c-runtime-library/reference/fegetround-fesetround2.md). Ta aktualizacja zachowania jest dostępna w programie Visual Studio 2019 w wersji 16,2 lub nowszej. Starsze zachowanie jest używane we wcześniejszych wersjach programu Visual Studio lub przez udostępnienie tej opcji linku.|
|loosefpmath.obj|nie dotyczy|Zapewnia, że kod zmiennoprzecinkowy dopuszcza wartości nienormalne.|
|newmode.obj|pnewmode.obj|Powoduje, że funkcja [malloc](../c-runtime-library/reference/malloc.md) wywołuje nowy program obsługi w przypadku awarii. Zobacz [_set_new_mode](../c-runtime-library/reference/set-new-mode.md), [_set_new_handler](../c-runtime-library/reference/set-new-handler.md), [calloc](../c-runtime-library/reference/calloc.md)i [realloc](../c-runtime-library/reference/realloc.md).|
|noarg.obj|pnoarg.obj|Wyłącza przetwarzanie argc i argv.|
|nochkclr.obj|nie dotyczy|Nic nie robi. Usuń z projektu.|
|noenv.obj|pnoenv.obj|Wyłącza tworzenie środowiska pamięci podręcznej dla CRT.|
|nothrownew.obj|pnothrownew.obj|Włącza niezgłaszaną wersję nowego w CRT. Zobacz [Operatory New i DELETE](../cpp/new-and-delete-operators.md).|
|setargv.obj|psetargv.obj|Włącza rozszerzanie symboli wieloznacznych argumentu wiersza polecenia. Zobacz [Rozszerzanie argumentów z symbolami wieloznacznymi](../c-language/expanding-wildcard-arguments.md).|
|threadlocale.obj|pthreadlocale.obj|Włącza domyślnie dla wszystkich nowych wątków ustawienia regionalne dla każdego wątku.|
|wsetargv.obj|pwsetargv.obj|Włącza rozszerzanie symboli wieloznacznych argumentu wiersza polecenia. Zobacz [Rozszerzanie argumentów z symbolami wieloznacznymi](../c-language/expanding-wildcard-arguments.md).|

## <a name="see-also"></a>Zobacz także

- [Funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md)
