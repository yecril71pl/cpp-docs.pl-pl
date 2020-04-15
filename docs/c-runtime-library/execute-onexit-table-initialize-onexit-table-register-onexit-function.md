---
title: _execute_onexit_table, _initialize_onexit_table, _register_onexit_function
ms.date: 4/2/2020
api_name:
- _execute_onexit_table
- _initialize_onexit_table
- _register_onexit_function
- _o__execute_onexit_table
- _o__initialize_onexit_table
- _o__register_onexit_function
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _execute_onexit_table
- process/_execute_onexit_table
- _initialize_onexit_table
- process/_initialize_onexit_table
- _register_onexit_function
- process/_register_onexit_function
helpviewer_keywords:
- _execute_onexit_table function
- _initialize_onexit_table function
- _register_onexit_function function
ms.assetid: ad9e4149-d4ad-4fdf-aaaf-cf786fcb4473
ms.openlocfilehash: a1e35d9e86a43e48849373a1cf1aa07febcd0e33
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351653"
---
# <a name="_execute_onexit_table-_initialize_onexit_table-_register_onexit_function"></a>_execute_onexit_table, _initialize_onexit_table, _register_onexit_function

Zarządza procedurami, które mają być wywoływane w czasie zakończenia.

## <a name="syntax"></a>Składnia

```
int _initialize_onexit_table(
    _onexit_table_t* table
    );

int _register_onexit_function(
    _onexit_table_t* table,
    _onexit_t        function
    );

int _execute_onexit_table(
    _onexit_table_t* table
    );
```

#### <a name="parameters"></a>Parametry

*table*<br/>
[w, na zewnątrz] Wskaźnik do tabeli funkcji onexit.

*Funkcja*<br/>
[w] Wskaźnik do funkcji, aby dodać do tabeli funkcji onexit.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwraca wartość 0. W przeciwnym razie zwraca wartość ujemną.

## <a name="remarks"></a>Uwagi

Te funkcje są szczegóły implementacji infrastruktury używane do obsługi środowiska wykonawczego języka C i nie powinny być wywoływane bezpośrednio z kodu. Środowisko wykonawcze C używa *tabeli funkcji onexit* do reprezentowania `atexit` `at_quick_exit`sekwencji `_onexit`funkcji zarejestrowanych przez wywołania , i . Struktura danych tabeli funkcji onexit jest nieprzezroczyste szczegóły implementacji środowiska wykonawczego C; kolejność i znaczenie jego danych mogą ulec zmianie. Nie powinny one być kontrolowane przez kod zewnętrzny.

Funkcja `_initialize_onexit_table` inicjuje tabelę funkcji onexit do jej wartości początkowej.  Ta funkcja musi zostać wywołana przed przekazaniem tabeli funkcji onexit do jednego `_register_onexit_function` lub `_execute_onexit_table`.

Funkcja `_register_onexit_function` dołącza funkcję na końcu tabeli funkcji onexit.

Funkcja `_execute_onexit_table` wykonuje wszystkie funkcje w tabeli funkcji onexit, czyści tabelę, a następnie zwraca. Po wywołaniu `_execute_onexit_table`tabela jest w stanie nierozerwalnym; musi być ponownie zainicjowany przez `_initialize_onexit_table` wywołanie, zanim zostanie użyty ponownie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`_initialize_onexit_table function`, `_register_onexit_function`, `_execute_onexit_table`|C, C++: \<process.h>|

Program `_initialize_onexit_table` `_register_onexit_function`, `_execute_onexit_table` i funkcje są specyficzne dla firmy Microsoft. Aby uzyskać informacje o zgodności, zobacz [Zgodność](../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)
