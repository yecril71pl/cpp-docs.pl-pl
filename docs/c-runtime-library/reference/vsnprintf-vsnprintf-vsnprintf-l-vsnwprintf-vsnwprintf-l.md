---
title: vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l
ms.date: 11/04/2016
api_name:
- _vsnprintf
- _vsnprintf_l
- _vsnwprintf
- _vsnwprintf_l
- _vsnprintf
- _vsnprintf;
- vsnprintf; _vsnprintf
- _vsnwprintf;
- _vsnprintf_l;
- _vsnwprintf_l;
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
- ntoskrnl.exe
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _vsnprintf
- _vsnwprintf
- _vsntprintf
- vsnprintf
- stdio/vsnprintf
- stdio/_vsnprintf
- stdio/_vsnprintf_l
- stdio/_vsnwprintf
- stdio/_vsnwprintf_l
- _vsnprintf_l
- _vsnwprintf_l
helpviewer_keywords:
- vsntprintf function
- _vsnwprintf_l function
- vsnwprintf_l function
- vsntprintf_l function
- _vsntprintf function
- _vsnprintf_l function
- vsnprintf function
- _vsntprintf_l function
- vsnprintf_l function
- _vsnwprintf function
- _vsnprintf function
- formatted text [C++]
- vsnwprintf function
ms.assetid: a97f92df-c2f8-4ea0-9269-76920d2d566a
ms.openlocfilehash: abe34dc0f3baf9bdc63e0314ac70af3783d2bd9a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857713"
---
# <a name="vsnprintf-_vsnprintf-_vsnprintf_l-_vsnwprintf-_vsnwprintf_l"></a>vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l

Napisz sformatowane dane wyjściowe przy użyciu wskaźnika do listy argumentów. Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l](vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md).

## <a name="syntax"></a>Składnia

