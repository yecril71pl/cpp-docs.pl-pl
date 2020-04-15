---
title: wcstombs_s, _wcstombs_s_l
ms.date: 4/2/2020
api_name:
- _wcstombs_s_l
- wcstombs_s
- _o__wcstombs_s_l
- _o_wcstombs_s
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: c20066cddb3f28d31d2964ec720b64ed49836f65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328047"
---
# <a name="wcstombs_s-_wcstombs_s_l"></a>wcstombs_s, _wcstombs_s_l

Konwertuje sekwencję znaków szerokich na odpowiednią sekwencję znaków wielobajtowych. Wersja [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*pZawąkaWartość*<br/>
Rozmiar w bajtach przekonwertowanego ciągu, w tym zerowy terminator.

*mbstr*<br/>
Adres buforu dla wynikowego przekonwertowanego wielobajtowego ciągu znaków.

*rozmiarWzdjęty*<br/>
Rozmiar w bajtach buforu *mbstr.*

*wcstr*<br/>
Wskazuje szeroki ciąg znaków do konwersji.

*Liczba*<br/>
Maksymalna liczba bajtów do zapisania w buforze *mbstr,* z wyłączeniem kończącego się znaku null lub [_TRUNCATE](../../c-runtime-library/truncate.md).

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie, kod błędu w przypadku awarii.

|Błąd|Zwracana wartość i **errno**|
|---------------------|------------------------------|
|*mbstr* ma **wartość NULL** i *rozmiarWzdjęty* > 0|**Einval**|
|*wcstr* ma **wartość NULL**|**Einval**|
|Bufor docelowy jest zbyt mały, aby zawierał przekonwertowany ciąg (chyba że *liczba* jest **_TRUNCATE**; patrz Uwagi poniżej)|**Układ ERANGE**|

Jeśli wystąpi którykolwiek z tych warunków, nieprawidłowy wyjątek parametru jest wywoływany zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie jest dozwolone, funkcja zwraca kod błędu i ustawia **errno** jak wskazano w tabeli.

## <a name="remarks"></a>Uwagi

Funkcja **wcstombs_s** konwertuje ciąg szerokich znaków wskazywalnych przez *wcstr* na znaki wielobajtowe przechowywane w buforze wskazywowym przez *mbstr*. Konwersja będzie kontynuowana dla każdego znaku, dopóki nie zostanie spełniony jeden z następujących warunków:

- Napotkany znak o szerokości null

- Napotkany szeroki znak, który nie może zostać przekonwertowany

- Liczba bajtów przechowywanych w buforze *mbstr* jest równa *liczbie*.

Ciąg docelowy jest zawsze zakończony zerem (nawet w przypadku błędu).

Jeśli *count* jest specjalną wartością [_TRUNCATE](../../c-runtime-library/truncate.md), następnie **wcstombs_s** konwertuje tyle ciągu, ile zmieści się w buforze docelowym, pozostawiając jednocześnie miejsce na zerowy terminator. Jeśli ciąg jest obcięty, zwracana wartość jest **STRUNCATE**, a konwersja jest uważana za pomyślną.

Jeśli **wcstombs_s** pomyślnie konwertuje ciąg źródłowy, umieszcza rozmiar w bajtach przekonwertowanego ciągu, w tym terminatora zerowego, *na&#42;pReturnValue* (pod warunkiem, że *wartość zwrotu* nie jest **null).** Dzieje się tak, nawet jeśli *mbstr* argument jest **NULL** i zapewnia sposób określenia rozmiaru buforu wymagane. Należy zauważyć, że jeśli *mbstr* ma **wartość NULL**, *liczba* jest ignorowana.

Jeśli **wcstombs_s** napotka szeroki znak, nie można go przekonwertować na znak wielobajtowy, umieszcza 0 w *&#42;pReturnValue*, ustawia bufor docelowy na pusty ciąg, ustawia **errno** na **EILSEQ**i zwraca **EILSEQ**.

Jeśli sekwencje wskazane przez *wcstr* i *mbstr* nakładają się na siebie, zachowanie **wcstombs_s** jest niezdefiniowane.

> [!IMPORTANT]
> Upewnij się, że *wcstr* i *mbstr* nie nakładają się na siebie, a *liczba ta* poprawnie odzwierciedla liczbę szerokich znaków do konwersji.

**wcstombs_s** używa bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; **_wcstombs_s_l** jest identyczna z **wcstombs,** z tą różnicą, że używa ustawień regionalnych przekazanych zamiast. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia można wywnioskować długość buforu automatycznie (eliminując konieczność określenia argumentu rozmiaru) i mogą automatycznie zastąpić starsze, niezabezpieczone funkcje z ich nowszych, bezpiecznych odpowiedników. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wcstombs_s**|\<>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program ilustruje zachowanie funkcji **wcstombs_s.**

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

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
