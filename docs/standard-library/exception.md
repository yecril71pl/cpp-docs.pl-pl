---
title: '&lt;Oprócz&gt;'
ms.date: 11/04/2016
f1_keywords:
- <exception>
helpviewer_keywords:
- exception header
ms.assetid: 28900768-5dd7-4834-b907-5e37ab3407db
ms.openlocfilehash: 681baee5ac5d19e8b3ffdf37c37599c9cb68f253
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457903"
---
# <a name="ltexceptiongt"></a>&lt;Oprócz&gt;

Definiuje kilka typów i funkcji związanych z obsługą wyjątków. Obsługa wyjątków jest używana w sytuacjach, w których system może odzyskać sprawność po błędzie. Zapewnia środek kontroli, który ma być zwracany z funkcji do programu. Celem włączenia obsługi wyjątków jest zwiększenie niezawodności programu przy jednoczesnym zapewnieniu sposobu odzyskania sprawności po błędzie w sposób uporządkowany.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> wyjątku

**Przestrzeń nazw:** std

## <a name="members"></a>Elementy członkowskie

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)|Typ, który opisuje wskaźnik do wyjątku.|
|[terminate_handler](../standard-library/exception-typedefs.md#terminate_handler)|Typ, który opisuje wskaźnik do funkcji odpowiedniej do użycia jako `terminate_handler`.|
|[unexpected_handler](../standard-library/exception-typedefs.md#unexpected_handler)|Typ, który opisuje wskaźnik do funkcji odpowiedniej do użycia jako `unexpected_handler`.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[current_exception](../standard-library/exception-functions.md#current_exception)|Uzyskuje wskaźnik do bieżącego wyjątku.|
|[get_terminate](../standard-library/exception-functions.md#get_terminate)|Uzyskuje bieżącą `terminate_handler` funkcję.|
|[get_unexpected](../standard-library/exception-functions.md#get_unexpected)|Uzyskuje bieżącą `unexpected_handler` funkcję.|
|[make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr)|`exception_ptr` Tworzy obiekt, który przechowuje kopię wyjątku.|
|[rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)|Zgłasza wyjątek przekazany jako parametr.|
|[rethrow_if_nested](../standard-library/exception-functions.md#rethrow_if_nested)|Rzutuje i zgłasza wyjątek, jeśli jest zagnieżdżony.|
|[set_terminate](../standard-library/exception-functions.md#set_terminate)|Ustanawia nowy `terminate_handler` , który zostanie wywołany po zakończeniu działania programu.|
|[set_unexpected](../standard-library/exception-functions.md#set_unexpected)|Ustanawia nowy `unexpected_handler` , gdy zostanie napotkany nieoczekiwany wyjątek.|
|[kończyć](../standard-library/exception-functions.md#terminate)|Wywołuje terminate_handler.|
|[throw_with_nested](../standard-library/exception-functions.md#throw_with_nested)|Zgłasza wyjątek, jeśli jest zagnieżdżony.|
|[uncaught_exception](../standard-library/exception-functions.md#uncaught_exception)|Zwraca **wartość true** tylko wtedy, gdy zgłoszony wyjątek jest aktualnie przetwarzany.|
|[oczekiwan](../standard-library/exception-functions.md#unexpected)|Wywołuje program obsługi nieoczekiwanych wyjątków.|

### <a name="classes"></a>Klasy

|||
|-|-|
|[bad_exception, klasa](../standard-library/bad-exception-class.md)|Klasa opisuje wyjątek, który może zostać wygenerowany z `unexpected_handler`.|
|[exception, klasa](../standard-library/exception-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych przez niektóre wyrażenia i przez bibliotekę C++ standardową.|
|[Klasa nested_exception](../standard-library/nested-exception-class.md)|Klasa opisuje wyjątek, który może zostać przechwycony i zapisany do późniejszego użycia.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
