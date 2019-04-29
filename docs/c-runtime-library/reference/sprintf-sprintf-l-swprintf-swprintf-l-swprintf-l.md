---
title: sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l
ms.date: 11/04/2016
apiname:
- __swprintf_l
- sprintf
- _sprintf_l
- _swprintf_l
- swprintf
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _stprintf_l
- __swprintf_l
- sprintf_l
- swprintf
- _sprintf_l
- sprintf
- _stprintf
- stprintf_l
helpviewer_keywords:
- _swprintf_l function
- _stprintf function
- __swprintf_l function
- stprintf function
- sprintf function
- _sprintf_l function
- _stprintf_l function
- swprintf function
- strings [C++], writing to
- _CRT_NON_CONFORMING_SWPRINTFS
- swprintf_l function
- stprintf_l function
- sprintf_l function
- formatted text [C++]
ms.assetid: f6efe66f-3563-4c74-9455-5411ed939b81
ms.openlocfilehash: f32b1622539e73ab04c19d6d46ffdbc58b9961d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62354876"
---
# <a name="sprintf-sprintfl-swprintf-swprintfl-swprintfl"></a>sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l

Wpisz sformatowane dane do ciągu. Bardziej bezpieczne wersje niektórych z tych funkcji są dostępne; zobacz [sprintf_s —, _sprintf_s_l —, swprintf_s —, _swprintf_s_l —](sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md). Bezpieczne wersje **swprintf** i **_swprintf_l —** nie przyjmują *liczba* parametru.

## <a name="syntax"></a>Składnia

```C
int sprintf(
   char *buffer,
   const char *format [,
   argument] ...
);
int _sprintf_l(
   char *buffer,
   const char *format,
   locale_t locale [,
   argument] ...
);
int swprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format [,
   argument]...
);
int _swprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
int __swprintf_l(
   wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
template <size_t size>
int sprintf(
   char (&buffer)[size],
   const char *format [,
   argument] ...
); // C++ only
template <size_t size>
int _sprintf_l(
   char (&buffer)[size],
   const char *format,
   locale_t locale [,
   argument] ...
); // C++ only
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Lokalizacja magazynowa danych wyjściowych

*Liczba*<br/>
Maksymalna liczba znaków do przechowywania w wersji Unicode tej funkcji.

*Format*<br/>
Ciąg formantu formatu

*argument*<br/>
Argumenty opcjonalne.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

Aby uzyskać więcej informacji, zobacz [specyfikacji formatu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Wartość zwracana

Liczba znaków zapisanych, lub -1, jeśli wystąpił błąd. Jeśli *buforu* lub *format* jest pustym wskaźnikiem, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość -1 i ustaw **errno** do **EINVAL**.

**sprintf** zwraca liczbę bajtów przechowywanych w *buforu*, nie licząc zamykającego kończącego znaku null. **swprintf** zwraca liczbę znaków szerokich przechowywanych w *buforu*, nie licząc zamykającego znaku pustego.

## <a name="remarks"></a>Uwagi

**Sprintf** funkcja formatuje i przechowuje serie znaków i wartości w *buforu*. Każdy *argument* (jeśli istnieje) jest konwertowaya i wychodzi według specyfikacji formatu w *format*. Format składa się ze znaków zwykłych i ma taką samą formę i funkcjonuje jako *format* argument [printf](printf-printf-l-wprintf-wprintf-l.md). Znak null jest dołączany po ostatnim napisanym znaku. Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.

> [!IMPORTANT]
> Za pomocą **sprintf**, nie ma możliwości ograniczenia liczby znaków zapisanych, co oznacza, że kod korzystający **sprintf** jest podatny na przepełnienia buforu. Należy rozważyć użycie funkcji pokrewnych [_snprintf](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md), która określa maksymalną liczbę znaków, które mają być zapisywane *buforu*, lub użyj [_scprintf](scprintf-scprintf-l-scwprintf-scwprintf-l.md) ustalenie, jak duże rozmiar buforu jest wymagany. Ponadto upewnij się, że *format* nie jest ciągiem zdefiniowanym przez użytkownika.

**swprintf** to wersja znaku dwubajtowego **sprintf**; argumenty wskaźnika do **swprintf** są ciągami znaków dwubajtowych. Wykrywanie kodowania błędów w **swprintf** mogą się różnić od tego w **sprintf**. **swprintf** i **fwprintf —** zachowują się identycznie, chyba że **swprintf** zapisuje dane wyjściowe do ciągu, a nie do miejsca docelowego typu **pliku**i **swprintf** wymaga *liczba* parametru, aby określić maksymalną liczbę znaków, które mają być zapisywane. Wersje tych funkcji **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych wątku.

**swprintf** jest zgodny ze standardem C ISO, co wymaga drugiego parametru, *liczba*, typu **size_t**. Aby wymusić stare niestandardowe zachowanie, zdefiniuj **_CRT_NON_CONFORMING_SWPRINTFS**. W przyszłej wersji stare zachowanie może być usunięte, więc kod powinien zostać zmieniony tak, aby użyć nowe zachowanie zgodne z normą.

W języku C++ funkcje te mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf —**|**sprintf**|**sprintf**|**_swprintf**|
|**_stprintf_l**|**_sprintf_l**|**_sprintf_l**|**__swprintf_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**sprintf**, **_sprintf_l**|\<stdio.h>|
|**swprintf**, **_swprintf_l —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_sprintf.c
// compile with: /W3
// This program uses sprintf to format various
// data and place them in the string named buffer.

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf( buffer,     "   String:    %s\n", s ); // C4996
   j += sprintf( buffer + j, "   Character: %c\n", c ); // C4996
   j += sprintf( buffer + j, "   Integer:   %d\n", i ); // C4996
   j += sprintf( buffer + j, "   Real:      %f\n", fp );// C4996
   // Note: sprintf is deprecated; consider using sprintf_s instead

   printf( "Output:\n%s\ncharacter count = %d\n", buffer, j );
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
// crt_swprintf.c
// wide character example
// also demonstrates swprintf returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf fails because string contains WEOF (\xffff)
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
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf, funkcje](../../c-runtime-library/vprintf-functions.md)<br/>
