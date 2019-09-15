---
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson
ms.date: 11/04/2016
api_name:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: b2714c140a2396d88c700689244c6ec04e12169c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954610"
---
# <a name="_invalid_parameter-_invalid_parameter_noinfo-_invalid_parameter_noinfo_noreturn-_invoke_watson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson

Te funkcje są używane przez bibliotekę środowiska uruchomieniowego języka C do obsługi nieprawidłowych parametrów przekazaną do funkcji biblioteki CRT. Kod może również używać tych funkcji do obsługi domyślnej lub dostosowywalnej obsługi nieprawidłowych parametrów.

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
Ciąg reprezentujący nieprawidłowe wyrażenie parametru kodu źródłowego.

*function_name*<br/>
Nazwa funkcji, która wywołała procedurę obsługi.

*nazwa_pliku*<br/>
Plik kodu źródłowego, w którym została wywołana procedura obsługi.

*line_number*<br/>
Numer wiersza w kodzie źródłowym, w którym została wywołana procedura obsługi.

*rezerwacj*<br/>
Przestrzeń.

## <a name="return-value"></a>Wartość zwracana

Te funkcje nie zwracają wartości. Funkcje **_invalid_parameter_noinfo_noreturn** i **_invoke_watson** nie zwracają do obiektu wywołującego, a w niektórych przypadkach **_invalid_parameter** i **_invalid_parameter_noinfo** mogą nie zwracać do obiektu wywołującego.

## <a name="remarks"></a>Uwagi

Gdy funkcje biblioteki środowiska uruchomieniowego języka C przechodzą nieprawidłowe parametry, funkcje biblioteki wywołują *procedurę obsługi nieprawidłowego parametru*, czyli funkcję, która może być określona przez programistę, aby wykonać dowolną z kilku rzeczy. Na przykład może zgłosić problem do użytkownika, zapis do dziennika, przerwanie w debugerze, zakończenie działania programu lub nic nie robić. Jeśli funkcja nie zostanie określona przez programistę, wywoływana jest domyślna procedura obsługi **_invoke_watson**.

Domyślnie po zidentyfikowaniu nieprawidłowego parametru w kodzie debugowania funkcje biblioteki CRT wywołują funkcję **_invalid_parameter** przy użyciu parametrów pełnych. W kodzie niedebugowanym wywoływana jest funkcja **_invalid_parameter_noinfo** , która wywołuje funkcję **_invalid_parameter** przy użyciu pustych parametrów. Jeśli funkcja biblioteki CRT niedebugowania wymaga zakończenia programu, wywoływana jest funkcja **_invalid_parameter_noinfo_noreturn** , która wywołuje funkcję **_invalid_parameter** przy użyciu pustych parametrów, a następnie wywołanie **_invoke_** funkcja programu Watson wymusić zakończenie działania programu.

Funkcja **_invalid_parameter** sprawdza, czy ustawiono zdefiniowaną przez użytkownika procedurę obsługi nieprawidłowego parametru i jeśli tak, wywoła ją. Na przykład jeśli zdefiniowana przez użytkownika procedura obsługi oparta na wątku została ustawiona przez wywołanie [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) w bieżącym wątku, jest wywoływana, a następnie funkcja zwraca wartość. W przeciwnym razie, jeśli zdefiniowana przez użytkownika procedura obsługi nieprawidłowego parametru została ustawiona przez wywołanie [set_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md), jest wywoływana, a następnie funkcja zwraca wartość. W przeciwnym razie zostanie wywołana domyślna procedura obsługi **_invoke_watson** . Domyślnym zachowaniem **_invoke_watson** jest zakończenie tego programu. Programy obsługi zdefiniowane przez użytkownika mogą kończyć się lub zwracać. Zalecamy, aby programy obsługi zdefiniowane przez użytkownika przerywali działanie, chyba że odzyskiwanie jest określone.

Gdy zostanie wywołana domyślna procedura obsługi **_invoke_watson** , jeśli procesor obsługuje operację [__fastfail](../../intrinsics/fastfail.md) , jest wywoływany przy użyciu parametru **FAST_FAIL_INVALID_ARG** , a proces kończy się. W przeciwnym razie zostanie zgłoszony wyjątek szybkiego błędu, który może zostać przechwycony przez dołączony debuger. Jeśli proces może być kontynuowany, zostaje zakończony przez wywołanie funkcji **TerminateProcess** systemu Windows przy użyciu stanu kodu wyjątku **STATUS_INVALID_CRUNTIME_PARAMETER**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|------------------|
|**_invalid_parameter**, **_invalid_parameter_noinfo**, **_invalid_parameter_noinfo_noreturn**, **_invoke_watson**|\<corecrt.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Walidacja parametru](../../c-runtime-library/parameter-validation.md)<br/>
