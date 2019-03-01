---
title: sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l
ms.date: 11/04/2016
apiname:
- _swprintf_s_l
- _sprintf_s_l
- swprintf_s
- sprintf_s
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- swprintf_s
- sprintf_s
- stdio/sprintf_s
- stdio/swprintf_s
- stdio/_sprintf_s_l
- stdio/_swprintf_s_l
- _sprintf_s_l
- _swprintf_s_l
helpviewer_keywords:
- stprintf_s function
- stprintf_s_l function
- swprintf_s_l function
- sprintf_s function
- swprintf_s function
- _swprintf_s_l function
- sprintf_s_l function
- _stprintf_s_l function
- _stprintf_s function
- _sprintf_s_l function
- formatted text [C++]
ms.assetid: 424f0a29-22ef-40e8-b565-969f5f57782f
ms.openlocfilehash: 4d4bec339caccf9b0843afada4b56b435243dd11
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210890"
---
# <a name="sprintfs-sprintfsl-swprintfs-swprintfsl"></a>sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l

Wpisz sformatowane dane do ciągu. Są to wersje [sprintf, _sprintf_l —, swprintf, _swprintf_l —, \__swprintf_l —](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
int sprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   ...
);
int _sprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   locale_t locale,
   ...
);
int swprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   ...
);
int _swprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   locale_t locale,
   ...
);
template <size_t size>
int sprintf_s(
   char (&buffer)[size],
   const char *format,
   ...
); // C++ only
template <size_t size>
int swprintf_s(
   wchar_t (&buffer)[size],
   const wchar_t *format,
   ...
); // C++ only
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Lokalizacja magazynowa danych wyjściowych

*sizeOfBuffer*<br/>
Maksymalna liczba znaków do zapisania.

*Format*<br/>
Ciąg formantu formatu

*...*<br/>
Argumenty opcjonalne formatowania

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

Aby uzyskać więcej informacji, zobacz [specyfikacji formatu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Wartość zwracana

Liczba znaków zapisanych, lub -1, jeśli wystąpił błąd. Jeśli *buforu* lub *format* jest pustym wskaźnikiem, **sprintf_s —** i **swprintf_s —** zwracają wartość -1 i ustaw **errno**do **EINVAL**.

**sprintf_s —** zwraca liczbę bajtów przechowywanych w *buforu*, nie licząc zamykającego kończącego znaku null. **swprintf_s —** zwraca liczbę znaków szerokich przechowywanych w *buforu*, nie licząc zamykającego znaku pustego.

## <a name="remarks"></a>Uwagi

**Sprintf_s —** funkcja formatuje i przechowuje serie znaków i wartości w *buforu*. Każdy *argument* (jeśli istnieje) jest konwertowaya i wychodzi według specyfikacji formatu w *format*. Format składa się ze znaków zwykłych i ma taką samą formę i funkcjonuje jako *format* argument [printf](printf-printf-l-wprintf-wprintf-l.md). Znak null jest dołączany po ostatnim napisanym znaku. Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.

Jedną z głównych różnic między **sprintf_s —** i [sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) jest fakt, że **sprintf_s —** sprawdza, czy ciąg formatu dla prawidłowych znaków formatowania, natomiast [ sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) sprawdza tylko, jeśli ciąg formatu lub bufor to **NULL** wskaźników. Jeśli sprawdzenie zakończy się niepowodzeniem, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja zwraca wartość -1 i ustawia **errno** do **EINVAL**.

Główna różnica między **sprintf_s —** i [sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) jest fakt, że **sprintf_s —** przyjmuje parametr długości określający rozmiar bufora wyjściowego w znakach. Jeśli bufor jest zbyt mały dla tekstu sformatowanego, w tym kończącą wartość null, a następnie bufor zostaje ustawiony na pusty ciąg, umieszczając znak null w *buforu*[0], a zostanie wywołany nieprawidłowy parametr uchwytu. W odróżnieniu od **_snprintf**, **sprintf_s —** gwarantuje, że bufor będzie zakończony zerem, chyba że rozmiar buforu jest równy zero.

**swprintf_s —** to wersja znaku dwubajtowego **sprintf_s —**; argumenty wskaźnika do **swprintf_s —** są ciągami znaków dwubajtowych. Wykrywanie kodowania błędów w **swprintf_s —** mogą się różnić od tego w **sprintf_s —**. Wersje tych funkcji **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych wątku.

W języku C++ korzystania z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu, co eliminuje potrzebę określenia argumentu rozmiaru, a te mogą automatycznie zastąpić starsze, niezabezpieczone funkcje za pomocą ich nowsze, bezpieczne odpowiedniki. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Istnieją wersje **sprintf_s —** , oferują dodatkową kontrolę nad co się stanie, jeśli bufor jest za mały. Aby uzyskać więcej informacji, zobacz [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf_s**|**sprintf_s**|**sprintf_s**|**swprintf_s**|
|**_stprintf_s_l**|**_sprintf_s_l**|**_sprintf_s_l**|**_swprintf_s_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**sprintf_s**, **_sprintf_s_l**|C: \<stdio.h><br /><br /> C++: \<cstdio — > lub \<stdio.h >|
|**swprintf_s**, **_swprintf_s_l**|C: \<stdio.h > lub \<wchar.h ><br /><br /> C++: \<cstdio>, \<cwchar>, \<stdio.h> or \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_sprintf_s.c
// This program uses sprintf_s to format various
// data and place them in the string named buffer.
//

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf_s( buffer, 200,     "   String:    %s\n", s );
   j += sprintf_s( buffer + j, 200 - j, "   Character: %c\n", c );
   j += sprintf_s( buffer + j, 200 - j, "   Integer:   %d\n", i );
   j += sprintf_s( buffer + j, 200 - j, "   Real:      %f\n", fp );

   printf_s( "Output:\n%s\ncharacter count = %d\n", buffer, j );
}
```

```Output
Output:
   String:    computer
   Character: l
   Integer:   35
   Real:      1.732053

character count = 79
```

## <a name="example"></a>Przykład

```C
// crt_swprintf_s.c
// wide character example
// also demonstrates swprintf_s returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf_s( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf_s( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf_s fails because string contains WEOF (\xffff)
   printf( "wrote %d characters\n", len );
}
```

```Output
wrote 11 characters
wrote -1 characters
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf, funkcje](../../c-runtime-library/vprintf-functions.md)<br/>
