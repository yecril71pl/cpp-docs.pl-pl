---
title: vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- _vsnprintf_s
- _vsntprintf_s
- _vsnwprintf_s
dev_langs:
- C++
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
caps.latest.revision: 30
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 230f60f33f37f1151af693f4de585bf78703e983
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="vsnprintfs-vsnprintfs-vsnprintfsl-vsnwprintfs-vsnwprintfsl"></a>vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l

Zapisywanie sformatowanego danych wyjściowych przy użyciu wskaźnika do listy argumentów. Są to wersje [vsnprintf —, _vsnprintf —, _vsnprintf_l —, _vsnwprintf —, _vsnwprintf_l —](vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Lokalizacja magazynu dla danych wyjściowych.

*sizeOfBuffer*<br/>
Rozmiar *buforu* dla danych wyjściowych jako liczba znaków.

*Liczba*<br/>
Maksymalna liczba znaków do zapisu (nie w tym zakończenia null), lub [_truncate —](../../c-runtime-library/truncate.md).

*Format*<br/>
Definicja formatu.

*argptr*<br/>
Wskaźnik do listy argumentów.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

Aby uzyskać więcej informacji, zobacz [specyfikacje formatu](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Wartość zwracana

**vsnprintf_s —**, **_vsnprintf_s —** i **_vsnwprintf_s —** zwraca liczbę znaków zapisane, nie tym zakończenia wartość null lub wartość ujemną, jeśli wystąpi błąd wyjścia. **vsnprintf_s —** jest taka sama jak **_vsnprintf_s —**. **vsnprintf_s —** jest uwzględniony w zgodności ze standardem ANSI. **_vnsprintf** został zachowany na potrzeby zgodności z poprzednimi wersjami.

Jeśli przekracza magazynu wymaganego do przechowywania danych i zakończenia null *sizeOfBuffer*, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md), chyba że *liczby*  jest [_truncate —](../../c-runtime-library/truncate.md), w którym to przypadku tyle ciągu jako zmieści się *buforu* są zapisywane i zwrócił wartość -1. Jeśli program obsługi nieprawidłowych parametrów wykonywania odtwarzanie jest kontynuowane, te funkcje ustawić *buforu* na pusty ciąg, ustaw **errno** do **erange —**i zwróć -1.

Jeśli *buforu* lub *format* jest **NULL** wskaźnika, lub, jeśli *liczba* jest mniejsza lub równa zero, program obsługi nieprawidłowych parametrów jest wywoływany. Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji **errno** do **einval —** i zwróć -1.

### <a name="error-conditions"></a>Warunki błędów

|**Warunek**|Zwraca|**errno**|
|-----------------|------------|-------------|
|*Bufor* jest **wartości NULL**|-1|**EINVAL —**|
|*Format* jest **wartości NULL**|-1|**EINVAL —**|
|*Liczba* < = 0|-1|**EINVAL —**|
|*sizeOfBuffer* za mały (i *liczba* ! = **_truncate —**)|-1 (i *buforu* ustawiony na pusty ciąg)|**ERANGE —**|

## <a name="remarks"></a>Uwagi

Każda z tych funkcji przyjmuje wskaźnik do listy argumentów, a następnie formatuje i zapisuje do *liczba* znaki określone dane do pamięci wskazywanej przez *buforu* i dołącza zakończenia wartości null.

Jeśli *liczba* jest [_truncate —](../../c-runtime-library/truncate.md), a następnie zapisać te funkcje, jaka ciągu, ile zmieści się *buforu* pozostawiając miejsca do zakończenia wartości null. Jeśli cały ciąg (przy użyciu zakończenia wartości null) mieści się w *buforu*, następnie funkcje zwracają liczbę znaków, zapisane (bez przerywania null); w przeciwnym razie funkcje zwracają wartość -1, aby wskazać, że obcięcie Wystąpił.

Wersje tych funkcji z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych przekazano zamiast bieżącego ustawienia regionalne wątku.

> [!IMPORTANT]
> Upewnij się, że *format* nie jest ciągiem zdefiniowane przez użytkownika. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).

> [!NOTE]
> Aby upewnić się, czy jest miejsce na null Trwa przerywanie działania, upewnij się, że *liczba* jest ściśle mniejsza niż długość buforu, lub użyj **_truncate —**.

W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (wyeliminowanie konieczności określania argumentem rozmiaru) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf_s —**|**_vsnprintf_s**|**_vsnprintf_s**|**_vsnwprintf_s**|
|**_vsntprintf_s_l —**|**_vsnprintf_s_l**|**_vsnprintf_s_l**|**_vsnwprintf_s_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**vsnprintf_s**|\<stdio.h > i \<stdarg.h >|\<varargs.h>*|
|**_vsnprintf_s —**, **_vsnprintf_s_l —**|\<stdio.h > i \<stdarg.h >|\<varargs.h>*|
|**_vsnwprintf_s —**, **_vsnwprintf_s_l —**|\<stdio.h > lub \<wchar.h >, a \<stdarg.h >|\<varargs.h>*|

\* Wymagany w przypadku zgodności UNIX V.

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

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf, funkcje](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
