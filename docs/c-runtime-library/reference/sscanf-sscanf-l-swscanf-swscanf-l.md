---
title: sscanf, _sscanf_l, swscanf, _swscanf_l
ms.date: 11/04/2016
apiname:
- swscanf
- sscanf
- _sscanf_l
- _swscanf_l
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
- _sscanf_l
- _stscanf
- swscanf
- _stscanf_l
- sscanf
- _swscanf_l
helpviewer_keywords:
- swscanf function
- _stscanf function
- sscanf function
- _stscanf_l function
- _sscanf_l function
- _swscanf_l function
- swscanf_l function
- strings [C++], reading data from
- stscanf function
- reading data, strings
- strings [C++], reading
- sscanf_l function
- stscanf_l function
ms.assetid: c2dcf0d2-9798-499f-a4a8-06f7e2b9a80c
ms.openlocfilehash: 60dbb8e89e531c3020c243d998a69370095424e5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661971"
---
# <a name="sscanf-sscanfl-swscanf-swscanfl"></a>sscanf, _sscanf_l, swscanf, _swscanf_l

Odczyt sformatowanych danych z ciągu. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [sscanf_s —, _sscanf_s_l —, swscanf_s —, _swscanf_s_l —](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md).

## <a name="syntax"></a>Składnia

```C
int sscanf(
   const char *buffer,
   const char *format [,
   argument ] ...
);
int _sscanf_l(
   const char *buffer,
   const char *format,
   locale_t locale [,
   argument ] ...
);
int swscanf(
   const wchar_t *buffer,
   const wchar_t *format [,
   argument ] ...
);
int _swscanf_l(
   const wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument ] ...
);
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Przechowywane dane

*Format*<br/>
Ciąg kontroli formatu. Aby uzyskać więcej informacji, zobacz [specyfikacji formatu](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*Argument*<br/>
Argumenty opcjonalne.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca liczbę pól pomyślnie przekonwertowanych i przypisanych; zwracana wartość nie uwzględnia pól, które zostały odczytane, ale nie przypisane. Zwracana wartość wynosząca 0 wskazuje, że nie przydzielono żadnych pól. Wartość zwracana jest **EOF** dla błędu lub w przypadku osiągnięcia końca ciągu przed dokonaniem pierwszej konwersji.

Jeśli *buforu* lub *format* jest **NULL** wskaźnika, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość -1 i ustaw **errno** do **EINVAL**.

Aby uzyskać informacje na temat tych i innych kodów błędu, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**Sscanf —** funkcja odczytuje dane z *buforu* w lokalizacji określonej przez każdą *argument*. Każdy *argument* musi być wskaźnikiem do zmiennej typu odpowiadającego specyfikatorowi typu w parametrze *format*. *Format* formantów argument interpretacji danych wejściowych pola i ma taką samą formę i funkcjonuje jako *format* argument dla **scanf** funkcji. Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.

> [!IMPORTANT]
> Podczas odczytywania ciągu za pomocą **sscanf —**, należy zawsze określać szerokość dla **%s** formacie (na przykład **"% 32s"** zamiast **"%s"**); w przeciwnym razie , nieprawidłowo sformatowane dane wejściowe mogą łatwo spowodować przepełnienie buforu.

**swscanf —** to wersja znaku dwubajtowego **sscanf —**; argumenty **swscanf —** są ciągami znaków dwubajtowych. **sscanf —** nie obsługuje wielobajtowych znaków szesnastkowych. **swscanf —** nie obsługuje znaków "strefa zgodności" ani szesnastkowych pełnej szerokości Unicode. W przeciwnym razie **swscanf —** i **sscanf —** zachowują się identycznie.

Wersje tych funkcji **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych wątku.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stscanf —**|**sscanf**|**sscanf**|**swscanf**|
|**_stscanf_l —**|**_sscanf_l**|**_sscanf_l**|**_swscanf_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**sscanf —**, **_sscanf_l —**|\<stdio.h>|
|**swscanf —**, **_swscanf_l —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_sscanf.c
// compile with: /W3
// This program uses sscanf to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>

int main( void )
{
   char  tokenstring[] = "15 12 14...";
   char  s[81];
   char  c;
   int   i;
   float fp;

   // Input various data from tokenstring:
   // max 80 character string:
   sscanf( tokenstring, "%80s", s ); // C4996
   sscanf( tokenstring, "%c", &c );  // C4996
   sscanf( tokenstring, "%d", &i );  // C4996
   sscanf( tokenstring, "%f", &fp ); // C4996
   // Note: sscanf is deprecated; consider using sscanf_s instead

   // Output the data read
   printf( "String    = %s\n", s );
   printf( "Character = %c\n", c );
   printf( "Integer:  = %d\n", i );
   printf( "Real:     = %f\n", fp );
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
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)<br/>
