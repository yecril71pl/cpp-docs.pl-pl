---
title: vscanf_s, vwscanf_s
ms.date: 11/04/2016
apiname:
- vscanf_s
- vwscanf_s
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
- _vtscanf_s
- vscanf_s
- vwscanf_s
ms.assetid: 23a1c383-5b01-4887-93ce-534a1e38ed93
ms.openlocfilehash: 90100a5fbc03371a11f437acc12562d9ccf957f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519473"
---
# <a name="vscanfs-vwscanfs"></a>vscanf_s, vwscanf_s

Odczyty sformatowanych danych ze standardowego strumienia wejściowego. Te wersje [vscanf, vwscanf](vscanf-vwscanf.md) mają wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
int vscanf_s(
   const char *format,
   va_list arglist
);
int vwscanf_s(
   const wchar_t *format,
   va_list arglist
);
```

### <a name="parameters"></a>Parametry

*Format*<br/>
Ciąg formantu formatu.

*arglist*<br/>
Lista zmiennych argumentów.

## <a name="return-value"></a>Wartość zwracana

Zwraca liczbę pól pomyślnie przekonwertowanych i przypisanych; zwracana wartość nie uwzględnia pól, które zostały odczytane, ale nie przypisane. Zwracana wartość wynosząca 0 wskazuje, że nie przydzielono żadnych pól. Wartość zwracana jest **EOF** dla błędu, czy znak końca pliku lub koniec ciągu zostanie napotkany w pierwszej próbie odczytania znaku. Jeśli *format* jest **NULL** wskaźnika, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **vscanf_s** i **vwscanf_s** zwracają **EOF** i ustaw **errno** do **EINVAL**.

Aby uzyskać informacje na temat tych i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**Vscanf_s** funkcja odczytuje dane ze standardowego strumienia wejściowego **stdin** i zapisuje je w lokalizacjach, które są określone przez *lista_argumentów* listy argumentów. Każdy argument na liście musi być wskaźnikiem do zmiennej typu odpowiadającego specyfikatorowi typu w parametrze *format*. Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.

**vwscanf_s** to wersja znaku dwubajtowego **vscanf_s**; *format* argument **vwscanf_s** jest ciągiem znaku dwubajtowego. **vwscanf_s** i **vscanf_s** zachowują się identycznie, jeżeli strumień jest otwarty w trybie ANSI. **vscanf_s** nie obsługuje danych wejściowych ze strumienia UNICODE.

W odróżnieniu od **vscanf** i **vwscanf**, **vscanf_s** i **vwscanf_s** wymagają rozmiar buforu, należy określić dla wszystkich parametrów wejściowych typu **c**, **C**, **s**, **S**, lub zestawów kontroli, które są ujęte w ciągów **[]**. Rozmiar buforu w znakach jest przekazywany jako dodatkowy parametr natychmiast po wskaźniku do buforu lub zmiennej. Rozmiar buforu w znakach **wchar_t** ciąg nie jest taki sam jak rozmiar w bajtach.

Rozmiar buforu obejmuje kończącą wartość null. Pole określania szerokości można użyć, aby upewnić się, że token, który jest wczytywany w zmieści się w buforze. Jeśli jest używane nie pole specyfikacji szerokości, a odczyt tokenu jest zbyt duży, aby zmieścić się w buforze, nic nie jest zapisywane do tego buforu.

> [!NOTE]
> *Rozmiar* parametr jest typu **niepodpisane**, a nie **size_t**.

Aby uzyskać więcej informacji, zobacz [scanf — specyfikacje szerokości](../../c-runtime-library/scanf-width-specification.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtscanf_s**|**vscanf_s**|**vscanf_s**|**vwscanf_s**|

Aby uzyskać więcej informacji, zobacz [pola specyfikacji formatu: funkcji wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**vscanf_s**|\<stdio.h>|
|**wscanf_s**|\<stdio.h > lub \<wchar.h >|

Konsola nie jest obsługiwana w aplikacjach platformy uniwersalnej Windows (UWP). Standardowe uchwyty strumienia, które są powiązane z konsolą, **stdin**, **stdout**, i **stderr**, muszą zostać przekierowane zanim funkcje środowiska wykonawczego języka C można ich używać w aplikacjach platformy UWP . Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_vscanf_s.c
// compile with: /W3
// This program uses the vscanf_s and vwscanf_s functions
// to read formatted input.

#include <stdio.h>
#include <stdarg.h>
#include <stdlib.h>

int call_vscanf_s(char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vscanf_s(format, arglist);
    va_end(arglist);
    return result;
}

int call_vwscanf_s(wchar_t *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vwscanf_s(format, arglist);
    va_end(arglist);
    return result;
}

int main( void )
{
    int   i, result;
    float fp;
    char  c, s[81];
    wchar_t wc, ws[81];
    result = call_vscanf_s("%d %f %c %C %s %S", &i, &fp, &c, 1,
                           &wc, 1, s, _countof(s), ws, _countof(ws) );
    printf( "The number of fields input is %d\n", result );
    printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c, wc, s, ws);
    result = call_vwscanf_s(L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,
                            &wc, 1, s, _countof(s), ws, _countof(ws) );
    wprintf( L"The number of fields input is %d\n", result );
    wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp, c, wc, s, ws);
}
```

Gdy ten program został podany w danych wejściowych w przykładzie, produkuje następujące dane wyjściowe:

```Input
71 98.6 h z Byte characters
36 92.3 y n Wide characters
```

```Output
The number of fields input is 6
The contents are: 71 98.599998 h z Byte characters
The number of fields input is 6
The contents are: 36 92.300003 y n Wide characters
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[vscanf, vwscanf](vscanf-vwscanf.md)<br/>
