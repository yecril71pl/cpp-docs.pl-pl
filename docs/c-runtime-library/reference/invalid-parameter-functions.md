---
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- CORECRT/_invalid_parameter
- _invalid_parameter
- CORECRT/_invalid_parameter_noinfo
- _invalid_parameter_noinfo
- CORECRT/_invalid_parameter_noinfo_noreturn
- _invalid_parameter_noinfo_noreturn
- CORECRT/_invoke_watson
- _invoke_watson
ms.assetid: a4d6f1fd-ce56-4783-8719-927151a7a814
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 258d3e3aa9f005c76b5e4f2b3739ee588cde3f0a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="invalidparameter-invalidparameternoinfo-invalidparameternoinfonoreturn-invokewatson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson
Funkcje te są używane przez biblioteki wykonawczej C do obsługi nieprawidłowych parametrów przekazanych do funkcji CRT biblioteki. Kod może także korzystania z tych funkcji do obsługi domyślne lub dostosować obsługi nieprawidłowych parametrów.

## <a name="syntax"></a>Składnia
```
extern "C" void __cdecl 
_invalid_parameter(
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);  

extern "C" void __cdecl 
_invalid_parameter_noinfo(void);  

extern "C" __declspec(noreturn) void __cdecl 
_invalid_parameter_noinfo_noreturn(void);  

extern "C" __declspec(noreturn) void __cdecl 
_invoke_watson(  
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);
```

## <a name="return-value"></a>Wartość zwracana
Te funkcje nie zwracają wartość. `_invalid_parameter_noinfo_noreturn` i `_invoke_watson` nie zwracają do elementu wywołującego, a w niektórych przypadkach `_invalid_parameter` i `_invalid_parameter_noinfo` nie może zwracać do obiektu wywołującego.

## <a name="parameters"></a>Parametry
`expression`  
Ciąg reprezentujący wyrażenie parametru kodu źródłowego jest nieprawidłowy.

`function_name`  
Nazwa funkcji, która wywołuje program obsługi.

`file_name`  
Pliku źródła kodu, gdy została wywołana przez program obsługi.

`line_number`  
Numer wiersza w kodzie źródłowym, gdy została wywołana przez program obsługi.

`reserved`  
Nieużywane.

## <a name="remarks"></a>Uwagi
Gdy funkcje biblioteki czasu wykonywania języka C przekazano nieprawidłowe parametry, biblioteka funkcji wywołania *program obsługi nieprawidłowych parametrów*, funkcji, która może zostać określona przez programistę wykonywać kilka czynności. Na przykład go może Zgłoś problem do użytkownika, zapisu w dzienniku, przerwanie w debugerze, zakończyć program lub w ogóle nic nie rób. Jeśli funkcja nie jest określona przez programistę domyślny program obsługi `_invoke_watson`, nosi nazwę.

Domyślnie, gdy nie jest prawidłowym parametrem zostanie zidentyfikowana w debugowaniu kodu, funkcje bibliotek CRT wywołanie funkcji `_invalid_parameter` przy użyciu pełnego parametrów. W kodzie bez debugowania `_invalid_parameter_noinfo` funkcja jest wywoływana, które wywołuje `_invalid_parameter` funkcji przy użyciu parametrów puste. Jeśli funkcja biblioteki CRT bez debugowania wymaga zakończenie programu `_invalid_parameter_noinfo_noreturn` funkcja jest wywoływana, które wywołuje `_invalid_parameter` funkcji przy użyciu parametrów pusty, a następnie przez wywołanie do `_invoke_watson` funkcji, aby wymusić Kończenie działania programu.

`_invalid_parameter` Funkcji kontroli czy ustawiono obsługi zdefiniowane przez użytkownika nieprawidłowy parametr, a jeśli tak, określa je. Na przykład, jeśli program lokalnej wątku obsługi zdefiniowane przez użytkownika została ustawiona przez wywołanie do [set_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) w bieżącym wątku jest wywoływana, a następnie zwraca funkcję. W przeciwnym razie, jeśli program obsługi zdefiniowane przez użytkownika globalne nieprawidłowy parametr został ustawiony przez wywołanie do [set_invalid_parameter_handler —](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md), jest ona wywoływana, a następnie zwraca funkcję. W przeciwnym razie domyślny program obsługi `_invoke_watson` jest wywoływana. Domyślne zachowanie `_invoke_watson` jest, aby zakończyć program. Programy obsługi zdefiniowane przez użytkownika może zakończyć lub return. Firma Microsoft zaleca, programy obsługi zdefiniowane przez użytkownika zakończyć program, chyba że odzyskiwanie zostało określone. 

Gdy domyślny program obsługi `_invoke_watson` jest wywoływana, gdy procesor obsługuje [__fastfail](../../intrinsics/fastfail.md) operacji jest wywoływana przy użyciu parametru `FAST_FAIL_INVALID_ARG` i kończy proces. W przeciwnym razie wartość niepowodzenie szybkiego Wystąpił wyjątek, które mogą podlegać dołączony debuger. Jeśli proces będzie mógł kontynuować, zostanie zakończony przez wywołanie do systemu Windows `TerminateProcess` funkcji przy użyciu stan kod wyjątku `STATUS_INVALID_CRUNTIME_PARAMETER`. 

## <a name="requirements"></a>Wymagania  
|Funkcja|Wymagany nagłówek|  
|--------------|------------------|  
|`_invalid_parameter`, `_invalid_parameter_noinfo`, `_invalid_parameter_noinfo_noreturn`, `_invoke_watson`|\<corecrt.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Alfabetyczne odwołanie funkcji](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)  
 [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](../../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)  
 [Walidacja parametru](../../c-runtime-library/parameter-validation.md)
