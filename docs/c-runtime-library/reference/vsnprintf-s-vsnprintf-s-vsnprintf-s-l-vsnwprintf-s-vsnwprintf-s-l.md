---
title: vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l
ms.date: 11/04/2016
apiname:
- _vsnwprintf_s
- _vsnwprintf_s_l
- _vsnprintf_s
- vsnprintf_s
- _vsnprintf_s_l
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
ms.openlocfilehash: 255c3b760dec1495a4f9a82915878a5504844f24
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210708"
---
# <a name="vsnprintfs-vsnprintfs-vsnprintfsl-vsnwprintfs-vsnwprintfsl"></a>vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l

Napisz sformatowane wyniki za pomocą wskaźnika do listy argumentów. Są to wersje [vsnprintf —, _vsnprintf —, _vsnprintf_l —, _vsnwprintf —, _vsnwprintf_l —](vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*buffer*<br/>
Lokalizacja magazynowa danych wyjściowych.

*sizeOfBuffer*<br/>
Rozmiar *buforu* dla danych wyjściowych w formacie liczby znaków.

*Liczba*<br/>
Maksymalna liczba znaków do zapisu (nie wliczając zakończenia o wartości null), lub [_TRUNCATE](../../c-runtime-library/truncate.md).

*Format*<br/>
Specyfikacja formatu.

*argptr*<br/>
Wskaźnik do listy argumentów.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

Aby uzyskać więcej informacji, zobacz [specyfikacji formatu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Wartość zwracana

**vsnprintf_s —**, **_vsnprintf_s —** i **_vsnwprintf_s —** zwracają liczbę znaków napisanych, nie wliczając zakończenia o wartości null lub wartość ujemną, jeśli wystąpi błąd danych wyjściowych. **vsnprintf_s —** jest taka sama jak **_vsnprintf_s —**. **vsnprintf_s —** jest uwzględniany w przypadku zgodności ze standardem ANSI. **_vnsprintf** został zachowany na potrzeby zgodności z poprzednimi wersjami.

Jeśli magazynu wymaganego do przechowywania danych i kończącą wartość null, przekracza *sizeOfBuffer*, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md), chyba że *liczba*  jest [_TRUNCATE](../../c-runtime-library/truncate.md), w którym to przypadku tyle ciągu jako zmieści się w *buforu* jest zapisywana i zwracana wartość -1. Jeśli wykonywanie jest kontynuowane po nieprawidłowy parametr uchwytu, te funkcje ustawiają *buforu* na pusty ciąg, ustaw **errno** do **ERANGE**i zwracają wartość -1.

Jeśli *buforu* lub *format* jest **o wartości NULL** wskaźnika, lub jeśli *liczba* jest mniejszy niż lub równy zero, procedura obsługi nieprawidłowego parametru zostanie wywołana. Jeśli wykonanie może być kontynuowane, te funkcje ustawiają **errno** do **EINVAL** i zwracają wartość -1.

### <a name="error-conditions"></a>Warunki błędów

|**Warunek**|Wróć|**numer błędu**|
|-----------------|------------|-------------|
|*Bufor* jest **o wartości NULL**|-1|**EINVAL**|
|*Format* jest **o wartości NULL**|-1|**EINVAL**|
|*Liczba* < = 0|-1|**EINVAL**|
|*sizeOfBuffer* za mały (i *liczba* ! = **_TRUNCATE**)|-1 (i *buforu* ustawiony na pusty ciąg)|**ERANGE**|

## <a name="remarks"></a>Uwagi

Każda z tych funkcji pobiera wskaźnik do listy argumentów, a następnie formatuje i zapisuje do *liczba* znaków dostarczone dane do pamięci wskazywany przez *buforu* i dołącza zakończenia o wartości null.

Jeśli *liczba* jest [_TRUNCATE](../../c-runtime-library/truncate.md), wówczas te funkcje wpisuje tyle parametrów pasujące *buforu* przy równoczesnym zachowaniu miejsca do zakończenia o wartości null. Jeśli cały ciąg (z zakończenia o wartości null) są dopasowane do *buforu*, następnie te funkcje zwracają liczbę znaków napisanych (nie wliczając zakończenia o wartości null); w przeciwnym wypadku te funkcje zwracają wartość -1, aby wskazać, że obcięcie Wystąpił.

Wersje tych funkcji **_l** sufiksem są identyczne, z tą różnicą, że używają parametru ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych wątku.

> [!IMPORTANT]
> Upewnij się, że *format* nie jest ciągiem zdefiniowanym przez użytkownika. Aby uzyskać więcej informacji, zobacz [unikanie przepełnień bufora](/windows/desktop/SecBP/avoiding-buffer-overruns).

> [!NOTE]
> Aby upewnić się, że ma miejsce dla zakończenia o wartości null, upewnij się, że *liczba* jest mniejsza niż długość buforu lub użyj **_TRUNCATE**.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując potrzebę określenia argumentu rozmiaru) oraz ich mogą automatycznie zastąpić starsze, niezabezpieczone funkcje ich nowsze, bezpieczne odpowiedniki. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf_s**|**_vsnprintf_s**|**_vsnprintf_s**|**_vsnwprintf_s**|
|**_vsntprintf_s_l**|**_vsnprintf_s_l**|**_vsnprintf_s_l**|**_vsnwprintf_s_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**vsnprintf_s**|\<stdio.h > i \<stdarg.h >|\<varargs.h>*|
|**_vsnprintf_s**, **_vsnprintf_s_l**|\<stdio.h > i \<stdarg.h >|\<varargs.h>*|
|**_vsnwprintf_s**, **_vsnwprintf_s_l**|\<stdio.h > lub \<wchar.h >, a \<stdarg.h >|\<varargs.h>*|

\* Wymagane dla zgodności systemu UNIX V.

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf, funkcje](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
