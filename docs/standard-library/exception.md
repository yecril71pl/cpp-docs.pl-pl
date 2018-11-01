---
title: '&lt;wyjątek&gt;'
ms.date: 11/04/2016
f1_keywords:
- <exception>
helpviewer_keywords:
- exception header
ms.assetid: 28900768-5dd7-4834-b907-5e37ab3407db
ms.openlocfilehash: 6260b100bf62662738cb5fa1c5f74df89086f033
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612800"
---
# <a name="ltexceptiongt"></a>&lt;wyjątek&gt;

Definiuje kilka typów i funkcji związanych z obsługą wyjątków. Obsługa wyjątków jest używana w sytuacjach, w których system może odzyskać sprawność po błędzie. Zapewnia środek kontroli, który ma być zwracany z funkcji do programu. Celem włączenia obsługi wyjątków jest zwiększenie niezawodności programu przy jednoczesnym zapewnieniu sposobu odzyskania sprawności po błędzie w sposób uporządkowany.

## <a name="syntax"></a>Składnia

```cpp
#include <exception>

```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)|Typ, który opisuje wskaźnik do wyjątku.|
|[terminate_handler](../standard-library/exception-typedefs.md#terminate_handler)|Typ, który opisuje wskaźnik do funkcji odpowiedni do użytku jako `terminate_handler`.|
|[unexpected_handler](../standard-library/exception-typedefs.md#unexpected_handler)|Typ, który opisuje wskaźnik do funkcji odpowiedni do użytku jako `unexpected_handler`.|

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[current_exception](../standard-library/exception-functions.md#current_exception)|Uzyskuje wskaźnik do bieżącego wyjątku.|
|[get_terminate](../standard-library/exception-functions.md#get_terminate)|Uzyskuje bieżącą `terminate_handler` funkcji.|
|[get_unexpected](../standard-library/exception-functions.md#get_unexpected)|Uzyskuje bieżącą `unexpected_handler` funkcji.|
|[make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr)|Tworzy `exception_ptr` obiekt, który przechowuje kopię wyjątku.|
|[rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)|Zgłasza wyjątek przekazany jako parametr.|
|[set_terminate](../standard-library/exception-functions.md#set_terminate)|Ustanawia nowy `terminate_handler` wywoływany przy zakończeniu programu.|
|[set_unexpected](../standard-library/exception-functions.md#set_unexpected)|Ustanawia nowy `unexpected_handler` się kiedy napotkane nieoczekiwane wyjątki.|
|[Zakończenie](../standard-library/exception-functions.md#terminate)|Wywołuje terminate_handler.|
|[uncaught_exception](../standard-library/exception-functions.md#uncaught_exception)|Zwraca **true** tylko wtedy, gdy zgłoszony wyjątek jest obecnie przetwarzany.|
|[Nieoczekiwany](../standard-library/exception-functions.md#unexpected)|Wywołuje program obsługi nieoczekiwanych wyjątków.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[bad_exception, klasa](../standard-library/bad-exception-class.md)|Klasa opisuje wyjątek, który może zostać wygenerowany z `unexpected_handler`.|
|[exception, klasa](../standard-library/exception-class.md)|Klasa służy jako klasa bazowa dla wszystkich wyjątków generowanych przez niektóre wyrażenia i standardowej biblioteki języka C++.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
