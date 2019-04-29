---
title: _seh_filter_dll, _seh_filter_exe
ms.date: 11/04/2016
apiname:
- _XcptFilter
- _seh_filter_dll
- _seh_filter_exe
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
ms.openlocfilehash: 51d6a21b3867eb830a7d9f9b4b9b0ac844cd5aa1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356735"
---
# <a name="sehfilterdll-sehfilterexe"></a>_seh_filter_dll, _seh_filter_exe

Identyfikuje wyjątku i powiązane działania podejmowane.

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
Identyfikator, dla wyjątku.

*_ExceptionPtr*<br/>
Wskaźnik do informacji o wyjątku.

## <a name="return-value"></a>Wartość zwracana

Liczba całkowita, która określa akcję do wykonania, na podstawie wyniku wyjątek podczas przetwarzania.

## <a name="remarks"></a>Uwagi

Te metody są wywoływane przez wyrażenie filtru wyjątków [spróbuj-except, instrukcja](../../cpp/try-except-statement.md). Metoda sprawdza stałej tabeli wewnętrznej do identyfikowania wyjątek i określ odpowiednie działanie, jak pokazano poniżej. Liczby wyjątków są zdefiniowane w pliku winnt.h, i liczby sygnału są zdefiniowane w sygnale.h.

|Liczba wyjątków (unsigned long)|Liczba sygnałów|
|----------------------------------------|-------------------|
|STATUS_ACCESS_VIOLATION|SIGSEGV|
|STATUS_ILLEGAL_INSTRUCTION|SIGILL|
|STATUS_PRIVILEGED_INSTRUCTION|SIGILL|
|STATUS_FLOAT_DENORMAL_OPERAND|SIGFPE|
|STATUS_FLOAT_DIVIDE_BY_ZERO|SIGFPE|
|STATUS_FLOAT_INEXACT_RESULT|SIGFPE|
|STATUS_FLOAT_INVALID_OPERATION|SIGFPE|
|STATUS_FLOAT_OVERFLOW|SIGFPE|
|STATUS_FLOAT_STACK_CHECK|SIGFPE|
|STATUS_FLOAT_UNDERFLOW|SIGFPE|

## <a name="requirements"></a>Wymagania

**Nagłówek:** corecrt_startup.h

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
