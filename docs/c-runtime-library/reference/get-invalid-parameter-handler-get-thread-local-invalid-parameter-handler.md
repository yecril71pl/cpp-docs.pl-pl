---
title: _get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler
ms.date: 11/04/2016
apiname:
- _get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
apilocation:
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
apitype: DLLExport
f1_keywords:
- _get_invalid_parameter_handler
- stdlib/_get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- stdlib/_get_thread_local_invalid_parameter_handler
helpviewer_keywords:
- _get_thread_local_invalid_parameter_handler function
- _get_invalid_parameter_handler function
ms.assetid: a176da0e-38ca-4d99-92bb-b0e2b8072f53
ms.openlocfilehash: 7d1a87f9ade0845994918d5a4d59dc56e190d2b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287485"
---
# <a name="getinvalidparameterhandler-getthreadlocalinvalidparameterhandler"></a>_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler

Pobiera funkcja, która jest wywoływana, gdy wykryje CRT, nieprawidłowy argument.

## <a name="syntax"></a>Składnia

```C
_invalid_parameter_handler _get_invalid_parameter_handler(void);
_invalid_parameter_handler _get_thread_local_invalid_parameter_handler(void);
```

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do aktualnie ustawione funkcji obsługi nieprawidłowego parametru lub wskaźnikiem typu null Jeśli nie została ustawiona.

## <a name="remarks"></a>Uwagi

**_Get_invalid_parameter_handler** funkcja pobiera aktualnie ustawione globalne nieprawidłowy parametr uchwytu. Zwraca wskaźnik zerowy, jeśli żadna procedura obsługi globalnej nieprawidłowy parametr został ustawiony. Podobnie **_get_thread_local_invalid_parameter_handler** pobiera bieżącego wątku lokalnego nieprawidłowy parametr uchwytu wątku, jest wywoływana w lub wskaźnikiem typu null, jeśli żadna procedura obsługi nie została ustawiona. Aby uzyskać informacje o sposobie ustawiania globalnych i lokalnych wątków nieprawidłowy parametr obsługi, zobacz [_set_invalid_parameter_handler —, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

Wskaźnik funkcji obsługi zwrócone nieprawidłowy parametr ma następującego typu:

```C
typedef void (__cdecl* _invalid_parameter_handler)(
    wchar_t const*,
    wchar_t const*,
    wchar_t const*,
    unsigned int,
    uintptr_t
    );
```

Szczegółowe informacje dotyczące obsługi nieprawidłowego parametru, zobacz temat prototypu w [_set_invalid_parameter_handler —, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_invalid_parameter_handler**, **_get_thread_local_invalid_parameter_handler**|C: \<stdlib.h><br /><br /> C++: \<cstdlib — > lub \<stdlib.h >|

**_Get_invalid_parameter_handler** i **_get_thread_local_invalid_parameter_handler** funkcje są specyficzne dla firmy Microsoft. Aby uzyskać informacje o zgodności – zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Wersje funkcji CRT z rozszerzonymi zabezpieczeniami](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
