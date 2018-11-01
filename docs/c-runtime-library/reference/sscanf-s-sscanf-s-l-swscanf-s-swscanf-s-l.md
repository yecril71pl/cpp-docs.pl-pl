---
title: sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l
ms.date: 11/04/2016
apiname:
- _sscanf_s_l
- sscanf_s
- _swscanf_s_l
- swscanf_s
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
- _stscanf_s
- sscanf_s
- swscanf_s
- _swscanf_s_l
- _stscanf_s_l
- _sscanf_s_l
helpviewer_keywords:
- stscanf_s_l function
- stscanf_s function
- swscanf_s function
- swscanf_s_l function
- sscanf_s_l function
- _stscanf_s_l function
- strings [C++], reading data from
- sscanf_s function
- _swscanf_s_l function
- _stscanf_s function
- reading data, strings
- strings [C++], reading
- _sscanf_s_l function
ms.assetid: 956e65c8-00a5-43e8-a2f2-0f547ac9e56c
ms.openlocfilehash: b1f535ad8a418fa3ce6492f9bdaa6e0299073504
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538141"
---
# <a name="sscanfs-sscanfsl-swscanfs-swscanfsl"></a>sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l

Odczyty sformatowanych danych z ciągu. Te wersje [sscanf —, _sscanf_l —, swscanf —, _swscanf_l —](sscanf-sscanf-l-swscanf-swscanf-l.md) mają wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
int sscanf_s(
   const char *buffer,
   const char *format [,
   argument ] ...
);
int _sscanf_s_l(
   const char *buffer,
   const char *format,
   locale_t locale [,
   argument ] ...
);
int swscanf_s(
   const wchar_t *buffer,
   const wchar_t *format [,
   argument ] ...
);
int _swscanf_s_l(
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
Ciąg kontroli formatu. Aby uzyskać więcej informacji, zobacz [pola specyfikacji formatu: funkcji wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*Argument*<br/>
Argumenty opcjonalne.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca liczbę pól pomyślnie przekonwertowanych i przypisanych; zwracana wartość nie uwzględnia pól, które zostały odczytane, ale nie przypisane. Zwracana wartość wynosząca 0 wskazuje, że nie przydzielono żadnych pól. Wartość zwracana jest **EOF** dla błędu lub w przypadku osiągnięcia końca ciągu przed dokonaniem pierwszej konwersji.

Jeśli *buforu* lub *format* jest **NULL** wskaźnika, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość -1 i ustaw **errno** do **EINVAL**

Aby uzyskać informacje na temat tych i innych kodów błędu, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**Sscanf_s —** funkcja odczytuje dane z *buforu* w lokalizacji, która została każda *argument*. Argumenty po ciągu formatu określają wskaźniki do zmiennych, które mają typ odpowiadający specyfikatorowi typu w parametrze *format*. W przeciwieństwie do mniej bezpiecznej wersji [sscanf —](sscanf-sscanf-l-swscanf-swscanf-l.md), parametr rozmiaru buforu jest wymagany, gdy używasz znaki pola typu **c**, **C**, **s**, **S**, lub zestawów kontroli, które są ujęte w ciągów **[]**. Rozmiar buforu w znakach musi zostać dostarczony jako dodatkowy parametr natychmiast po każdym parametrze buforu, który go wymaga. Na przykład podczas czytania w ciąg rozmiar buforu dla tego ciągu jest przekazywany w następujący sposób:

```C
wchar_t ws[10];
swscanf_s(in_str, L"%9s", ws, (unsigned)_countof(ws)); // buffer size is 10, width specification is 9
```

Rozmiar buforu obejmuje kończącą wartość null. Pole określania szerokości może służyć do zapewnienia, że token, który jest wczytywany w zmieści się w buforze. Jeśli jest używane nie pole specyfikacji szerokości, a odczyt tokenu jest zbyt duży, aby zmieścić się w buforze, nic nie jest zapisywane do tego buforu.

W przypadku znaków jeden znak może wyglądać następująco:

```C
wchar_t wc;
swscanf_s(in_str, L"%c", &wc, 1);
```

W tym przykładzie odczytuje pojedynczy znak w ciągu wejściowym, a następnie przechowuje je w buforze znaków dwubajtowych. Podczas odczytywania wielu znaków dla ciągów zakończonych wartością inną niż null liczb całkowitych bez znaku są używane jako specyfikacje szerokości i rozmiar buforu.

```C
char c[4];
sscanf_s(input, "%4c", &c, (unsigned)_countof(c)); // not null terminated
```

Aby uzyskać więcej informacji, zobacz [scanf_s, _scanf_s_l —, wscanf_s —, _wscanf_s_l —](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) i [scanf — znaki pola typu](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> Parametr rozmiaru ma typ **niepodpisane**, a nie **size_t**. Podczas kompilowania dla celów 64-bitowych, należy użyć rzutowania statycznego, aby przekonwertować **_countof** lub **sizeof** wyniki do właściwego rozmiaru.

*Format* formantów argument interpretacji danych wejściowych pola i ma taką samą formę i funkcjonuje jako *format* argument **scanf_s** funkcji. Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.

**swscanf_s —** to wersja znaku dwubajtowego **sscanf_s —**; argumenty **swscanf_s —** są ciągami znaków dwubajtowych. **sscanf_s —** nie obsługuje wielobajtowych znaków szesnastkowych. **swscanf_s —** nie obsługuje znaków "strefa zgodności" ani szesnastkowych pełnej szerokości Unicode. W przeciwnym razie **swscanf_s —** i **sscanf_s —** zachowują się identycznie.

Wersje tych funkcji, które mają **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych, który jest przekazywany zamiast bieżących ustawień regionalnych wątku.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stscanf_s —**|**sscanf_s**|**sscanf_s**|**swscanf_s**|
|**_stscanf_s_l —**|**_sscanf_s_l**|**_sscanf_s_l**|**_swscanf_s_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**sscanf_s —**, **_sscanf_s_l —**|\<stdio.h>|
|**swscanf_s —**, **_swscanf_s_l —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_sscanf_s.c
// This program uses sscanf_s to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char  tokenstring[] = "15 12 14...";
   char  s[81];
   char  c;
   int   i;
   float fp;

   // Input various data from tokenstring:
   // max 80 character string plus null terminator
   sscanf_s( tokenstring, "%s", s, (unsigned)_countof(s) );
   sscanf_s( tokenstring, "%c", &c, (unsigned)sizeof(char) );
   sscanf_s( tokenstring, "%d", &i );
   sscanf_s( tokenstring, "%f", &fp );

   // Output the data read
   printf_s( "String    = %s\n", s );
   printf_s( "Character = %c\n", c );
   printf_s( "Integer:  = %d\n", i );
   printf_s( "Real:     = %f\n", fp );
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
