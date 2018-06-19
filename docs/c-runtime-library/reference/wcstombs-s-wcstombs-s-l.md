---
title: wcstombs_s —, _wcstombs_s_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- wcstombs_s function
- string conversion, wide characters
- wide characters, converting
- _wcstombs_s_l function
- wcstombs_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 105f2d33-221a-4f6d-864c-23c1865c42af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f23c4836d178c64590536a809ac5fe6cbbdf8380
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32416504"
---
# <a name="wcstombss-wcstombssl"></a>wcstombs_s, _wcstombs_s_l

Konwertuje odpowiedniej sekwencji znaków wielobajtowych sekwencji znaki dwubajtowe. Wersja [wcstombs —, _wcstombs_l —](wcstombs-wcstombs-l.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Liczba znaków konwersji.

*mbstr*<br/>
Adres buforu dla wynikowy ciąg znaków wielobajtowych przekonwertowany.

*sizeInBytes*<br/>
Wyrażony w bajtach rozmiar *mbstr* buforu.

*wcstr*<br/>
Wskazuje ciąg znaków typu wide do skonwertowania.

*Liczba*<br/>
Maksymalna liczba bajtów, które mają być przechowywane w *mbstr* buforu, nie włączając znak końcowy null lub [_truncate —](../../c-runtime-library/truncate.md).

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie, kod błędu w przypadku awarii.

|Warunek błędu|Wartość zwracana i **errno**|
|---------------------|------------------------------|
|*mbstr* jest **NULL** i *sizeInBytes* > 0.|**EINVAL —**|
|*wcstr* jest **wartości NULL**|**EINVAL —**|
|Bufor docelowy jest zbyt mały, aby pomieścił skonwertowany ciąg (chyba że *liczba* jest **_truncate —**; zobacz uwagi poniżej)|**ERANGE —**|

Jeśli występuje którykolwiek z tych warunków, zgodnie z opisem w wywołaniu wyjątek nieprawidłowy parametr [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może kontynuować, funkcja zwraca błąd o kodzie i ustawia **errno** wymienione w tabeli.

## <a name="remarks"></a>Uwagi

**Wcstombs_s —** funkcja konwertuje ciąg znaki dwubajtowe wskazywana przez *wcstr* do znaków wielobajtowych przechowywane w buforze wskazywana przez *mbstr*. Konwersja będzie kontynuowane dla każdego znaku, dopóki spełniony jest jeden z następujących warunków:

- Napotkano pusty znaków dwubajtowych

- Napotkano znaków dwubajtowych, której nie można przekonwertować

- Liczba bajtów przechowywanych w *mbstr* buforu equals *liczba*.

Ciąg docelowego jest zawsze zerem (nawet w przypadku błędu).

Jeśli *liczba* jest specjalna wartość [_truncate —](../../c-runtime-library/truncate.md), następnie **wcstombs_s —** konwertuje tyle ciągu jako spowoduje mieści się w bufor docelowy, pozostawiając nadal miejsca na wartość null terminator. Jeśli ten ciąg został obcięty, jest zwracana wartość **struncate —**, a konwersja jest uznawany za pomyślny.

Jeśli **wcstombs_s —** pomyślnie konwertuje ciąg źródłowy umieszcza rozmiar w bajtach skonwertowany ciąg, włącznie z terminatorem null do  *&#42;pReturnValue* (pod warunkiem  *pReturnValue* nie jest **NULL**). Dzieje się tak nawet wtedy, gdy *mbstr* argument jest **NULL** i zapewnia możliwość określenia wymagany rozmiar buforu. Należy pamiętać, że jeśli *mbstr* jest **NULL**, *liczba* jest ignorowana.

Jeśli **wcstombs_s —** napotka znaków dwubajtowych nie można przekonwertować znaków wielobajtowych, umieszcza 0 w  *&#42;pReturnValue*, ustawia bufor docelowy na pusty ciąg, ustawia **errno**  do **eilseq —** i zwraca **eilseq —**.

Jeśli sekwencje wskazywana przez *wcstr* i *mbstr* nakładają się zachowanie **wcstombs_s —** jest niezdefiniowana.

> [!IMPORTANT]
> Upewnij się, że *wcstr* i *mbstr* nie pokrywają oraz że *liczba* poprawnie odzwierciedla liczbę znaki dwubajtowe, aby przekonwertować.

**wcstombs_s —** używa bieżące ustawienia regionalne dla dowolnego zachowań zależnych od ustawień regionalnych. **_wcstombs_s_l —** jest taka sama jak **wcstombs —** z tą różnicą, że używa ustawień regionalnych przekazano zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (wyeliminowanie konieczności określania argumentem rozmiaru) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wcstombs_s —**|\<stdlib.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten program ilustruje zachowanie **wcstombs_s —** funkcji.

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
[WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)<br/>
