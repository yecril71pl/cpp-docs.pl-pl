---
title: Opcje łącza | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98965b94c83b69e15c38319d7bc5a6e4151b323e
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704889"
---
# <a name="link-options"></a>Opcje łącz

Katalogu lib CRT zawiera wiele plików małego obiektu, które umożliwiają określonych funkcji CRT bez zmiany kodu. Są one nazywane "Opcje łącza", ponieważ należy je dodać do wiersza polecenia konsolidatora z nich korzystać.

CLR pure tryb czysty wersje tych obiektów są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r. Za pomocą regularnego wersji dla kodu natywnego i/CLR.

|Natywne i/CLR|Pure tryb czysty|Opis|
|----------------------|---------------|-----------------|
|binmode.obj|pbinmode.obj|Ustawia domyślny tryb tłumaczenia pliku binarnego. Zobacz [_fmode —](../c-runtime-library/fmode.md).|
|chkstk.obj|n/d|Umożliwia obsługę sprawdzanie stosu i alloca, gdy nie używać CRT.|
|commode.obj|pcommode.obj|Ustawia flagi globalne zatwierdzenia "Zatwierdź". Zobacz [fopen —, _wfopen —](../c-runtime-library/reference/fopen-wfopen.md) i [fopen_s —, _wfopen_s —](../c-runtime-library/reference/fopen-s-wfopen-s.md).|
|fp10.obj|n/d|Zmienia domyślny precyzyjną kontrolę na 64-bitowy. Zobacz [Obsługa liczb zmiennoprzecinkowych](../c-runtime-library/floating-point-support.md).|
|invalidcontinue.obj|pinvalidcontinue.obj|Ustawia program obsługi nieprawidłowy parametr domyślny, który nie działa, co oznacza, że nieprawidłowe parametry przekazywane do innych funkcji CRT właśnie zostanie ustawiony numer błędu i zwraca wynik błędu.|
|loosefpmath.obj|n/d|Zapewnia, że zmiennoprzecinkową kod punktu zaakceptować Brak reprezentacji zmiennoprzecinkowej wartości.|
|newmode.obj|pnewmode.obj|Powoduje, że [— funkcja malloc](../c-runtime-library/reference/malloc.md) do wywołania nowy program obsługi w przypadku awarii. Zobacz [_set_new_mode —](../c-runtime-library/reference/set-new-mode.md), [_set_new_handler —](../c-runtime-library/reference/set-new-handler.md), [calloc —](../c-runtime-library/reference/calloc.md), i [realloc](../c-runtime-library/reference/realloc.md).|
|noarg.obj|pnoarg.obj|Wyłącza wszystkie przetwarzanie argc — i ARGV —.|
|nochkclr.obj|n/d|Nic nie robi. Usuń z projektu.|
|noenv.obj|pnoenv.obj|Wyłącza tworzenie pamięci podręcznej środowiska dla CRT.|
|nothrownew.obj|pnothrownew.obj|Umożliwia-zgłaszanie wersja nowych w CRT. Zobacz [nowy i delete — operatory](../cpp/new-and-delete-operators.md).|
|setargv.obj|psetargv.obj|Umożliwia rozwijanie symbolu wieloznacznego argumentu wiersza polecenia. Zobacz [rozszerzanie argumentów z symbolami wieloznacznymi](../c-language/expanding-wildcard-arguments.md).|
|threadlocale.obj|pthreadlocale.obj|Włącza dla każdego wątku ustawienia regionalne dla wszystkich nowych wątków domyślnie.|
|wsetargv.obj|pwsetargv.obj|Umożliwia rozwijanie symbolu wieloznacznego argumentu wiersza polecenia. Zobacz [rozszerzanie argumentów z symbolami wieloznacznymi](../c-language/expanding-wildcard-arguments.md).|

## <a name="see-also"></a>Zobacz także

- [Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)
