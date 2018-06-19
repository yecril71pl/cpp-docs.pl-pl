---
title: vscanf_s, vwscanf_s | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 23a1c383-5b01-4887-93ce-534a1e38ed93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c32d1e50f554c32917f9fa0450abba15463386ab
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415650"
---
# <a name="vscanfs-vwscanfs"></a>vscanf_s, vwscanf_s

Odczyty sformatowanych danych z Standardowy strumień wejściowy. Te wersje programu [vscanf, vwscanf](vscanf-vwscanf.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Ciąg formatu w kontroli.

*arglist*<br/>
Listy zmiennych argumentów.

## <a name="return-value"></a>Wartość zwracana

Zwraca liczbę pól pomyślnie przekonwertowany i przypisane; wartość zwrotna nie zawiera pola, które zostały do odczytu, ale nie są przypisane. Wartość zwracana 0 wskazuje, że nie ma pól zostały przypisane. Wartość zwracana jest **EOF** wystąpił błąd, lub jeśli napotkano znak końca pliku lub znak zakończenia ciągu w pierwszej próby odczytu znak. Jeśli *format* jest **NULL** wskaźnika, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **vscanf_s** i **vwscanf_s** zwracać **EOF** i ustaw **errno** do **einval —**.

Aby uzyskać informacje na temat tych i innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**Vscanf_s** funkcja odczytuje dane z Standardowy strumień wejściowy **stdin** i zapisuje dane do lokalizacji, które są podane przez *lista_argumentów* listy argumentów. Każdy argument na liście musi być wskaźnikiem do zmiennej typu, który odpowiada specyfikatorowi typu w *format*. Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.

**vwscanf_s** jest wersja znaków dwubajtowych **vscanf_s**; *format* argument **vwscanf_s** jest ciągiem znaków dwubajtowych. **vwscanf_s** i **vscanf_s** zachowują się tak samo, jakby strumień jest otwarty w trybie ANSI. **vscanf_s** nie obsługuje dane wejściowe ze strumienia UNICODE.

W odróżnieniu od **vscanf** i **vwscanf**, **vscanf_s** i **vwscanf_s** wymagają określenia wszystkich parametrów typu wejściowych rozmiar buforu **c**, **C**, **s**, **S**, lub string zestawów kontroli, które są ujęte w **[]**. Rozmiar buforu w znakach jest przekazywany jako dodatkowy parametr natychmiast po wskaźnik do buforu lub zmiennej. Rozmiar buforu w znakach **wchar_t** ciąg nie jest taka sama jak rozmiar w bajtach.

Rozmiar buforu obejmuje zakończenia wartości null. Specyfikacja szerokości pola służy do zapewnienia, że token, który jest odczytywany w zmieści się w buforze. Jeśli żadne pole Specyfikacja szerokości jest używany, a token odczytu w jest zbyt duży, aby zmieścić się w buforze, nic nie są zapisywane w tym buforu.

> [!NOTE]
> *Rozmiar* parametr jest typu **niepodpisane**, a nie **size_t**.

Aby uzyskać więcej informacji, zobacz [scanf — specyfikacje szerokości](../../c-runtime-library/scanf-width-specification.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtscanf_s**|**vscanf_s**|**vscanf_s**|**vwscanf_s**|

Aby uzyskać więcej informacji, zobacz [pola specyfikacji formatu: funkcji wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**vscanf_s**|\<stdio.h>|
|**wscanf_s**|\<stdio.h > lub \<wchar.h >|

Konsoli nie jest obsługiwane w aplikacjach systemu Windows platformy Uniwersalnej. Uchwyty Standardowy strumień, które są skojarzone z konsoli programu **stdin**, **stdout**, i **stderr**, muszą być przekierowywane przed funkcje wykonawcze języka C można używać ich w aplikacji platformy uniwersalnej systemu Windows . Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

Gdy ten program znajduje się w tym przykładzie dane wejściowe, tworzy te dane wyjściowe:

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
[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[vscanf, vwscanf](vscanf-vwscanf.md)<br/>
