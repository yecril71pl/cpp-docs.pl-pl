---
title: vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
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
- ntoskrnl.exe
- ucrtbase.dll
apitype: DLLExport
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 738a69ad0acd1af3b400b56f0f759414b9e28578
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451605"
---
# <a name="vsnprintf-vsnprintf-vsnprintfl-vsnwprintf-vsnwprintfl"></a>vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l

Zapisywanie sformatowanego danych wyjściowych przy użyciu wskaźnika do listy argumentów. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [vsnprintf_s —, _vsnprintf_s —, _vsnprintf_s_l —, _vsnwprintf_s —, _vsnwprintf_s_l —](vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md).

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

*Liczba*<br/>
Maksymalna liczba znaków do zapisu.

*Format*<br/>
Definicja formatu.

*argptr*<br/>
Wskaźnik do listy argumentów.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

Aby uzyskać więcej informacji, zobacz [specyfikacje formatu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Wartość zwracana

**Vsnprintf —** funkcja zwraca liczbę znaków zapisane, nie licząc znak końcowy null. Jeśli rozmiar buforu określony przez *liczba* nie jest wystarczająco duży, aby określi dane wyjściowe zawierają *format* i *argptr*, zwracana wartość  **vsnprintf —** jest liczba znaków, które powinny być zapisane, nie licząc znak null, jeśli *liczba* dostatecznie duża. Jeśli wartość zwracana jest większa niż *liczba* - 1, dane wyjściowe zostały obcięte. Zwracana wartość -1 wskazuje, że wystąpił błąd kodowania.

Zarówno **_vsnprintf —** i **_vsnwprintf —** zwracają liczbę znaków, jeśli liczba znaków do zapisu jest mniejsze niż lub równe *liczba*; Jeśli jest to liczba znaków do zapisania jest większa niż *liczby*, te funkcje zwracany -1, wskazującą, czy dane wyjściowe zostały obcięte.

Wartość zwrócona przez te funkcje nie ma zakończenia wartość null, czy jeden są zapisywane lub nie. Gdy *liczba* wynosi zero, wartość zwracana jest liczba znaków funkcje zapisać, nie w tym wszelkie zakończenia wartości null. Można użyciu tego wyniku Przydziel wystarczająca ilość miejsca w buforze na ciąg i jego zakończenia wartość null, a następnie wywołaj funkcję ponownie w celu wypełnienia buforu.

Jeśli *format* jest **NULL**, lub jeśli *buforu* jest **NULL** i *liczby* nie jest równa zero, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zwróć -1, jeśli wykonanie może kontynuować, następujące funkcje i ustaw **errno** do **einval —**.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji przyjmuje wskaźnik do listy argumentów, a następnie formatuje dane i zapisuje do *liczba* znaków do pamięci wskazywanej przez *buforu*. **Vsnprintf —** funkcja zawsze zapisuje terminatorem null, nawet jeśli jego obcina dane wyjściowe. Korzystając z **_vsnprintf —** i **_vsnwprintf —**, bufor będzie być zakończony zerem tylko wtedy, gdy jest miejsca na końcu (to znaczy, jeśli liczba znaków do zapisania jest mniejsza niż *liczba*).

> [!IMPORTANT]
> Aby zapobiec niektóre rodzaje zagrożenia bezpieczeństwa, upewnij się, że *format* nie jest ciągiem zdefiniowane przez użytkownika. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).

> [!NOTE]
> Aby upewnić się, że jest miejsce na zakończenia wartości null podczas wywoływania metody **_vsnprintf —**, **_vsnprintf_l —**, **_vsnwprintf —** i **_vsnwprintf_l —**, upewnij się, że *liczba* jest ściśle mniejsza niż długość buforu i zainicjuj buforu na wartość null przed wywołaniem funkcji.
>
> Ponieważ **vsnprintf —** zawsze zapisuje zakończenia wartość null, *liczba* parametru może być taka sama jak rozmiar buforu.

Począwszy od Biblioteka UCRT w programie Visual Studio 2015 i Windows 10 **vsnprintf —** nie jest już takie same jak **_vsnprintf —**. **Vsnprintf —** funkcji jest zgodny ze standardem C99; **_vnsprintf** został zachowany na potrzeby zgodności z poprzednimi wersjami z starszego kodu programu Visual Studio.

Wersje tych funkcji z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżącego ustawienia regionalne wątku.

W języku C++ te funkcje mają przeciążenia szablonu, które wywołują odpowiedników nowsza, bezpieczne tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf —**|**_vsnprintf**|**_vsnprintf**|**_vsnwprintf**|
|**_vsntprintf_l —**|**_vsnprintf_l**|**_vsnprintf_l**|**_vsnwprintf_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymaganego nagłówka (C++)|
|-------------|---------------------------|-------------------------------|
|**vsnprintf —**, **_vsnprintf —**, **_vsnprintf_l —**|\<stdio.h>|\<stdio.h > lub \<cstdio — >|
|**_vsnwprintf —**, **_vsnwprintf_l —**|\<stdio.h > lub \<wchar.h >|\<stdio.h >, \<wchar.h >, \<cstdio — >, lub \<cwchar — >|

**_Vsnprintf —**, **_vsnprintf_l —**, **_vsnwprintf —** i **_vsnwprintf_l —** funkcje są określone firmy Microsoft. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

Zmiany sposobu działania, jeśli zamiast tego użyj vsnprintf — wraz z parametrami wąski ciąg. *Liczba* parametr może być cały rozmiar buforu, a wartość zwracana jest liczba znaków, które będą zapisywane, jeśli *liczba* był wystarczająco duży:

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

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf, funkcje](../../c-runtime-library/vprintf-functions.md)<br/>
[Składnia specyfikacji formatu: funkcje printf i wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
