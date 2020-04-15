---
title: _invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson
ms.date: 4/2/2020
api_name:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
- _o__invalid_parameter_noinfo
- _o__invalid_parameter_noinfo_noreturn
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 0f0a3ea3e1f2e43d53650b4017905c696269ce20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343942"
---
# <a name="_invalid_parameter-_invalid_parameter_noinfo-_invalid_parameter_noinfo_noreturn-_invoke_watson"></a>_invalid_parameter, _invalid_parameter_noinfo, _invalid_parameter_noinfo_noreturn, _invoke_watson

Te funkcje są używane przez bibliotekę środowiska wykonawczego C do obsługi nieprawidłowych parametrów przekazanych do funkcji biblioteki CRT. Kod może również używać tych funkcji do obsługi domyślnej lub konfigurowalnej obsługi nieprawidłowych parametrów.

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

*Wyrażenie*<br/>
Ciąg reprezentujący wyrażenie parametru kodu źródłowego, który jest nieprawidłowy.

*function_name*<br/>
Nazwa funkcji, która wywoływała program obsługi.

*Nazwa_pliku*<br/>
Plik kodu źródłowego, w którym został wywołany program obsługi.

*line_number*<br/>
Numer wiersza w kodzie źródłowym, w którym został wywołany program obsługi.

*Zastrzeżone*<br/>
Nieużywany.

## <a name="return-value"></a>Wartość zwracana

Te funkcje nie zwracają wartości. Funkcje **_invalid_parameter_noinfo_noreturn** i **_invoke_watson** nie zwracają się do wywołującego, a w niektórych przypadkach **_invalid_parameter** i **_invalid_parameter_noinfo** mogą nie powrócić do wywołującego.

## <a name="remarks"></a>Uwagi

Gdy funkcje biblioteki wykonawczej języka C są przekazywane nieprawidłowe parametry, funkcje biblioteki wywołać *nieprawidłowy program obsługi parametrów*, funkcja, która może być określona przez programistę, aby wykonać dowolną z kilku rzeczy. Na przykład może zgłosić problem do użytkownika, napisać do dziennika, przerwać debuger, zakończyć program lub nic nie robić. Jeśli programator nie określi żadnej funkcji, wywoływany jest domyślny program obsługi **_invoke_watson**.

Domyślnie, gdy w kodzie debugowania zidentyfikowano nieprawidłowy parametr, funkcje biblioteki CRT wywołują funkcję **_invalid_parameter** przy użyciu pełnych parametrów. W kodzie nie debugowania wywoływana jest funkcja **_invalid_parameter_noinfo,** która wywołuje funkcję **_invalid_parameter** przy użyciu pustych parametrów. Jeśli funkcja biblioteki CRT nie debugowania wymaga zakończenia programu, wywoływana jest funkcja **_invalid_parameter_noinfo_noreturn,** która wywołuje funkcję **_invalid_parameter** przy użyciu pustych parametrów, po której następuje wywołanie funkcji **_invoke_watson,** aby wymusić zakończenie programu.

Funkcja **_invalid_parameter** sprawdza, czy zdefiniowany przez użytkownika nieprawidłowy program obsługi parametrów został ustawiony, a jeśli tak, wywołuje go. Na przykład jeśli zdefiniowany przez użytkownika program obsługi lokalnego wątku został ustawiony przez wywołanie [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) w bieżącym wątku, jest wywoływana, a następnie zwraca funkcję. W przeciwnym razie jeśli zdefiniowany przez użytkownika globalny nieprawidłowy program obsługi parametrów został ustawiony przez wywołanie [set_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md), jest wywoływana, funkcja zwraca. W przeciwnym razie wywoływana jest domyślna **_invoke_watson** obsługi. Domyślnym zachowaniem **_invoke_watson** jest zakończenie programu. Programy obsługi zdefiniowane przez użytkownika mogą zakończyć lub zwrócić. Zaleca się, aby programy obsługi zdefiniowane przez użytkownika kończyły program, chyba że odzyskiwanie jest pewne.

Gdy wywoływana jest domyślna **_invoke_watson** obsługi, jeśli procesor obsługuje operację [__fastfail,](../../intrinsics/fastfail.md) jest wywoływana przy użyciu parametru **FAST_FAIL_INVALID_ARG** i kończy się proces. W przeciwnym razie wyjątek szybki nie jest wywoływany, który może zostać przechwycony przez dołączonego debugera. Jeśli proces jest dozwolony, jest zakończony wywołaniem **funkcji** Zakończenia przetwarzania systemu Windows przy użyciu stanu kodu wyjątku **STATUS_INVALID_CRUNTIME_PARAMETER**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek|
|--------------|------------------|
|**_invalid_parameter** **, _invalid_parameter_noinfo,** **_invalid_parameter_noinfo_noreturn**, **_invoke_watson**|\<corecrt.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Walidacja parametru](../../c-runtime-library/parameter-validation.md)<br/>
