---
title: _get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler
ms.date: 4/2/2020
api_name:
- _get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- _o__get_invalid_parameter_handler
- _o__get_thread_local_invalid_parameter_handler
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_invalid_parameter_handler
- stdlib/_get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- stdlib/_get_thread_local_invalid_parameter_handler
helpviewer_keywords:
- _get_thread_local_invalid_parameter_handler function
- _get_invalid_parameter_handler function
ms.assetid: a176da0e-38ca-4d99-92bb-b0e2b8072f53
ms.openlocfilehash: 2465852b7bcc0251f218c68df14ff33930ad2378
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345074"
---
# <a name="_get_invalid_parameter_handler-_get_thread_local_invalid_parameter_handler"></a>_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler

Pobiera funkcję, która jest wywoływana, gdy CRT wykrywa nieprawidłowy argument.

## <a name="syntax"></a>Składnia

```C
_invalid_parameter_handler _get_invalid_parameter_handler(void);
_invalid_parameter_handler _get_thread_local_invalid_parameter_handler(void);
```

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do aktualnie ustawionej nieprawidłowej funkcji obsługi parametrów lub wskaźnik zerowy, jeśli nie został ustawiony.

## <a name="remarks"></a>Uwagi

Funkcja **_get_invalid_parameter_handler** pobiera aktualnie ustawioną globalną nieprawidłową obsługę parametrów. Zwraca wskaźnik null, jeśli nie ustawiono nie globalnego nieprawidłowego programu obsługi parametrów. Podobnie **_get_thread_local_invalid_parameter_handler** pobiera bieżący nieprawidłowy program obsługi parametrów nieprawidłowy wątku, który jest wywoływany, lub wskaźnik zerowy, jeśli nie ustawiono obsługi. Aby uzyskać informacje dotyczące ustawiania nieprawidłowych programów obsługi parametrów globalnych i lokalnych w wątku, zobacz [_set_invalid_parameter_handler _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

Zwrócony nieprawidłowy wskaźnik funkcji obsługi parametrów ma następujący typ:

```C
typedef void (__cdecl* _invalid_parameter_handler)(
    wchar_t const*,
    wchar_t const*,
    wchar_t const*,
    unsigned int,
    uintptr_t
    );
```

Aby uzyskać szczegółowe informacje na temat nieprawidłowego programu obsługi parametrów, zobacz prototyp w [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_invalid_parameter_handler** **, _get_thread_local_invalid_parameter_handler**|C: \<> stdlib.h<br /><br /> C++: \<cstdlib> lub \<stdlib.h>|

Funkcje **_get_invalid_parameter_handler** i **_get_thread_local_invalid_parameter_handler** są specyficzne dla firmy Microsoft. Aby uzyskać informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Ulepszone pod względem zabezpieczeń wersje funkcji CRT](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
