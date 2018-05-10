---
title: '&lt;wyjątek&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <exception>
dev_langs:
- C++
helpviewer_keywords:
- exception header
ms.assetid: 28900768-5dd7-4834-b907-5e37ab3407db
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbd57085225bb21b9f7ce8bd34c537d3bc414797
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="ltexceptiongt"></a>&lt;Wyjątek&gt;

Definiuje kilka typów i funkcji związanych z obsługą wyjątków. Obsługa wyjątków jest używana w sytuacjach, w których system może odzyskać sprawność po błędzie. Zapewnia środek kontroli, który ma być zwracany z funkcji do programu. Celem włączenia obsługi wyjątków jest zwiększenie niezawodności programu przy jednoczesnym zapewnieniu sposobu odzyskania sprawności po błędzie w sposób uporządkowany.

## <a name="syntax"></a>Składnia

```cpp
#include <exception>

```

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)|Typ, który opisuje wskaźnik do wyjątku.|
|[terminate_handler](../standard-library/exception-typedefs.md#terminate_handler)|Typ, który opisuje wskaźnika do funkcji, które są odpowiednie do użycia jako `terminate_handler`.|
|[unexpected_handler](../standard-library/exception-typedefs.md#unexpected_handler)|Typ, który opisuje wskaźnika do funkcji, które są odpowiednie do użycia jako `unexpected_handler`.|

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[current_exception](../standard-library/exception-functions.md#current_exception)|Uzyskuje wskaźnik do bieżącego wyjątku.|
|[get_terminate](../standard-library/exception-functions.md#get_terminate)|Pobiera bieżący `terminate_handler` funkcji.|
|[get_unexpected](../standard-library/exception-functions.md#get_unexpected)|Pobiera bieżący `unexpected_handler` funkcji.|
|[make_exception_ptr](../standard-library/exception-functions.md#make_exception_ptr)|Tworzy `exception_ptr` obiekt przechowujący kopię Wystąpił wyjątek.|
|[rethrow_exception](../standard-library/exception-functions.md#rethrow_exception)|Zgłasza wyjątek przekazany jako parametr.|
|[set_terminate —](../standard-library/exception-functions.md#set_terminate)|Określa nową `terminate_handler` ma być wywoływana po zakończeniu programu.|
|[set_unexpected](../standard-library/exception-functions.md#set_unexpected)|Określa nową `unexpected_handler` się po wystąpił nieoczekiwany wyjątek napotkano.|
|[Zakończenie](../standard-library/exception-functions.md#terminate)|Wywołuje terminate_handler.|
|[uncaught_exception](../standard-library/exception-functions.md#uncaught_exception)|Zwraca **true** tylko wtedy, gdy zwrócony wyjątek jest obecnie przetwarzana w.|
|[Nieoczekiwany](../standard-library/exception-functions.md#unexpected)|Wywołuje program obsługi nieoczekiwanych wyjątków.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[bad_exception, klasa](../standard-library/bad-exception-class.md)|Klasa opisuje wyjątek, który może zostać wygenerowany z `unexpected_handler`.|
|[exception, klasa](../standard-library/exception-class.md)|Klasa służy jako klasa podstawowa dla wszystkich wyjątków zgłoszonych przez niektórych wyrażeń i standardowa biblioteka C++.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
