---
title: _get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler
ms.date: 11/04/2016
api_name:
- _get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
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
ms.openlocfilehash: 572d21696d38c47fe0f67d68af5eb249aeb94319
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857811"
---
# <a name="_get_invalid_parameter_handler-_get_thread_local_invalid_parameter_handler"></a>_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler

Pobiera funkcję, która jest wywoływana, gdy CRT wykryje nieprawidłowy argument.

## <a name="syntax"></a>Składnia

```C
_invalid_parameter_handler _get_invalid_parameter_handler(void);
_invalid_parameter_handler _get_thread_local_invalid_parameter_handler(void);
```

## <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obecnie ustawionej nieprawidłowej funkcji obsługi parametrów lub pusty wskaźnik, jeśli żaden nie został ustawiony.

## <a name="remarks"></a>Uwagi

Funkcja **_get_invalid_parameter_handler** Pobiera obecnie ustawioną globalną procedurę obsługi nieprawidłowego parametru. Zwraca wskaźnik o wartości null, jeśli nie ustawiono żadnej procedury obsługi nieprawidłowego parametru. Podobnie **_get_thread_local_invalid_parameter_handler** pobiera bieżącą procedurę obsługi nieprawidłowego parametru wątku, w którym jest on wywoływany, lub pusty wskaźnik, jeśli nie ustawiono żadnej procedury obsługi. Aby uzyskać informacje na temat sposobu ustawiania globalnych i lokalnych procedur obsługi parametrów, zobacz [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

Zwrócony wskaźnik funkcji procedury obsługi nieprawidłowego parametru ma następujący typ:

```C
typedef void (__cdecl* _invalid_parameter_handler)(
    wchar_t const*,
    wchar_t const*,
    wchar_t const*,
    unsigned int,
    uintptr_t
    );
```

Aby uzyskać szczegółowe informacje na temat procedury obsługi nieprawidłowego parametru, zobacz prototyp w [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_invalid_parameter_handler**, **_get_thread_local_invalid_parameter_handler**|C: \<stdlib.h><br /><br /> C++: \<cstdlib > lub \<STDLIB. h >|

**_Get_invalid_parameter_handler** i **_get_thread_local_invalid_parameter_handler** funkcje są specyficzne dla firmy Microsoft. Aby uzyskać informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Wersje funkcji CRT z rozszerzonymi zabezpieczeniami](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
