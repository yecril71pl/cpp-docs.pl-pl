---
title: '&lt;Oprócz&gt;'
ms.date: 11/04/2016
f1_keywords:
- <exception>
helpviewer_keywords:
- exception header
ms.assetid: 28900768-5dd7-4834-b907-5e37ab3407db
ms.openlocfilehash: 1533e8238b40f6ca5dc6faaef35a65db9020defd
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835972"
---
# <a name="ltexceptiongt"></a>&lt;Oprócz&gt;

Definiuje kilka typów i funkcji związanych z obsługą wyjątków. Obsługa wyjątków jest używana w sytuacjach, w których system może odzyskać sprawność po błędzie. Zapewnia środek kontroli, który ma być zwracany z funkcji do programu. Celem włączenia obsługi wyjątków jest zwiększenie niezawodności programu przy jednoczesnym zapewnieniu sposobu odzyskania sprawności po błędzie w sposób uporządkowany.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<exception>

**Przestrzeń nazw:** std

## <a name="members"></a>Elementy członkowskie

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|-|-|
|[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)|Typ, który opisuje wskaźnik do wyjątku.|
|[terminate_handler](../standard-library/exception-typedefs.md#terminate_handler)|Typ, który opisuje wskaźnik do funkcji odpowiedniej do użycia jako `terminate_handler` .|
|[unexpected_handler](../standard-library/exception-typedefs.md#unexpected_handler)|Typ, który opisuje wskaźnik do funkcji odpowiedniej do użycia jako `unexpected_handler` .|

### <a name="functions"></a>Functions

|Nazwa|Opis|
|-|-|
|[current_exception](../standard-library/exception-functions.md#current_exception)|Uzyskuje wskaźnik do bieżącego wyjątku.|
|[get_terminate](../standard-library/exception-functions.md#get_terminate)|Uzyskuje bieżącą `terminate_handler` funkcję.|
|[get_unexpected](../standard-library/exception-functions.md#get_unexpected)|Uzyskuje bieżącą `unexpected_handler` funkcję.|
|[make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr)|Tworzy `exception_ptr` obiekt, który przechowuje kopię wyjątku.|
|[rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)|Zgłasza wyjątek przekazany jako parametr.|
|[rethrow_if_nested](../standard-library/exception-functions.md#rethrow_if_nested)|Rzutuje i zgłasza wyjątek, jeśli jest zagnieżdżony.|
|[set_terminate](../standard-library/exception-functions.md#set_terminate)|Ustanawia nowy `terminate_handler` , który zostanie wywołany po zakończeniu działania programu.|
|[set_unexpected](../standard-library/exception-functions.md#set_unexpected)|Ustanawia nowy, `unexpected_handler` gdy zostanie napotkany nieoczekiwany wyjątek.|
|[kończyć](../standard-library/exception-functions.md#terminate)|Wywołuje terminate_handler.|
|[throw_with_nested](../standard-library/exception-functions.md#throw_with_nested)|Zgłasza wyjątek, jeśli jest zagnieżdżony.|
|[uncaught_exception](../standard-library/exception-functions.md#uncaught_exception)|Zwraca **`true`** tylko wtedy, gdy zgłoszony wyjątek jest aktualnie przetwarzany.|
|[oczekiwan](../standard-library/exception-functions.md#unexpected)|Wywołuje program obsługi nieoczekiwanych wyjątków.|

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|-|-|
|[Klasa bad_exception](../standard-library/bad-exception-class.md)|Klasa opisuje wyjątek, który może zostać wygenerowany z `unexpected_handler` .|
|[Klasa wyjątku](../standard-library/exception-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków zgłoszonych przez niektóre wyrażenia i przez standardową bibliotekę języka C++.|
|[Klasa nested_exception](../standard-library/nested-exception-class.md)|Klasa opisuje wyjątek, który może zostać przechwycony i zapisany do późniejszego użycia.|

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
