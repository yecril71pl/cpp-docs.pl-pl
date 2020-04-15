---
title: _seh_filter_dll, _seh_filter_exe
ms.date: 4/2/2020
api_name:
- _XcptFilter
- _seh_filter_dll
- _seh_filter_exe
- _o__seh_filter_dll
- _o__seh_filter_exe
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
- XcptFilter
- _XcptFilter
- _seh_filter_dll
- _seh_filter_exe
- corecrt_startup/_seh_filter_exe
- corecrt_startup/_seh_filter_dll
helpviewer_keywords:
- XcptFilter function
- _XcptFilter function
- _seh_filter_dll function
- _seh_filter_exe function
ms.assetid: 747e5963-3a12-4bf5-b5c4-d4c1b6068e15
ms.openlocfilehash: bf92ea52c2614eb133bcd1ec820a386d1f38e8f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337956"
---
# <a name="_seh_filter_dll-_seh_filter_exe"></a>_seh_filter_dll, _seh_filter_exe

Określa wyjątek i powiązane działania, które należy podjąć.

## <a name="syntax"></a>Składnia

```C
int __cdecl _seh_filter_dll(
   unsigned long _ExceptionNum,
   struct _EXCEPTION_POINTERS* _ExceptionPtr
);
int __cdecl _seh_filter_exe(
   unsigned long _ExceptionNum,
   struct _EXCEPTION_POINTERS* _ExceptionPtr
);
```

### <a name="parameters"></a>Parametry

*_ExceptionNum*<br/>
Identyfikator wyjątku.

*_ExceptionPtr*<br/>
Wskaźnik do informacji o wyjątku.

## <a name="return-value"></a>Wartość zwracana

Liczba całkowita, która wskazuje akcję, która ma zostać podjęta, na podstawie wyniku przetwarzania wyjątków.

## <a name="remarks"></a>Uwagi

Te metody są wywoływane przez wyrażenie filtr wyjątku [try-except Instrukcji](../../cpp/try-except-statement.md). Metoda konsultuje się ze stałą tabelą wewnętrzną w celu zidentyfikowania wyjątku i określenia odpowiedniej akcji, jak pokazano poniżej. Numery wyjątków są zdefiniowane w winnt.h, a numery sygnałów są zdefiniowane w signal.h.

|Numer wyjątku (niepodpisany długi)|Numer sygnału|
|----------------------------------------|-------------------|
|STATUS_ACCESS_VIOLATION|SIGSEGV ( SIGSEGV )|
|STATUS_ILLEGAL_INSTRUCTION|SIGILL ( SIGILL )|
|STATUS_PRIVILEGED_INSTRUCTION|SIGILL ( SIGILL )|
|STATUS_FLOAT_DENORMAL_OPERAND|SIGFPE ( SIGFPE )|
|STATUS_FLOAT_DIVIDE_BY_ZERO|SIGFPE ( SIGFPE )|
|STATUS_FLOAT_INEXACT_RESULT|SIGFPE ( SIGFPE )|
|STATUS_FLOAT_INVALID_OPERATION|SIGFPE ( SIGFPE )|
|STATUS_FLOAT_OVERFLOW|SIGFPE ( SIGFPE )|
|STATUS_FLOAT_STACK_CHECK|SIGFPE ( SIGFPE )|
|STATUS_FLOAT_UNDERFLOW|SIGFPE ( SIGFPE )|

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** corecrt_startup.h

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
