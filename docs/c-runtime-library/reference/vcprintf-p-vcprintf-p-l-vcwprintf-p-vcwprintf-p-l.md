---
title: _vcprintf_p, _vcprintf_p_l, _vcwprintf_p, _vcwprintf_p_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03251c9f0442ffa3cda6b00b6528e424e1fe9007
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415637"
---
# <a name="vcprintfp-vcprintfpl-vcwprintfp-vcwprintfpl"></a>_vcprintf_p, _vcprintf_p_l, _vcwprintf_p, _vcwprintf_p_l

Zapisuje sformatowane dane wyjściowe do konsoli za pomocą wskaźnika do listy argumentów i obsługuje parametrów pozycyjnych w ciągu formatu.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Format*<br/>
Definicja formatu.

*argptr*<br/>
Wskaźnik do listy argumentów.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

Aby uzyskać więcej informacji, zobacz [składnia specyfikacji formatu: funkcje printf i wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Wartość zwracana

Liczba znaków, które są zapisywane lub wartość ujemną, jeśli wystąpi błąd danych wyjściowych. Jeśli *format* wskaźnika o wartości null, jest program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i jest zwracana wartość -1.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji przyjmuje wskaźnik do listy argumentów, a następnie używa **_putch —** funkcja sformatowanie i zapisać podanych danych do konsoli. (**_vcwprintf_p —** używa **_putwch —** zamiast **_putch —**. **_vcwprintf_p —** jest wersja znaków dwubajtowych **_vcprintf_p —**. Trwa ciąg znaków dwubajtowych jako argument.)

Wersje tych funkcji, które mają **_l** sufiks są identyczne z tym, że parametr ustawień regionalnych, który jest przekazywany w ich użyć zamiast bieżących ustawień regionalnych.

Każdy *argument* (jeśli istnieje) jest konwertowany i dane wyjściowe według specyfikacji formatu w *format*. Specyfikacji formatu obsługuje parametrów pozycyjnych, dzięki czemu można określić kolejność, w którym argumenty są używane w ciągu formatu. Aby uzyskać więcej informacji, zobacz [printf_p parametry pozycyjne](../../c-runtime-library/printf-p-positional-parameters.md).

Te funkcje nie przetłumaczenie znaki wysuwu wiersza kombinacji powrotu wiersza kanału informacyjnego (CR LF) karetki po danych wyjściowych.

> [!IMPORTANT]
> Upewnij się, że *format* nie jest ciągiem zdefiniowane przez użytkownika. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).

Te funkcje sprawdzania poprawności wskaźnika wejścia i ciąg formatu. Jeśli *format* lub *argument* jest **NULL**, lub jeśli ciąg formatu zawiera nieprawidłowe znaki formatowania, te funkcje wywołanie program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli wykonanie może kontynuować, następujące funkcje i ustaw **errno** do **einval —**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_vtcprintf_p —**|**_vcprintf_p**|**_vcprintf_p**|**_vcwprintf_p**|
|**_vtcprintf_p_l —**|**_vcprintf_p_l**|**_vcprintf_p_l**|**_vcwprintf_p_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_vcprintf_p —**, **_vcprintf_p_l —**|\<conio.h > i \<stdarg.h >|
|**_vcwprintf_p —**, **_vcwprintf_p_l —**|\<conio.h > i \<stdarg.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

[We/Wy konsoli i portu](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
[printf_p Parametry pozycyjne](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
