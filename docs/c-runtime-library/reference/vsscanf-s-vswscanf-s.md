---
title: vsscanf_s, vswscanf_s
ms.date: 11/04/2016
apiname:
- vswscanf_s
- vsscanf_s
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
- vsscanf_s
- vswscanf_s
- _vstscanf_s
ms.assetid: 7b732e68-c6f4-4579-8917-122f5a7876e1
ms.openlocfilehash: 3106e3533f5bb65334f8a4f3d38f55d886faef4c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477171"
---
# <a name="vsscanfs-vswscanfs"></a>vsscanf_s, vswscanf_s

Odczyty sformatowanych danych z ciągu. Te wersje [vsscanf —, vswscanf —](vsscanf-vswscanf.md) mają wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*buffer*<br/>
Przechowywane dane

*Format*<br/>
Ciąg kontroli formatu. Aby uzyskać więcej informacji, zobacz [pola specyfikacji formatu: funkcji wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*arglist*<br/>
Lista zmiennych argumentów.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca liczbę pól pomyślnie przekonwertowanych i przypisanych; zwracana wartość nie uwzględnia pól, które zostały odczytane, ale nie przypisane. Zwracana wartość wynosząca 0 wskazuje, że nie przydzielono żadnych pól. Wartość zwracana jest **EOF** dla błędu lub w przypadku osiągnięcia końca ciągu przed dokonaniem pierwszej konwersji.

Jeśli *buforu* lub *format* jest **NULL** wskaźnika, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość -1 i ustaw **errno** do **EINVAL**.

Aby uzyskać informacje na temat tych i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**Vsscanf_s** funkcja odczytuje dane z *buforu* do lokalizacji, które są określone przez każdy argument *lista_argumentów* listy argumentów. Argumenty na liście argumentów określają wskaźniki do zmiennych, które mają typ odpowiadający specyfikatorowi typu w parametrze *format*. W przeciwieństwie do mniej bezpiecznej wersji **vsscanf —**, parametr rozmiaru buforu jest wymagany, gdy używasz znaki pola typu **c**, **C**, **s**, **S**, lub zestawów kontroli ciągów, które są ujęte w **[]**. Rozmiar buforu w znakach musi zostać dostarczony jako dodatkowy parametr natychmiast po każdym parametrze buforu, który go wymaga.

Rozmiar buforu obejmuje kończącą wartość null. Pole określania szerokości może służyć do zapewnienia, że token, który jest wczytywany w zmieści się w buforze. Jeśli jest używane nie pole specyfikacji szerokości, a odczyt tokenu jest zbyt duży, aby zmieścić się w buforze, nic nie jest zapisywane do tego buforu.

Aby uzyskać więcej informacji, zobacz [scanf_s, _scanf_s_l —, wscanf_s —, _wscanf_s_l —](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) i [scanf — znaki pola typu](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Parametr rozmiaru ma typ **niepodpisane**, a nie **size_t**.

*Format* formantów argument interpretacji danych wejściowych pola i ma taką samą formę i funkcjonuje jako *format* argument **scanf_s** funkcji. Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.

**vswscanf_s** to wersja znaku dwubajtowego **vsscanf_s**; argumenty **vswscanf_s** są ciągami znaków dwubajtowych. **vsscanf_s** nie obsługuje wielobajtowych znaków szesnastkowych. **vswscanf_s** nie obsługuje znaków "strefa zgodności" ani szesnastkowych pełnej szerokości Unicode. W przeciwnym razie **vswscanf_s** i **vsscanf_s** zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vstscanf_s**|**vsscanf_s**|**vsscanf_s**|**vswscanf_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**vsscanf_s**|\<stdio.h>|
|**vswscanf_s**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vsscanf, vswscanf](vsscanf-vswscanf.md)<br/>
