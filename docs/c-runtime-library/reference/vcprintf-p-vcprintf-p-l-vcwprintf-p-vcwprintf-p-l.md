---
title: _vcprintf_p, _vcprintf_p_l, _vcwprintf_p, _vcwprintf_p_l
ms.date: 11/04/2016
apiname:
- _vcprintf_p
- _vcwprintf_p_l
- _vcprintf_p_l
- _vcwprintf_p
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
- vcwprintf_p
- vcprintf_p_l
- _vcprintf_p
- _vcprintf_p_l
- vcwprintf_p_l
- vcprintf_p
- _vcwprintf_p
- _vcwprintf_p_l
helpviewer_keywords:
- _vtcprintf_p_l function
- vcprintf_p_l function
- _vcprintf_p_l function
- vtcprintf_p_l function
- vcprintf_p function
- _vcwprintf_p function
- _vcprintf_p function
- vcwprintf_p function
- vcwprintf_p_l function
- vtcprintf_p function
- _vcwprintf_p_l function
- _vtcprintf_p function
ms.assetid: 611024cc-90e7-41db-8e85-145ca95012b1
ms.openlocfilehash: 4d2346237181299b3497fade37827a3abc5e7749
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499365"
---
# <a name="_vcprintf_p-_vcprintf_p_l-_vcwprintf_p-_vcwprintf_p_l"></a>_vcprintf_p, _vcprintf_p_l, _vcwprintf_p, _vcwprintf_p_l

Zapisuje sformatowane dane wyjściowe do konsoli za pomocą wskaźnika do listy argumentów i obsługuje parametry pozycyjne w ciągu formatu.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _vcprintf_p(
   const char* format,
   va_list argptr
);
int _vcprintf_p_l(
   const char* format,
   locale_t locale,
   va_list argptr
);
int _vcwprintf_p(
   const wchar_t* format,
   va_list argptr
);
int _vcwprintf_p_l(
   const wchar_t* format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>Parametry

*format*<br/>
Specyfikacja formatu.

*argptr*<br/>
Wskaźnik do listy argumentów.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

Aby uzyskać więcej informacji, zobacz [składnia specyfikacji formatowania: printf i wprintf Functions](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Wartość zwracana

Liczba znaków, które są zapisywane lub wartość ujemna, jeśli wystąpi błąd danych wyjściowych. Jeśli *Format* jest pustym wskaźnikiem, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** i-1 jest zwracany.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji Pobiera wskaźnik do listy argumentów, a następnie używa funkcji **_putch** do formatowania i zapisywania danych w konsoli. ( **_vcwprintf_p** używa **_putwch** zamiast **_putch**. **_vcwprintf_p** to dwubajtowa wersja **_vcprintf_p**. Ciąg znaków dwubajtowych przyjmuje wartość argumentu.

Wersje tych funkcji, które mają sufiks **_l** są identyczne, z tą różnicą, że korzystają z parametru ustawień regionalnych, który został przesłany zamiast bieżących ustawień regionalnych.

Każdy *argument* (jeśli istnieje) jest konwertowany i jest wyprowadzany zgodnie z odpowiadającą specyfikacją formatu w *formacie*. Specyfikacja formatu obsługuje parametry pozycyjne, aby można było określić kolejność, w której argumenty są używane w ciągu formatu. Aby uzyskać więcej informacji, zobacz [Printf_p parametry pozycyjne](../../c-runtime-library/printf-p-positional-parameters.md).

Te funkcje nie tłumaczą znaków wysuwu wiersza w kombinacje wysuwu wiersza (CR-LF), gdy są one wyjściowe.

> [!IMPORTANT]
> Upewnij się, że *Format* nie jest ciągiem zdefiniowanym przez użytkownika. Aby uzyskać więcej informacji, zobacz Unikanie przekroczeń [buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

Te funkcje weryfikują wskaźnik wejściowy i ciąg formatu. Jeśli *Format* lub *argument* ma **wartość null**lub jeśli ciąg formatu zawiera nieprawidłowe znaki formatowania, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość-1 i ustawiają **errno** na **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_vtcprintf_p**|**_vcprintf_p**|**_vcprintf_p**|**_vcwprintf_p**|
|**_vtcprintf_p_l**|**_vcprintf_p_l**|**_vcprintf_p_l**|**_vcwprintf_p_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_vcprintf_p**, **_vcprintf_p_l**|\<CONIO. h > i \<STDARG. h >|
|**_vcwprintf_p**, **_vcwprintf_p_l**|\<CONIO. h > i \<STDARG. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_vcprintf_p.c
// compile with: /c
#include <conio.h>
#include <stdarg.h>

// An error formatting function that's used to print to the console.
int eprintf(const char* format, ...)
{
   va_list args;
   va_start(args, format);
   int result = _vcprintf_p(format, args);
   va_end(args);
   return result;
}

int main()
{
   int n = eprintf("parameter 2 = %2$d; parameter 1 = %1$s\r\n",
      "one", 222);
   _cprintf_s("%d characters printed\r\n");
}
```

```Output
parameter 2 = 222; parameter 1 = one
38 characters printed
```

## <a name="see-also"></a>Zobacz także

[We/wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
[printf_p Parametry pozycyjne](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
