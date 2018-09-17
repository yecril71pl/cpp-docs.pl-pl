---
title: _execute_onexit_table _initialize_onexit_table, _register_onexit_function | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- _execute_onexit_table
- _initialize_onexit_table
- _register_onexit_function
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _execute_onexit_table
- process/_execute_onexit_table
- _initialize_onexit_table
- process/_initialize_onexit_table
- _register_onexit_function
- process/_register_onexit_function
dev_langs:
- C++
helpviewer_keywords:
- _execute_onexit_table function
- _initialize_onexit_table function
- _register_onexit_function function
ms.assetid: ad9e4149-d4ad-4fdf-aaaf-cf786fcb4473
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a54e3e5f5f040c80660bd12e6565cef82d09206
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720957"
---
# <a name="executeonexittable-initializeonexittable-registeronexitfunction"></a>_execute_onexit_table _initialize_onexit_table, _register_onexit_function
Zarządza procedury wywoływanej w momencie zakończenia.  
  
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

*Tabela*<br/>
[out w] Wskaźnik do tablicy funkcji OnExit —.  
  
*— Funkcja*<br/>
[in] Wskaźnik do funkcji, można dodać do tabeli funkcji OnExit —.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość 0. W przeciwnym razie zwraca wartość ujemną.  
  
## <a name="remarks"></a>Uwagi  
 Te funkcje są szczegóły implementacji infrastruktury używane do obsługi środowiska uruchomieniowego C i nie powinna być wywoływana bezpośrednio w kodzie. Środowisko uruchomieniowe C używa *OnExit — funkcja tabeli* sekwencji zarejestrowane w wyniku wywołania funkcji `atexit`, `at_quick_exit`, i `_onexit`. Struktura danych OnExit — funkcja tabeli jest szczegółowo opisuje implementacja nieprzezroczyste środowiska uruchomieniowego C; kolejność i znaczenie składowych danych mogą ulec zmianie. Powinny one być nie kontrolowane przez kod zewnętrzny.  
  
 `_initialize_onexit_table` Funkcja inicjuje tabelę funkcji OnExit — do swojej wartości początkowej.  Ta funkcja musi zostać wywołana przed tabelę funkcji OnExit — jest przekazywany do obu `_register_onexit_function` lub `_execute_onexit_table`.  
  
 `_register_onexit_function` Funkcja dołącza funkcję do końca tablicy funkcji OnExit —.  
  
 `_execute_onexit_table` Funkcja wykonuje wszystkie funkcje w tabeli funkcji OnExit —, czyści tabeli, a następnie zwraca. Po wywołaniu `_execute_onexit_table`, tabela jest w stanie nie jest ważna; muszą zostać zainicjowane ponownie przez wywołanie `_initialize_onexit_table` zanim zostanie on użyty ponownie.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_initialize_onexit_table function`, `_register_onexit_function`, `_execute_onexit_table`|C, C++: \<process.h >|  
  
 `_initialize_onexit_table`, `_register_onexit_function`, I `_execute_onexit_table` funkcje są specyficzne dla firmy Microsoft. Aby uzyskać informacje o zgodności – zobacz [zgodności](../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [atexit](../c-runtime-library/reference/atexit.md)   
 [exit, _Exit, _exit](../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)