---
title: wcstombs_s, _wcstombs_s_l
ms.date: 11/04/2016
apiname:
- _wcstombs_s_l
- wcstombs_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcstombs_s
- _wcstombs_s_l
helpviewer_keywords:
- wcstombs_s function
- string conversion, wide characters
- wide characters, converting
- _wcstombs_s_l function
- wcstombs_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 105f2d33-221a-4f6d-864c-23c1865c42af
ms.openlocfilehash: 3f30ef1f94803005a1afd99a6f82c46296f5c4f7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499002"
---
# <a name="wcstombs_s-_wcstombs_s_l"></a>wcstombs_s, _wcstombs_s_l

Konwertuje sekwencję szerokich znaków do odpowiedniej sekwencji znaków wielobajtowych. Wersja [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t wcstombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t *wcstr,
   size_t count
);

errno_t _wcstombs_s_l(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);

template <size_t size>
errno_t wcstombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only

template <size_t size>
errno_t _wcstombs_s_l(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Rozmiar w bajtach przekonwertowanego ciągu, łącznie z terminatorem wartości null.

*mbstr*<br/>
Adres buforu dla wyniku konwertowanego ciągu znaków wielobajtowych.

*sizeInBytes*<br/>
Rozmiar w bajtach buforu *mbstr* .

*wcstr*<br/>
Wskazuje ciąg znaków dwubajtowych do przekonwertowania.

*liczbą*<br/>
Maksymalna liczba bajtów do zapisania w buforze *mbstr* , bez uwzględnienia kończącego znaku null lub [_TRUNCATE](../../c-runtime-library/truncate.md).

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie, kod błędu w przypadku niepowodzenia.

|Warunek błędu|Wartość zwracana i **errno**|
|---------------------|------------------------------|
|*mbstr* ma **wartość NULL** i *sizeInBytes* > 0|**EINVAL**|
|*wcstr* ma **wartość null**|**EINVAL**|
|Bufor docelowy jest zbyt mały, aby zawierał przekonwertowany ciąg (chyba że *licznik* jest **_TRUNCATE**; Zobacz uwagi poniżej)|**ERANGE**|

Jeśli wystąpi którykolwiek z tych warunków, wyjątek nieprawidłowego parametru jest wywoływany zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, funkcja zwraca kod błędu i ustawia **errno** , jak wskazano w tabeli.

## <a name="remarks"></a>Uwagi

Funkcja **wcstombs_s** konwertuje ciąg znaków dwubajtowych, do których odnoszą się *wcstr* , do znaków wielowartościowych przechowywanych w buforze wskazywanym przez *mbstr*. Konwersja będzie kontynuowana dla każdego znaku do momentu spełnienia jednego z następujących warunków:

- Napotkano zerowy znak dwubajtowy

- Napotkano znak dwubajtowy, którego nie można przekonwertować

- Liczba bajtów przechowywanych w buforze *mbstr* jest równa *Count*.

Ciąg docelowy jest zawsze zakończony wartością null (nawet w przypadku błędu).

Jeśli *licznik* jest wartością specjalną [_TRUNCATE](../../c-runtime-library/truncate.md), **wcstombs_s** konwertuje tyle ciągu jako ciąg, jak zmieści się w buforze docelowym, pozostawiając nadal miejsce na terminator o wartości null. Jeśli ciąg zostanie obcięty, wartość zwracana to **STRUNCATE**, a konwersja zostanie uznana za pomyślnie.

Jeśli **wcstombs_s** pomyślnie konwertuje ciąg źródłowy, umieści rozmiar w bajtach przekonwertowanego ciągu, łącznie z terminatorem wartości null, na  *&#42;pReturnValue* (podany *pReturnValue* nie ma **wartości null**). Dzieje się tak nawet wtedy, gdy argument *mbstr* ma **wartość null** i umożliwia określenie wymaganego rozmiaru buforu. Należy pamiętać, że jeśli *mbstr* ma **wartość null**, *Count* jest ignorowany.

Jeśli **wcstombs_s** napotka znak dwubajtowy, nie może on zostać skonwertowany na znak wieloznaczny, umieszcza 0 w  *&#42;pReturnValue*, ustawia bufor docelowy na pusty ciąg, **ustawia errno** na **EILSEQ**i zwraca **EILSEQ**.

Jeśli sekwencje wskazywane przez *wcstr* i *mbstr* nakładają się na siebie, zachowanie **wcstombs_s** jest niezdefiniowane.

> [!IMPORTANT]
> Upewnij się, że *wcstr* i *mbstr* nie nakładają się na siebie, i że *licznik* poprawnie odzwierciedla liczbę szerokich znaków do przekonwertowania.

**wcstombs_s** używa bieżących ustawień regionalnych dla wszelkich zachowań zależnych od ustawień regionalnych; **_wcstombs_s_l** jest taka sama jak **wcstombs** , z tą różnicą, że w zamian korzysta z przekazaną ustawieniami regionalnymi. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

W C++programie korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując konieczność określenia argumentu rozmiaru) i mogą automatycznie zastąpić starsze, niezabezpieczone funkcje z ich nowszymi, bezpiecznymi odpowiednikami. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wcstombs_s**|\<stdlib.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program ilustruje zachowanie funkcji **wcstombs_s** .

```C
// crt_wcstombs_s.c
// This example converts a wide character
// string to a multibyte character string.
#include <stdio.h>
#include <stdlib.h>
#include <assert.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t   i;
    char      *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t*pWCBuffer = L"Hello, world.";

    printf( "Convert wide-character string:\n" );

    // Conversion
    wcstombs_s(&i, pMBBuffer, (size_t)BUFFER_SIZE,
               pWCBuffer, (size_t)BUFFER_SIZE );

    // Output
    printf("   Characters converted: %u\n", i);
    printf("    Multibyte character: %s\n\n",
     pMBBuffer );

    // Free multibyte character buffer
    if (pMBBuffer)
    {
    free(pMBBuffer);
    }
}
```

```Output
Convert wide-character string:
   Characters converted: 14
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
