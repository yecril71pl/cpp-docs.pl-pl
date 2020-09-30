---
title: vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l
ms.date: 11/04/2016
api_name:
- _vsnwprintf_s
- _vsnwprintf_s_l
- _vsnprintf_s
- vsnprintf_s
- _vsnprintf_s_l
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _vsnprintf_s
- _vsntprintf_s
- _vsnwprintf_s
helpviewer_keywords:
- vsnwprintf_s function
- _vsntprintf_s function
- _vsntprintf_s_l function
- vsntprintf_s function
- vsnwprintf_s_l function
- vsnprintf_s_l function
- vsntprintf_s_l function
- _vsnwprintf_s_l function
- _vsnprintf_s function
- vsnprintf_s function
- _vsnprintf_s_l function
- _vsnwprintf_s function
- formatted text [C++]
ms.assetid: 147ccfce-58c7-4681-a726-ef54ac1c604e
ms.openlocfilehash: edb534eb533d63c9298b7b7e9aced1be3e8652d9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502789"
---
# <a name="vsnprintf_s-_vsnprintf_s-_vsnprintf_s_l-_vsnwprintf_s-_vsnwprintf_s_l"></a>vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l

Napisz sformatowane dane wyjściowe przy użyciu wskaźnika do listy argumentów. Są to wersje [vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf _vsnwprintf_l](vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcjach zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
int vsnprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vsnwprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vsnwprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int _vsnprintf_s(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf_s(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>Parametry

*buforu*<br/>
Lokalizacja magazynu dla danych wyjściowych.

*sizeOfBuffer*<br/>
Rozmiar *buforu* dla danych wyjściowych w postaci liczby znaków.

*liczbą*<br/>
Maksymalna liczba znaków do zapisania (bez uwzględnienia kończącego się wartości null) lub [_TRUNCATE](../../c-runtime-library/truncate.md).

*Formatowanie*<br/>
Specyfikacja formatu.

*argptr*<br/>
Wskaźnik na listę argumentów.

*locale*<br/>
Ustawienia regionalne do użycia.

Aby uzyskać więcej informacji, zobacz temat [Formatowanie specyfikacji](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Wartość zwracana

**vsnprintf_s**, **_vsnprintf_s** i **_vsnwprintf_s** zwrócić liczbę znaków, bez uwzględnienia kończącej wartości null lub wartość ujemną, jeśli wystąpi błąd obcinania danych lub błędu wyjściowego.

* Jeśli *Liczba* jest mniejsza niż *sizeOfBuffer* , a liczba znaków w danych jest mniejsza lub równa *liczbie*, lub *licznik* jest [_TRUNCATE](../../c-runtime-library/truncate.md) a liczba znaków w danych jest mniejsza niż *sizeOfBuffer*, wszystkie dane są zapisywane i zwracana jest liczba znaków.

* Jeśli *Liczba* jest mniejsza niż *sizeOfBuffer* , ale dane przekraczają *liczbę* znaków, zapisywane są pierwsze znaki *Count* . Obcinanie pozostałych danych następuje, a-1 jest zwracane bez wywoływania nieprawidłowego parametru procedury obsługi.

* Jeśli *Liczba* jest [_TRUNCATE](../../c-runtime-library/truncate.md) , a liczba znaków w danych jest równa lub większa niż *sizeOfBuffer*, wówczas jest zapisywana część ciągu jako przenosząca się do *buforu* (z końcowym zerem). Obcinanie pozostałych danych następuje, a-1 jest zwracane bez wywoływania nieprawidłowego parametru procedury obsługi.

* Jeśli *Liczba* jest równa lub przekracza *sizeOfBuffer* , ale liczba znaków danych jest mniejsza niż *sizeOfBuffer*, wszystkie dane są zapisywane (z końcowym zerem) i zwracana jest liczba znaków.

* Jeśli *Liczba* i liczba znaków danych jest równa lub większa niż *sizeOfBuffer*, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonywanie jest kontynuowane po procedurze obsługi nieprawidłowego parametru, te funkcje ustawiają *bufor* na pusty ciąg, ustawia **errno** na **ERANGE**i zwracają-1.

* Jeśli *bufor* lub *Format* jest wskaźnikiem typu **null** lub jeśli *licznik* jest mniejszy lub równy zero, zostanie wywołana procedura obsługi nieprawidłowego parametru. Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** na **EINVAL** i Return-1.

### <a name="error-conditions"></a>Warunki błędów

|**Warunek**|Przesłać|**errno**|
|-----------------|------------|-------------|
|*bufor* ma **wartość null**|-1|**EINVAL**|
|*Format* ma **wartość null**|-1|**EINVAL**|
|*liczba* <= 0|-1|**EINVAL**|
|*sizeOfBuffer* za mały (i *count* ! = **_TRUNCATE**)|-1 (i *bufor* ustawiony na pusty ciąg)|**ERANGE**|

## <a name="remarks"></a>Uwagi

**vsnprintf_s** jest taka sama jak **_vsnprintf_s**. **vsnprintf_s** jest dołączona do zgodności ze standardem ANSI. **_vnsprintf** jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami.

Każda z tych funkcji Pobiera wskaźnik do listy argumentów, a następnie formatuje i zapisuje dane do *zliczania* znaków danych w pamięci wskazanej przez *bufor* i dołącza kończące wartość null.

Jeśli *Liczba* jest [_TRUNCATE](../../c-runtime-library/truncate.md), wówczas te funkcje zapisują tyle, ile ciągu jest w *buforze* , podczas gdy opuszcza miejsce na zakończenie wartości null. Jeśli cały ciąg (z kończącą się wartością null) mieści się w *buforze*, te funkcje zwracają liczbę znaków, które są zapisywane (nie dotyczy kończącego null); w przeciwnym razie te funkcje zwracają-1, aby wskazać, że wystąpiło obcinanie.

Wersje tych funkcji z sufiksem **_l** są identyczne, z tą różnicą, że korzystają z przekazaną parametrem ustawień regionalnych zamiast bieżących ustawień regionalnych wątku.

> [!IMPORTANT]
> Upewnij się, że *Format* nie jest ciągiem zdefiniowanym przez użytkownika. Aby uzyskać więcej informacji, zobacz [unikanie przekroczeń buforu](/windows/win32/SecBP/avoiding-buffer-overruns).

> [!NOTE]
> Aby upewnić się, że istnieje pomieszczenie dla kończącej wartości null, upewnij się, że *Liczba* jest ściśle mniejsza niż długość buforu lub Użyj **_TRUNCATE**.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując konieczność określenia argumentu rozmiaru) i mogą automatycznie zastąpić starsze, niezabezpieczone funkcje z ich nowszymi, bezpiecznymi odpowiednikami. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf_s**|**_vsnprintf_s**|**_vsnprintf_s**|**_vsnwprintf_s**|
|**_vsntprintf_s_l**|**_vsnprintf_s_l**|**_vsnprintf_s_l**|**_vsnwprintf_s_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**vsnprintf_s**|\<stdio.h> i \<stdarg.h>|\<varargs.h>*|
|**_vsnprintf_s**, **_vsnprintf_s_l**|\<stdio.h> i \<stdarg.h>|\<varargs.h>*|
|**_vsnwprintf_s**, **_vsnwprintf_s_l**|\<stdio.h> lub \<wchar.h> , i \<stdarg.h>|\<varargs.h>*|

\* Wymagane w przypadku zgodności z systemem UNIX V.

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```cpp
// crt_vsnprintf_s.cpp
#include <stdio.h>
#include <wtypes.h>

void FormatOutput(LPCSTR formatstring, ...)
{
   int nSize = 0;
   char buff[10];
   memset(buff, 0, sizeof(buff));
   va_list args;
   va_start(args, formatstring);
   nSize = vsnprintf_s( buff, _countof(buff), _TRUNCATE, formatstring, args);
   printf("nSize: %d, buff: %s\n", nSize, buff);
   va_end(args);
}

int main() {
   FormatOutput("%s %s", "Hi", "there");
   FormatOutput("%s %s", "Hi", "there!");
   FormatOutput("%s %s", "Hi", "there!!");
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: -1, buff: Hi there!
```

## <a name="see-also"></a>Zobacz też

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[Funkcje vprintf —](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf —, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
