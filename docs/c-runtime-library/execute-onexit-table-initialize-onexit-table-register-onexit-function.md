---
title: _execute_onexit_table, _initialize_onexit_table, _register_onexit_function
ms.date: 11/04/2016
api_name:
- _execute_onexit_table
- _initialize_onexit_table
- _register_onexit_function
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
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
ms.openlocfilehash: bf8c61e467796c7bfaedff6918bfbf598ada528e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944371"
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

*tabele*<br/>
[in. out] Wskaźnik do tabeli funkcji OnExit.

*funkcyjn*<br/>
podczas Wskaźnik do funkcji, która ma zostać dodana do tabeli funkcji OnExit.

## <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, zwraca wartość 0. W przeciwnym razie zwraca wartość ujemną.

## <a name="remarks"></a>Uwagi

Te funkcje są szczegółami implementacji infrastruktury używanymi do obsługi środowiska uruchomieniowego języka C i nie powinny być wywoływane bezpośrednio z kodu. Środowisko uruchomieniowe języka C używa *tabeli funkcji OnExit* do reprezentowania sekwencji funkcji zarejestrowanych przez wywołania do `atexit`, `at_quick_exit`, i `_onexit`. Struktura danych tabeli funkcji OnExit to nieprzezroczysta implementacja szczegółów środowiska uruchomieniowego języka C. kolejność i znaczenie jego składowych danych mogą ulec zmianie. Nie powinny być sprawdzane przez kod zewnętrzny.

`_initialize_onexit_table` Funkcja inicjuje tabelę funkcji OnExit do jej początkowej wartości.  Ta funkcja musi zostać wywołana przed przekazaniem tabeli funkcji OnExit do `_register_onexit_function` elementu lub. `_execute_onexit_table`

`_register_onexit_function` Funkcja dołącza funkcję do końca tabeli funkcji OnExit.

`_execute_onexit_table` Funkcja wykonuje wszystkie funkcje w tabeli funkcji OnExit, czyści tabelę, a następnie zwraca. Po wywołaniu `_execute_onexit_table`, tabela jest w stanie nieprawidłowym; musi być zainicjowana przez `_initialize_onexit_table` wywołanie przed ponownym użyciem.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`_initialize_onexit_table function`, `_register_onexit_function`, `_execute_onexit_table`|C, C++: \<Process. h >|

Funkcje `_initialize_onexit_table`, `_register_onexit_function` i`_execute_onexit_table` są specyficzne dla firmy Microsoft. Aby uzyskać informacje o zgodności, zobacz [zgodność](../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)
