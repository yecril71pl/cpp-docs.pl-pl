---
title: vsscanf, vswscanf
ms.date: 11/04/2016
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
helpviewer_keywords:
- vswscanf function
- vsscanf function
ms.assetid: e96180f2-df46-423d-b4eb-0a49ab819bde
ms.openlocfilehash: 5bbe80cd2463c5c5b9b4ea55b8d6574675e42054
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478588"
---
# <a name="vsscanf-vswscanf"></a>vsscanf, vswscanf

Odczyty sformatowanych danych z ciągu. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [vsscanf_s, vswscanf_s](vsscanf-s-vswscanf-s.md).

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

**Vsscanf —** funkcja odczytuje dane z *buforu* do lokalizacji, które są określone przez każdy argument *lista_argumentów* listy argumentów. Każdy argument na liście musi być wskaźnikiem do zmiennej, która ma typ odpowiadający specyfikatorowi typu w parametrze *format*. *Format* formantów argument interpretacji danych wejściowych pola i ma taką samą formę i funkcjonuje jako *format* argument dla **scanf** funkcji. Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.

> [!IMPORTANT]
> Kiedy używasz **vsscanf —** do odczytywania ciągu, należy zawsze określać szerokość dla **%s** formacie (na przykład **"% 32s"** zamiast **"%s"**); w przeciwnym razie niepoprawnie sformatowane dane wejściowe mogą spowodować przepełnienie buforu.

**vswscanf —** to wersja znaku dwubajtowego **vsscanf —**; argumenty **vswscanf —** są ciągami znaków dwubajtowych. **vsscanf —** nie obsługuje wielobajtowych znaków szesnastkowych. **vswscanf —** nie obsługuje znaków "strefa zgodności" ani szesnastkowych pełnej szerokości Unicode. W przeciwnym razie **vswscanf —** i **vsscanf —** zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
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

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vsscanf_s, vswscanf_s](vsscanf-s-vswscanf-s.md)<br/>
