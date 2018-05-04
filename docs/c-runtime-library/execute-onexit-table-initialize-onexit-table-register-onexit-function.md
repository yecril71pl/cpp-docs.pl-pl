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
ms.openlocfilehash: 1e1f4ebf40bc242d0daf98bbc85c2ea3d1295043
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
 [inout] `table`  
 Wskaźnik do tabeli OnExit — funkcja.  
  
 [in] `function`  
 Wskaźnik do funkcji, aby dodać do tabeli OnExit — funkcja.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość 0. W przeciwnym razie zwraca wartość ujemną.  
  
## <a name="remarks"></a>Uwagi  
 Te funkcje są szczegóły implementacji infrastruktury używana do obsługi środowiska uruchomieniowego C i nie powinna być wywoływana bezpośrednio w kodzie. Używa C runtime *OnExit — funkcja tabeli* sekwencji zarejestrowane w wyniku wywołania funkcji `atexit`, `at_quick_exit`, i `_onexit`. Szczegóły implementacji nieprzezroczyste C środowiska uruchomieniowego; jest struktury danych tabeli OnExit — funkcja kolejność i znaczenie elementów członkowskich danych mogą ulec zmianie. Powinny one być nie kontrolowane przez kod zewnętrzny.  
  
 `_initialize_onexit_table` Funkcja inicjuje tabeli OnExit — funkcja do swojej wartości początkowej.  Ta funkcja musi być wywołana przed OnExit — funkcja tabeli są przekazywane jako `_register_onexit_function` lub `_execute_onexit_table`.  
  
 `_register_onexit_function` Funkcja dołącza funkcję na końcu tabeli OnExit — funkcja.  
  
 `_execute_onexit_table` Wykonuje wszystkie funkcje w tabeli funkcji OnExit — funkcja, czyści tabeli, a następnie zwraca. Po wywołaniu `_execute_onexit_table`, tabela jest w stanie nieprawidłowych; muszą zostać zainicjowane ponownie przez wywołanie do `_initialize_onexit_table` zanim zostanie on użyty ponownie.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_initialize_onexit_table function`, `_register_onexit_function`, `_execute_onexit_table`|C, C++: \<process.h >|  
  
 `_initialize_onexit_table`, `_register_onexit_function`, I `_execute_onexit_table` funkcje są określone firmy Microsoft. Aby uzyskać informacje dotyczące zgodności, zobacz [zgodności](../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [atexit —](../c-runtime-library/reference/atexit.md)   
 [exit, _exit — _exit —](../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)