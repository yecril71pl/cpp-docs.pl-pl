---
title: vsscanf —, vswscanf — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- vsscanf
- vswscanf
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
- _vstscanf
- vsscanf
- vswscanf
dev_langs:
- C++
helpviewer_keywords:
- vswscanf function
- vsscanf function
ms.assetid: e96180f2-df46-423d-b4eb-0a49ab819bde
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7267e308f8b75a0e040e3fe33d51a9bdeea3914f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415894"
---
# <a name="vsscanf-vswscanf"></a>vsscanf, vswscanf

Odczyty sformatowane dane z ciągu. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [vsscanf_s, vswscanf_s](vsscanf-s-vswscanf-s.md).

## <a name="syntax"></a>Składnia

```C
int vsscanf(
   const char *buffer,
   const char *format,
   va_list arglist
);
int vswscanf(
   const wchar_t *buffer,
   const wchar_t *format,
   va_list arglist
);
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Przechowywanych danych

*Format*<br/>
Ciąg kontroli formatu. Aby uzyskać więcej informacji, zobacz [pola specyfikacji formatu: funkcji wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*arglist*<br/>
Listy zmiennych argumentów.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca liczbę pól, które pomyślnie przekonwertowany i przypisane; wartość zwrotna nie zawiera pola, które zostały do odczytu, ale nie są przypisane. Wartość zwracana 0 wskazuje, że nie ma pól zostały przypisane. Wartość zwracana jest **EOF** błędu lub po osiągnięciu końca ciągu przed pierwszym konwersji.

Jeśli *buforu* lub *format* jest **NULL** wskaźnika, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli wykonanie może kontynuować, następujące funkcje i ustaw **errno** do **einval —**.

Aby uzyskać informacje na temat tych i innych kodów błędów, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**Vsscanf —** funkcja odczytywać dane z *buforu* w lokalizacjach, które są podane przez każdy argument *lista_argumentów* listy argumentów. Każdy argument na liście musi być wskaźnik do zmiennej, która ma typ, który odpowiada specyfikatorowi typu w *format*. *Format* formanty argument interpretacji dane wejściowe pola i ma tę samą tworzą i działać jako *format* argument dla **scanf** funkcji. Jeśli kopiowanie odbywa się między ciągów, które nakładają się na, zachowanie jest niezdefiniowany.

> [!IMPORTANT]
> Jeśli używasz **vsscanf —** odczytać ciągu, należy zawsze określić szerokość **%s** formacie (na przykład **"% 32s"** zamiast **"%s"**); w przeciwnym razie niepoprawnie sformatowany danych wejściowych może spowodować przepełnienie buforu.

**vswscanf —** jest wersja znaków dwubajtowych **vsscanf —**; argumenty **vswscanf —** są ciągami znaków dwubajtowych. **vsscanf —** nie obsługuje wielobajtowe znaków szesnastkowych. **vswscanf —** nie obsługuje szesnastkowych pełnej szerokości Unicode lub znaków "strefy zgodności". W przeciwnym razie **vswscanf —** i **vsscanf —** zachowują się tak samo.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vstscanf**|**vsscanf —**|**vsscanf —**|**vswscanf —**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**vsscanf —**|\<stdio.h>|
|**vswscanf —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_vsscanf.c
// compile with: /W3
// This program uses vsscanf to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdarg.h>

int call_vsscanf(char *tokenstring, char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vsscanf(tokenstring, format, arglist);
    va_end(arglist);
    return result;
}

int main( void )
{
    char  tokenstring[] = "15 12 14...";
    char  s[81];
    char  c;
    int   i;
    float fp;

    // Input various data from tokenstring:
    // max 80 character string:
    call_vsscanf(tokenstring, "%80s", s);
    call_vsscanf(tokenstring, "%c", &c);
    call_vsscanf(tokenstring, "%d", &i);
    call_vsscanf(tokenstring, "%f", &fp);

    // Output the data read
    printf("String    = %s\n", s);
    printf("Character = %c\n", c);
    printf("Integer:  = %d\n", i);
    printf("Real:     = %f\n", fp);
}
```

```Output
String    = 15
Character = 1
Integer:  = 15
Real:     = 15.000000
```

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vsscanf_s, vswscanf_s](vsscanf-s-vswscanf-s.md)<br/>
