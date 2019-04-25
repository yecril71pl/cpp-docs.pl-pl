---
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson
ms.date: 11/04/2016
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
ms.openlocfilehash: e43d5caaeebb6303d209d870c804357117812985
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157542"
---
# <a name="invalidparameter-invalidparameternoinfo-invalidparameternoinfonoreturn-invokewatson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson

Te funkcje są używane przez biblioteki środowiska uruchomieniowego języka C do obsługi nieprawidłowych parametrów przekazana do funkcji biblioteki CRT. Na potrzeby obsługi domyślne lub możliwe do dostosowania obsługi nieprawidłowych parametrów kodu możesz skorzystać z tych funkcji.

## <a name="syntax"></a>Składnia

```C
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

## <a name="parameters"></a>Parametry

*expression*<br/>
Ciąg reprezentujący wyrażenie parametru kodu źródłowego, które jest nieprawidłowy.

*nazwa_funkcji*<br/>
Nazwa funkcji, która wywołuje program obsługi.

*nazwa_pliku*<br/>
Plik kodu źródłowego, gdzie został wywołany program obsługi.

*line_number*<br/>
Numer wiersza w kodzie źródłowym, gdzie został wywołany program obsługi.

*Zastrzeżone*<br/>
Nieużywane.

## <a name="return-value"></a>Wartość zwracana

Te funkcje nie zwracają wartości. **_Invalid_parameter_noinfo_noreturn** i **_invoke_watson** funkcje nie zwracają do obiektu wywołującego, a w niektórych przypadkach **_invalid_parameter** i **_invalid_parameter_noinfo** mogą nie zwracać wywołującemu.

## <a name="remarks"></a>Uwagi

Gdy funkcje biblioteki środowiska uruchomieniowego języka C przekazano nieprawidłowe parametry, biblioteka funkcji wywołanie *nieprawidłowy parametr uchwytu*, funkcja, która może być określone przez programisty, należy wykonać kilka czynności. Na przykład go może zgłosić problem do użytkownika, zapisu w dzienniku, przerwanie w debugerze, zakończyć program lub nie rób nic w ogóle. Jeśli żadna funkcja nie jest określony przez programistę domyślny program obsługi **_invoke_watson**, jest wywoływana.

Domyślnie, gdy nie jest prawidłowym parametrem jest zidentyfikowany w kodzie debugowania funkcji biblioteki CRT wywołanie funkcji **_invalid_parameter** przy użyciu pełnych parametrów. W kodzie bez debugowania **_invalid_parameter_noinfo** zostanie wywołana funkcja, która wywołuje metodę **_invalid_parameter** funkcję za pomocą puste parametry. Jeśli funkcja biblioteki CRT bez debugowania wymaga zakończenie programu **_invalid_parameter_noinfo_noreturn** zostanie wywołana funkcja, która wywołuje metodę **_invalid_parameter** funkcję za pomocą pustego Parametry, następuje wywołanie **_invoke_watson** funkcję, aby wymusić zakończenie programu.

**_Invalid_parameter** funkcja sprawdza czy ustawiono użytkownika nieprawidłowy parametr uchwytu, a jeśli tak, ją wywołuje. Na przykład, jeśli program obsługi wątków lokalnych zdefiniowanych przez użytkownika została ustawiona przez wywołanie [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) w bieżącym wątku, jest wywoływana, wówczas funkcja zwraca. W przeciwnym razie, jeśli zdefiniowany przez użytkownika globalnego nieprawidłowy parametr uchwytu została ustawiona przez wywołanie [set_invalid_parameter_handler —](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md), jest wywoływana, a następnie funkcja zwraca. W przeciwnym razie domyślny program obsługi **_invoke_watson** jest wywoływana. Domyślne zachowanie **_invoke_watson** jest, aby zakończyć program. Programy obsługi zdefiniowane przez użytkownika może zakończyć lub return. Firma Microsoft zaleca, programy obsługi zdefiniowane przez użytkownika zakończyć program, chyba że odzyskiwania jest określone.

Gdy domyślny program obsługi **_invoke_watson** jest wywoływana, gdy procesor obsługuje [__fastfail](../../intrinsics/fastfail.md) operacji jest wywoływany przy użyciu parametru **FAST_FAIL_INVALID_ARG** i kończy proces. W przeciwnym razie niepowodzenie szybkie zgłaszany jest wyjątek, który może zostać przechwycony przez dołączony debuger. Jeśli ten proces może być kontynuowane, zostanie zakończony przez wywołanie Windows **TerminateProcess** funkcję za pomocą stan kod wyjątku **STATUS_INVALID_CRUNTIME_PARAMETER**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|------------------|
|**_invalid_parameter**, **_invalid_parameter_noinfo**, **_invalid_parameter_noinfo_noreturn**, **_invoke_watson**|\<corecrt.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Walidacja parametru](../../c-runtime-library/parameter-validation.md)<br/>
