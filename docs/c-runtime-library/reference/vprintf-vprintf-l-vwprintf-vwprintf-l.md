---
title: vprintf, _vprintf_l, vwprintf, _vwprintf_l
ms.date: 11/04/2016
apiname:
- vprintf
- _vwprintf_l
- _vprintf_l
- vwprintf
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
apitype: DLLExport
f1_keywords:
- vwprintf
- _vtprintf
helpviewer_keywords:
- vwprintf function
- _vwprintf_l function
- vwprintf_l function
- _vtprintf function
- vtprintf_l function
- vprintf function
- _vprintf_l function
- vprintf_l function
- vtprintf function
- _vtprintf_l function
- formatted text [C++]
ms.assetid: 44549505-00a0-4fa7-9a85-f2e666f55a38
ms.openlocfilehash: db984b822e8b496d63bf7844882676581562930d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499135"
---
# <a name="vprintf-_vprintf_l-vwprintf-_vwprintf_l"></a>vprintf, _vprintf_l, vwprintf, _vwprintf_l

Zapisuje sformatowane dane wyjściowe przy użyciu wskaźnika do listy argumentów. Bardziej bezpieczne wersje tych funkcji są dostępne, zobacz [vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l](vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md).

## <a name="syntax"></a>Składnia

```C
int vprintf(
   const char *format,
   va_list argptr
);
int _vprintf_l(
   const char *format,
   locale_t locale,
   va_list argptr
);
int vwprintf(
   const wchar_t *format,
   va_list argptr
);
int _vwprintf_l(
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>Parametry

*format*<br/>
Specyfikacja formatu.

*argptr*<br/>
Wskaźnik na listę argumentów.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

Aby uzyskać więcej informacji, zobacz temat [Formatowanie specyfikacji](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Wartość zwracana

**vprintf —** i **vwprintf** zwracają liczbę znaków, bez uwzględnienia kończącego znaku null, lub wartość ujemną, jeśli wystąpi błąd danych wyjściowych. Jeśli *Format* jest wskaźnikiem typu null lub jeśli ciąg formatu zawiera nieprawidłowe znaki formatowania, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcje zwracają wartość-1 i ustawiają **errno** na **EINVAL**.

Aby uzyskać informacje o tych i innych kodach błędów, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda z tych funkcji Pobiera wskaźnik do listy argumentów, a następnie formatuje i zapisuje dane w strumieniu **stdout**.

**vwprintf** to dwubajtowa wersja **vprintf —** ; dwie funkcje zachowują się identycznie, jeśli strumień jest otwarty w trybie ANSI. **vprintf —** obecnie nie obsługuje danych wyjściowych w strumieniu Unicode.

Wersje tych funkcji z sufiksem **_l** są identyczne, z tą różnicą, że korzystają z przekazaną parametrem ustawień regionalnych zamiast bieżących ustawień regionalnych wątku.

> [!IMPORTANT]
> Upewnij się, że *Format* nie jest ciągiem zdefiniowanym przez użytkownika. Aby uzyskać więcej informacji, zobacz Unikanie przekroczeń [buforu](/windows/win32/SecBP/avoiding-buffer-overruns). Należy zauważyć, że wykryto nieprawidłowe ciągi formatu i spowoduje to wystąpienie błędu.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtprintf**|**vprintf**|**vprintf**|**vwprintf**|
|**_vtprintf_l**|**_vprintf_l**|**_vprintf_l**|**_vwprintf_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**vprintf —** , **_vprintf_l**|\<stdio. h > i \<STDARG. h >|\<varargs.h>*|
|**vwprintf**, **_vwprintf_l**|\<stdio. h > lub \<WCHAR. h > i \<STDARG. h >|\<varargs.h>*|

\*Wymagane w przypadku zgodności z systemem UNIX V.

Konsola nie jest obsługiwana w aplikacjach platforma uniwersalna systemu Windows (platformy UWP). Standardowe uchwyty strumienia, które są skojarzone z konsolą, **stdin**, **stdout**i **stderr**, muszą zostać przekierowane przed użyciem funkcji języka C w aplikacjach platformy UWP. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf, funkcje](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