```C
int vsnprintf(
   char *buffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf(
   char *buffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_l(
   char *buffer,
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vsnwprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vsnwprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int vsnprintf(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnprintf(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnprintf_l(
   char (&buffer)[size],
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf_l(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>Parametry

*buffer*<br/>
Lokalizacja magazynu dla danych wyjściowych.

*count*<br/>
Maksymalna liczba znaków do zapisania.

*format*<br/>
Format specyfikacji.

*argptr*<br/>
Wskaźnik na listę argumentów.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

Aby uzyskać więcej informacji, zobacz temat [Formatowanie specyfikacji](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Wartość zwrócona

Funkcja **vsnprintf** zwraca liczbę znaków pisanych, a nie zlicza kończącego znaku null. Jeśli rozmiar buforu określony przez *licznik* nie jest wystarczająco duży, aby można było zawierać dane wyjściowe określone przez *Format* i *argptr*, wartość zwracana przez **vsnprintf** to liczba znaków, które mają być zapisywane, a nie zliczanie znaku null, jeśli *Liczba* była wystarczająco duża. Jeśli wartość zwracana jest większa niż *Liczba* -1, dane wyjściowe zostały obcięte. Zwracana wartość-1 wskazuje, że wystąpił błąd kodowania.

Funkcje **_vsnprintf** i **_vsnwprintf** zwracają liczbę znaków napisanych, jeśli liczba znaków do zapisania jest mniejsza lub równa *liczbie.* Jeśli liczba znaków do zapisania jest większa niż *Liczba*, te funkcje zwracają wartość-1 wskazującą, że dane wyjściowe zostały obcięte.

Wartość zwracana przez wszystkie te funkcje nie obejmuje kończącej wartości null, niezależnie od tego, czy jest ona zapisywana. Gdy *Liczba* jest równa zero, zwracana wartość jest liczbą znaków, które mogą być zapisywane przez funkcje, bez uwzględniania żadnego kończącego null. Możesz użyć tego wyniku do przydzielenia wystarczającej ilości miejsca w buforze dla ciągu i jego końcowej wartości null, a następnie ponownie wywołaj funkcję, aby wypełnić bufor.

Jeśli *Format* ma **wartość null**lub jeśli *bufor* ma **wartość null** , a *Liczba* nie jest równa zero, te funkcje wywołują procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość-1 i ustawiają **errno** na **EINVAL**.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji Pobiera wskaźnik do listy argumentów, a następnie formatuje dane i zapisuje do *liczby* znaków w pamięci wskazywanej przez *bufor*. Funkcja **vsnprintf** zawsze zapisuje terminator o wartości null, nawet jeśli obcina dane wyjściowe. W przypadku używania **_vsnprintf** i **_vsnwprintf**bufor będzie zakończony wartością null tylko wtedy, gdy występuje miejsce na końcu (to oznacza, że liczba znaków do zapisania jest mniejsza niż *Liczba*).

> [!IMPORTANT]
> Aby uniknąć pewnego rodzaju zagrożeń bezpieczeństwa, upewnij się, że *Format* nie jest ciągiem zdefiniowanym przez użytkownika. Aby uzyskać więcej informacji, zobacz [unikanie przekroczeń buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

> [!NOTE]
> Aby upewnić się, że istnieje pomieszczenie dla kończącej wartości null podczas wywoływania **_vsnprintf**, **_vsnprintf_l**, **_vsnwprintf** i **_vsnwprintf_l**, upewnij się, że *Liczba* jest ściśle mniejsza niż długość buforu i zainicjuj bufor na wartość null przed wywołaniem funkcji.
>
> Ponieważ **vsnprintf** zawsze zapisuje kończącą wartość null, parametr *Count* może być równy rozmiarowi buforu.

Począwszy od UCRT w programie Visual Studio 2015 i Windows 10, **vsnprintf** nie jest już identyczna z **_vsnprintf**. Funkcja **vsnprintf** jest zgodna ze standardem C99; **_vnsprintf** jest zachowywana na potrzeby zgodności z poprzednimi wersjami ze starszym kodem programu Visual Studio.

Wersje tych funkcji z sufiksem **_l** są identyczne, z tą różnicą, że korzystają z przekazaną parametrem ustawień regionalnych zamiast bieżących ustawień regionalnych wątku.

W języku programowania C++ funkcje te mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf**|**_vsnprintf**|**_vsnprintf**|**_vsnwprintf**|
|**_vsntprintf_l**|**_vsnprintf_l**|**_vsnprintf_l**|**_vsnwprintf_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|-------------|---------------------------|-------------------------------|
|**vsnprintf**, **_vsnprintf**, **_vsnprintf_l**|\<stdio.h>|\<stdio. h > lub \<cstdio >|
|**_vsnwprintf**, **_vsnwprintf_l**|\<stdio. h > lub \<WCHAR. h >|\<stdio. h >, \<WCHAR. h >, \<cstdio > lub \<cwchar >|

Funkcje **_vsnprintf**, **_vsnprintf_l**, **_vsnwprintf** i **_vsnwprintf_l** są specyficzne dla firmy Microsoft. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_vsnwprintf.c
// compile by using: cl /W3 crt_vsnwprintf.c

// To turn off error C4996, define this symbol:
#define _CRT_SECURE_NO_WARNINGS

#include <stdio.h>
#include <wtypes.h>

#define BUFFCOUNT (10)

void FormatOutput(LPCWSTR formatstring, ...)
{
    int nSize = 0;
    wchar_t buff[BUFFCOUNT];
    memset(buff, 0, sizeof(buff));
    va_list args;
    va_start(args, formatstring);
    // Note: _vsnwprintf is deprecated; consider vsnwprintf_s instead
    nSize = _vsnwprintf(buff, BUFFCOUNT - 1, formatstring, args); // C4996
    wprintf(L"nSize: %d, buff: %ls\n", nSize, buff);
    va_end(args);
}

int main() {
    FormatOutput(L"%ls %ls", L"Hi", L"there");
    FormatOutput(L"%ls %ls", L"Hi", L"there!");
    FormatOutput(L"%ls %ls", L"Hi", L"there!!");
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: -1, buff: Hi there!
```

Zachowanie zmienia się w przypadku użycia vsnprintf zamiast parametrów z wąskim ciągiem. Parametr *Count* może być rozmiarem całego buforu, a wartością zwracaną jest liczba znaków, które zostałyby wprowadzone, jeśli *Liczba* była wystarczająco duża:

## <a name="example"></a>Przykład

```C
// crt_vsnprintf.c
// compile by using: cl /W4 crt_vsnprintf.c
#include <stdio.h>
#include <stdarg.h> // for va_list, va_start
#include <string.h> // for memset

#define BUFFCOUNT (10)

void FormatOutput(char* formatstring, ...)
{
    int nSize = 0;
    char buff[BUFFCOUNT];
    memset(buff, 0, sizeof(buff));
    va_list args;
    va_start(args, formatstring);
    nSize = vsnprintf(buff, sizeof(buff), formatstring, args);
    printf("nSize: %d, buff: %s\n", nSize, buff);
    va_end(args);
}

int main() {
    FormatOutput("%s %s", "Hi", "there");   //  8 chars + null
    FormatOutput("%s %s", "Hi", "there!");  //  9 chars + null
    FormatOutput("%s %s", "Hi", "there!!"); // 10 chars + null
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: 10, buff: Hi there!
```

## <a name="see-also"></a>Zobacz także

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf, funkcje](../../c-runtime-library/vprintf-functions.md)<br/>
[Składnia specyfikacji formatu: funkcje printf i wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
