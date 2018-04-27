---
title: _get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _get_thread_local_invalid_parameter_handler function
- _get_invalid_parameter_handler function
ms.assetid: a176da0e-38ca-4d99-92bb-b0e2b8072f53
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9a3e4df593e027c77909f6d3d1ea7c7a106799a9
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="getinvalidparameterhandler-getthreadlocalinvalidparameterhandler"></a>_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler

Pobiera funkcję, która jest wywoływana, gdy CRT wykryje nieprawidłowy argument.

## <a name="syntax"></a>Składnia

```C
_invalid_parameter_handler _get_invalid_parameter_handler(void);
_invalid_parameter_handler _get_thread_local_invalid_parameter_handler(void);
```

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do aktualnie ustawione funkcji obsługi nieprawidłowy parametr lub pustego wskaźnika, jeżeli brak nie ustawiono.

## <a name="remarks"></a>Uwagi

**_Get_invalid_parameter_handler** funkcja pobiera aktualnie ustawione program obsługi nieprawidłowych parametrów globalnych. Zwraca wskaźnika o wartości null, jeśli ustawiono bez obsługi globalne nieprawidłowy parametr. Podobnie **_get_thread_local_invalid_parameter_handler** pobiera bieżący obsługi lokalnej wątku nieprawidłowy parametr w wątku jest wywoływana w lub wskaźnika o wartości null, jeśli ustawiono bez obsługi. Informacje dotyczące sposobu konfigurowania obsługi globalne i lokalne wątku nieprawidłowy parametr, zobacz [_set_invalid_parameter_handler —, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

Wskaźnik funkcji obsługi zwrócony nieprawidłowy parametr ma następującego typu:

```C
typedef void (__cdecl* _invalid_parameter_handler)(
    wchar_t const*,
    wchar_t const*,
    wchar_t const*,
    unsigned int,
    uintptr_t
    );
```

Aby uzyskać szczegółowe informacje na program obsługi nieprawidłowych parametrów, zobacz prototyp [_set_invalid_parameter_handler —, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_invalid_parameter_handler**, **_get_thread_local_invalid_parameter_handler**|C: \<stdlib.h><br /><br /> C++: \<cstdlib — > lub \<stdlib.h >|

**_Get_invalid_parameter_handler** i **_get_thread_local_invalid_parameter_handler** funkcje są określone firmy Microsoft. Aby uzyskać informacje dotyczące zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Wersje funkcji CRT z rozszerzonymi zabezpieczeniami](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
