---
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b0fecd7eefe9ac6a7a479fb12475b2b1c769cf4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405474"
---
# <a name="invalidparameter-invalidparameternoinfo-invalidparameternoinfonoreturn-invokewatson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson

Funkcje te są używane przez biblioteki wykonawczej C do obsługi nieprawidłowych parametrów przekazanych do funkcji CRT biblioteki. Kod może także korzystania z tych funkcji do obsługi domyślne lub dostosować obsługi nieprawidłowych parametrów.

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

*wyrażenie* ciąg reprezentujący wyrażenie parametru kodu źródłowego jest nieprawidłowy.

*nazwa_funkcji* nazwę funkcji, która wywołuje program obsługi.

*nazwa_pliku* pliku źródła kodu, w którym została wywołana przez program obsługi.

*line_number* numer wiersza w kodzie źródłowym, gdy została wywołana przez program obsługi.

*zastrzeżone* węzła nieużywane.

## <a name="return-value"></a>Wartość zwracana

Te funkcje nie zwracają wartość. **_Invalid_parameter_noinfo_noreturn** i **_invoke_watson** nie zwracają do elementu wywołującego, a w niektórych przypadkach **_invalid_parameter** i **_invalid_parameter_noinfo** nie może zwracać do obiektu wywołującego.

## <a name="remarks"></a>Uwagi

Gdy funkcje biblioteki czasu wykonywania języka C przekazano nieprawidłowe parametry, biblioteka funkcji wywołania *program obsługi nieprawidłowych parametrów*, funkcji, która może zostać określona przez programistę wykonywać kilka czynności. Na przykład go może Zgłoś problem do użytkownika, zapisu w dzienniku, przerwanie w debugerze, zakończyć program lub w ogóle nic nie rób. Jeśli funkcja nie jest określona przez programistę domyślny program obsługi **_invoke_watson**, nosi nazwę.

Domyślnie, gdy nie jest prawidłowym parametrem zostanie zidentyfikowana w debugowaniu kodu, funkcje bibliotek CRT wywołanie funkcji **_invalid_parameter** przy użyciu pełnego parametrów. W kodzie bez debugowania **_invalid_parameter_noinfo** funkcja jest wywoływana, które wywołuje **_invalid_parameter** funkcji przy użyciu parametrów puste. Jeśli funkcja biblioteki CRT bez debugowania wymaga zakończenie programu **_invalid_parameter_noinfo_noreturn** funkcja jest wywoływana, które wywołuje **_invalid_parameter** funkcji przy użyciu pustego Parametry, a następnie wywołania **_invoke_watson** funkcji, aby wymusić Kończenie działania programu.

**_Invalid_parameter** funkcji kontroli czy ustawiono obsługi zdefiniowane przez użytkownika nieprawidłowy parametr, a jeśli tak, określa je. Na przykład, jeśli program lokalnej wątku obsługi zdefiniowane przez użytkownika została ustawiona przez wywołanie do [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) w bieżącym wątku jest wywoływana, a następnie zwraca funkcję. W przeciwnym razie, jeśli program obsługi zdefiniowane przez użytkownika globalne nieprawidłowy parametr został ustawiony przez wywołanie do [set_invalid_parameter_handler —](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md), jest ona wywoływana, a następnie zwraca funkcję. W przeciwnym razie domyślny program obsługi **_invoke_watson** jest wywoływana. Domyślne zachowanie **_invoke_watson** jest, aby zakończyć program. Programy obsługi zdefiniowane przez użytkownika może zakończyć lub return. Firma Microsoft zaleca, programy obsługi zdefiniowane przez użytkownika zakończyć program, chyba że odzyskiwanie zostało określone.

Gdy domyślny program obsługi **_invoke_watson** jest wywoływana, gdy procesor obsługuje [__fastfail](../../intrinsics/fastfail.md) operacji jest wywoływana przy użyciu parametru **FAST_FAIL_INVALID_ARG** i kończy proces. W przeciwnym razie wartość niepowodzenie szybkiego Wystąpił wyjątek, które mogą podlegać dołączony debuger. Jeśli proces będzie mógł kontynuować, zostanie zakończony przez wywołanie do systemu Windows **TerminateProcess** funkcji przy użyciu stan kod wyjątku **STATUS_INVALID_CRUNTIME_PARAMETER**.

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
