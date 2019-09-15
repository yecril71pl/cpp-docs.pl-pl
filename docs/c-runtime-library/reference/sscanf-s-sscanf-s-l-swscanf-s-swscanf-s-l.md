---
title: sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l
ms.date: 11/04/2016
api_name:
- _sscanf_s_l
- sscanf_s
- _swscanf_s_l
- swscanf_s
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 14707b64a9c5c49837391be59d83ee39b79d5065
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957957"
---
# <a name="sscanf_s-_sscanf_s_l-swscanf_s-_swscanf_s_l"></a>sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l

Odczytuje sformatowane dane z ciągu. Te wersje [sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*format*<br/>
Ciąg kontroli formatu. Aby uzyskać więcej informacji, zobacz [Formatowanie pól specyfikacji: scanf i wscanf Functions](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*argument*<br/>
Argumenty opcjonalne

*ustawienie*<br/>
Ustawienia regionalne do użycia

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca liczbę pól, które zostały pomyślnie przekonwertowane i przypisane; wartość zwracana nie zawiera pól, które zostały odczytane, ale nie przypisane. Wartość zwracana przez 0 wskazuje, że nie przypisano żadnych pól. Wartość zwracana to **eof** dla błędu lub, jeśli osiągnięto koniec ciągu przed pierwszą konwersją.

Jeśli *bufor* lub *Format* jest **pustym** wskaźnikiem, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość-1 i ustawiają **errno** na **EINVAL**

Aby uzyskać informacje o tych i innych kodach błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **sscanf_s** odczytuje dane z *buforu* do lokalizacji podanej przez każdy *argument*. Argumenty po ciągu formatu określają wskaźniki do zmiennych, które mają typ, który odpowiada specyfikatorowi typu w *formacie*. W przeciwieństwie do mniej bezpiecznej wersji [sscanf](sscanf-sscanf-l-swscanf-swscanf-l.md), parametr rozmiaru buforu jest wymagany w przypadku używania znaków pola typu **c**, **c**, **s**, **s**lub, które są ujęte w **[]** . Rozmiar buforu w znakach musi być podany jako dodatkowy parametr natychmiast po każdym parametrze buforu, który go wymaga. Na przykład, jeśli odczytujesz do ciągu, rozmiar buforu dla tego ciągu jest przesyłany w następujący sposób:

```C
wchar_t ws[10];
swscanf_s(in_str, L"%9s", ws, (unsigned)_countof(ws)); // buffer size is 10, width specification is 9
```

Rozmiar buforu zawiera kończący wartość null. Pole specyfikacji szerokości może służyć do zapewnienia, że token, który jest odczytywany, będzie pasować do buforu. Jeśli pole specyfikacji szerokości nie jest używane i odczyt tokenu jest zbyt duży, aby zmieścił się w buforze, nic nie jest zapisywane w tym buforze.

W przypadku znaków, pojedynczy znak może zostać odczytany w następujący sposób:

```C
wchar_t wc;
swscanf_s(in_str, L"%c", &wc, 1);
```

Ten przykład odczytuje pojedynczy znak z ciągu wejściowego, a następnie zapisuje go w buforze szerokich znaków. W przypadku odczytywania wielu znaków dla ciągów zakończonych niezerowymi liczbami całkowitymi bez znaku są używane jako Specyfikacja szerokości i rozmiar buforu.

```C
char c[4];
sscanf_s(input, "%4c", &c, (unsigned)_countof(c)); // not null terminated
```

Aby uzyskać więcej informacji, zobacz [znaki pól](../../c-runtime-library/scanf-type-field-characters.md) [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) i scanf.

> [!NOTE]
> Parametr size jest typu **unsigned**, not **size_t**. Podczas kompilowania dla elementów docelowych 64-bitowych Użyj statycznego rzutowania, aby przekonwertować **_countof** lub **sizeof** wyniki do poprawnego rozmiaru.

Argument *Format* kontroluje interpretację pól wejściowych i ma taką samą formę i funkcję jak argument *formatu* dla funkcji **scanf_s** . Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.

**swscanf_s** to dwubajtowa wersja **sscanf_s**; argumenty **swscanf_s** są ciągami znaków dwubajtowych. **sscanf_s** nie obsługuje wielobajtowych znaków szesnastkowych. **swscanf_s** nie obsługuje znaków szesnastkowych o pełnej szerokości Unicode lub "strefy zgodności". W przeciwnym razie **swscanf_s** i **sscanf_s** zachowują się identycznie.

Wersje tych funkcji, które mają sufiks **_l** są identyczne, z tą różnicą, że używają parametru ustawień regionalnych, który został przekazaną, zamiast bieżących ustawień regionalnych wątku.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stscanf_s**|**sscanf_s**|**sscanf_s**|**swscanf_s**|
|**_stscanf_s_l**|**_sscanf_s_l**|**_sscanf_s_l**|**_swscanf_s_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**sscanf_s**, **_sscanf_s_l**|\<stdio.h>|
|**swscanf_s**, **_swscanf_s_l**|\<stdio. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)<br/>
