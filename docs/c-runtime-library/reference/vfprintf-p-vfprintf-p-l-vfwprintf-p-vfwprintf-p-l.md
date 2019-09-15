---
title: _vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l
ms.date: 11/04/2016
api_name:
- _vfprintf_p
- _vfwprintf_p
- _vfprintf_p_l
- _vfwprintf_p_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _vfwprintf_p_l
- _vfprintf_p
- vfwprintf_p_l
- vfwprintf_p
- vfprintf_p_l
- _vfwprintf_p
- _vftprintf_p
- _vfprintf_p_l
- vfprintf_p
helpviewer_keywords:
- vfprintf_p_l function
- _vftprintf_p_l function
- _vfprintf_p function
- vfprintf_p function
- vftprintf_p_l function
- _vfprintf_p_l function
- _vftprintf_p function
- _vfwprintf_p_l function
- vfwprintf_p_l function
- _vfwprintf_p function
- vftprintf_p function
- formatted text [C++]
- vfwprintf_p function
ms.assetid: 4d4a0914-4175-4b65-9ca1-037c4ef29147
ms.openlocfilehash: a98c84ae9cfd221fd23da2eaa08c639e01f12ad4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945561"
---
# <a name="_vfprintf_p-_vfprintf_p_l-_vfwprintf_p-_vfwprintf_p_l"></a>_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l

Zapisz sformatowane dane wyjściowe przy użyciu wskaźnika do listy argumentów, z możliwością określenia kolejności, w której argumenty są używane w ciągu formatu.

## <a name="syntax"></a>Składnia

```C
int _vfprintf_p(
   FILE *stream,
   const char *format,
   va_list argptr
);
int _vfprintf_p_l(
   FILE *stream,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vfwprintf_p(
   FILE *stream,
   const wchar_t *format,
   va_list argptr
);
int _vfwprintf_p_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Wskaźnik do struktury **pliku** .

*format*<br/>
Specyfikacja formatu.

*argptr*<br/>
Wskaźnik na listę argumentów.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

Aby uzyskać więcej informacji, zobacz temat [Formatowanie specyfikacji](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Wartość zwracana

**_vfprintf_p** i **_vfwprintf_p** zwracają liczbę znaków, bez uwzględnienia kończącego znaku null, lub wartość ujemną, jeśli wystąpi błąd danych wyjściowych.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji Pobiera wskaźnik do listy argumentów, a następnie formatuje i zapisuje dane w *strumieniu*. Funkcje te różnią się od wersji **_vfprint_s** i **_vfwprint_s** tylko w przypadku, gdy obsługują parametry pozycyjne. Aby uzyskać więcej informacji, zobacz [Printf_p parametry pozycyjne](../../c-runtime-library/printf-p-positional-parameters.md).

**_vfwprintf_p** to dwubajtowa wersja **_vprintf_p**; dwie funkcje zachowują się identycznie, jeśli strumień jest otwarty w trybie ANSI. **_vprintf_p** obecnie nie obsługuje danych wyjściowych w strumieniu Unicode.

Wersje tych funkcji z sufiksem **_l** są identyczne, z tą różnicą, że korzystają z przekazaną parametrem ustawień regionalnych zamiast bieżących ustawień regionalnych wątku.

> [!IMPORTANT]
> Upewnij się, że *Format* nie jest ciągiem zdefiniowanym przez użytkownika. Aby uzyskać więcej informacji, zobacz [unikanie przekroczeń buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

Jeśli *strumień* lub *Format* jest wskaźnikiem typu null lub jeśli ciąg formatu zawiera nieprawidłowe znaki formatowania, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcje zwracają wartość-1 i ustawiają **errno** na **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vftprintf_p**|**_vfprintf_p**|**_vfprintf_p**|**_vfwprintf_p**|
|**_vftprintf_p_l**|**_vfprintf_p_l**|**_vfprintf_p_l**|**_vfwprintf_p_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**_vfprintf_p**, **_vfprintf_p_l**|\<stdio. h > i \<STDARG. h >|\<varargs.h>*|
|**_vfwprintf_p**, **_vfwprintf_p_l**|\<stdio. h > lub \<WCHAR. h > i \<STDARG. h >|\<varargs.h>*|

\*Wymagane w przypadku zgodności z systemem UNIX V.

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf, funkcje](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
[printf_p Parametry pozycyjne](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
[_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)<br/>
[_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l](sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)<br/>
