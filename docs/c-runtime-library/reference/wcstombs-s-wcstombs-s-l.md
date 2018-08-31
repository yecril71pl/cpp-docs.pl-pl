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
ms.openlocfilehash: 1fec8a41a1c9d1a9d01952a0a72829d2122e0e40
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216980"
---
# <a name="wcstombss-wcstombssl"></a>wcstombs_s, _wcstombs_s_l

Konwertuje sekwencję znaków dwubajtowych do odpowiedniej sekwencji znaków wielobajtowych. Wersja [wcstombs —, _wcstombs_l —](wcstombs-wcstombs-l.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Liczba znaków, konwersji.

*mbstr*<br/>
Adres buforu dla wynikowych konwersji ciągu znaków wielobajtowych.

*sizeInBytes*<br/>
Rozmiar w bajtach *mbstr* buforu.

*wcstr*<br/>
Wskazuje ciąg znaków dwubajtowych do konwersji.

*Liczba*<br/>
Maksymalna liczba bajtów do przechowywania w *mbstr* buforu, nie wliczając kończącego znaku null lub [_TRUNCATE](../../c-runtime-library/truncate.md).

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie, kod błędu.

|Warunek błędu|Zwraca wartość i **errno**|
|---------------------|------------------------------|
|*mbstr* jest **NULL** i *sizeInBytes* > 0|**EINVAL**|
|*wcstr* jest **o wartości NULL**|**EINVAL**|
|Bufora docelowego jest zbyt mała, aby zawierać ciąg przekonwertowany (chyba że *liczba* jest **_TRUNCATE**; zobacz uwagi poniżej)|**ERANGE**|

Jeśli występuje którykolwiek z tych warunków, wyjątek nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, funkcja zwraca kod błędu i ustawia **errno** jak wskazano w tabeli.

## <a name="remarks"></a>Uwagi

**Wcstombs_s —** funkcji konwertuje ciąg znaków dwubajtowych, wskazywana przez *wcstr* na znaki wielobajtowe przechowywane w bufor wskazywany przez *mbstr*. Konwersja będą nadal dla każdego znaku, dopóki nie jest spełniony jeden z następujących warunków:

- Szeroki znak null zostanie osiągnięty.

- Napotkano znak dwubajtowy, który nie może zostać przekonwertowany

- Liczbę bajtów przechowywanych w *mbstr* buforu equals *liczba*.

Ciąg docelowy jest zawsze zakończony znakiem null (nawet w przypadku błędu).

Jeśli *liczba* jest specjalna wartość [_TRUNCATE](../../c-runtime-library/truncate.md), następnie **wcstombs_s —** konwertuje tyle ciągu jako będą dopasowania do buforu docelowego pozostawiając nadal miejsca na wartość null Element przerywający. Jeśli ten ciąg został obcięty, wartość zwracana jest **STRUNCATE**, i konwersja jest uznawany za pomyślny.

Jeśli **wcstombs_s —** pomyślnie konwertuje ciąg źródłowy umieszcza rozmiar w bajtach przekonwertowanego ciągu, łącznie z terminatorem null do  *&#42;pReturnValue* (pod warunkiem  *pReturnValue* nie **NULL**). Dzieje się tak nawet wtedy, gdy *mbstr* argument jest **NULL** i zapewnia możliwość określenia wymagany rozmiar buforu. Należy pamiętać, że jeśli *mbstr* jest **NULL**, *liczba* jest ignorowana.

Jeśli **wcstombs_s —** napotka znakiem dwubajtowym, nie można przekonwertować na znak wielobajtowy umieszcza 0 w  *&#42;pReturnValue*, ustawia bufor docelowy pusty ciąg, ustawia **errno**  do **EILSEQ**i zwraca **EILSEQ**.

Jeśli sekwencji wskazywany przez *wcstr* i *mbstr* zachodziły na siebie, zachowanie **wcstombs_s —** jest niezdefiniowana.

> [!IMPORTANT]
> Upewnij się, że *wcstr* i *mbstr* nie zachodziły na siebie oraz że *liczba* poprawnie odzwierciedla liczbę znaków dwubajtowych do przekonwertowania.

**wcstombs_s —** używa bieżących ustawień regionalnych dla wszelkich zachowań zależnych od ustawień regionalnych; **_wcstombs_s_l —** jest taka sama jak **wcstombs —** z tą różnicą, że używa ustawień regionalnych przekazanych w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując potrzebę określenia argumentu rozmiaru) oraz ich mogą automatycznie zastąpić starsze, niezabezpieczone funkcje ich nowsze, bezpieczne odpowiedniki. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

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
[WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
