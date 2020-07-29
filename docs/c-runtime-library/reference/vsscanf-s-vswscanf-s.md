---
title: vsscanf_s, vswscanf_s
ms.date: 11/04/2016
api_name:
- vswscanf_s
- vsscanf_s
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
- vsscanf_s
- vswscanf_s
- _vstscanf_s
ms.assetid: 7b732e68-c6f4-4579-8917-122f5a7876e1
ms.openlocfilehash: 9150642a6a21198ae43bdea5f33cc5a8f0b6a581
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87189002"
---
# <a name="vsscanf_s-vswscanf_s"></a>vsscanf_s, vswscanf_s

Odczytuje sformatowane dane z ciągu. Te wersje programu [vsscanf vswscanf](vsscanf-vswscanf.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
int vsscanf_s(
   const char *buffer,
   const char *format,
   va_list argptr
);
int vswscanf_s(
   const wchar_t *buffer,
   const wchar_t *format,
   va_list arglist
);
```

### <a name="parameters"></a>Parametry

*buforu*<br/>
Przechowywane dane

*Formatowanie*<br/>
Ciąg kontroli formatu. Aby uzyskać więcej informacji, zobacz [Formatowanie pól specyfikacji: scanf i wscanf Functions](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*arglist*<br/>
Lista argumentów zmiennych.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca liczbę pól, które zostały pomyślnie przekonwertowane i przypisane; wartość zwracana nie zawiera pól, które zostały odczytane, ale nie przypisane. Wartość zwracana przez 0 wskazuje, że nie przypisano żadnych pól. Wartość zwracana to **eof** dla błędu lub, jeśli osiągnięto koniec ciągu przed pierwszą konwersją.

Jeśli *bufor* lub *Format* jest **pustym** wskaźnikiem, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość-1 i ustawiają **errno** na **EINVAL**.

Aby uzyskać informacje o tych i innych kodach błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **vsscanf_s** odczytuje dane z *buforu* do lokalizacji, które są określone przez każdy argument na liście argumentów *arglist* . Argumenty na liście argumentów określają wskaźniki do zmiennych, które mają typ, który odpowiada specyfikatorowi typu w *formacie*. W przeciwieństwie do mniej bezpiecznej wersji **vsscanf**, parametr rozmiaru buforu jest wymagany w przypadku użycia znaków pola typu **c**, **c**, **s**, **s**lub zestawu kontroli ciągów, które są ujęte w **[]**. Rozmiar buforu w znakach musi być podany jako dodatkowy parametr natychmiast po każdym parametrze buforu, który go wymaga.

Rozmiar buforu zawiera kończący wartość null. Pole specyfikacji szerokości może służyć do zapewnienia, że token, który jest odczytywany, będzie pasować do buforu. Jeśli pole specyfikacji szerokości nie jest używane i odczyt tokenu jest zbyt duży, aby zmieścił się w buforze, nic nie jest zapisywane w tym buforze.

Aby uzyskać więcej informacji, zobacz [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) i [pola typu scanf](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Parametr size ma typ, a **`unsigned`** nie **size_t**.

Argument *Format* kontroluje interpretację pól wejściowych i ma taką samą formę i funkcję jak argument *formatu* dla funkcji **scanf_s** . Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.

**vswscanf_s** to dwubajtowa wersja **vsscanf_s**; argumenty do **vswscanf_s** są ciągami znaków dwubajtowych. **vsscanf_s** nie obsługuje wielobajtowych znaków szesnastkowych. **vswscanf_s** nie obsługuje znaków szesnastkowych o pełnej szerokości Unicode lub "strefy zgodności". W przeciwnym razie **vswscanf_s** i **vsscanf_s** zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vstscanf_s**|**vsscanf_s**|**vsscanf_s**|**vswscanf_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**vsscanf_s**|\<stdio.h>|
|**vswscanf_s**|\<stdio.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_vsscanf_s.c
// compile with: /W3
// This program uses vsscanf_s to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdarg.h>
#include <stdlib.h>

int call_vsscanf_s(char *tokenstring, char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vsscanf_s(tokenstring, format, arglist);
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
    call_vsscanf_s(tokenstring, "%80s", s, _countof(s));
    call_vsscanf_s(tokenstring, "%c", &c, sizeof(char));
    call_vsscanf_s(tokenstring, "%d", &i);
    call_vsscanf_s(tokenstring, "%f", &fp);

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
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[sprintf —, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vsscanf, vswscanf](vsscanf-vswscanf.md)<br/>
