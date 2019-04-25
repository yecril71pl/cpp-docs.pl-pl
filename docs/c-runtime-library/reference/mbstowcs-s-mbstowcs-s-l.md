---
title: mbstowcs_s, _mbstowcs_s_l
ms.date: 11/04/2016
apiname:
- _mbstowcs_s_l
- mbstowcs_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbstowcs_s_l
- mbstowcs_s
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
ms.openlocfilehash: 18af20b5722364ea306daebdcb77f5771d8ea2b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331160"
---
# <a name="mbstowcss-mbstowcssl"></a>mbstowcs_s, _mbstowcs_s_l

Konwertuje sekwencję znaków wielobajtowych do odpowiedniej sekwencji znaków dwubajtowych. Wersje [mbstowcs, _mbstowcs_l —](mbstowcs-mbstowcs-l.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count
);
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Liczba znaków, konwersji.

*wcstr*<br/>
Adres buforu dla wynikowy ciąg przekonwertowany znak dwubajtowy.

*sizeInWords*<br/>
Rozmiar *wcstr* buforu w słowach.

*mbstr*<br/>
Adres sekwencji null zakończone znaków wielobajtowych.

*Liczba*<br/>
Maksymalna liczba znaków dwubajtowych do przechowywania w *wcstr* buforu, nie wliczając końcowej wartości null lub [_TRUNCATE](../../c-runtime-library/truncate.md).

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie, kod błędu.

|Warunek błędu|Zwraca wartość i **errno**|
|---------------------|------------------------------|
|*wcstr* jest **NULL** i *sizeInWords* > 0|**EINVAL**|
|*mbstr* jest **o wartości NULL**|**EINVAL**|
|Bufora docelowego jest zbyt mała, aby zawierać ciąg przekonwertowany (chyba że *liczba* jest **_TRUNCATE**; zobacz uwagi poniżej)|**ERANGE**|
|*wcstr* nie **NULL** i *sizeInWords* == 0|**EINVAL**|

Jeśli występuje którykolwiek z tych warunków, wyjątek nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, funkcja zwraca kod błędu i ustawia **errno** jak wskazano w tabeli.

## <a name="remarks"></a>Uwagi

**Mbstowcs_s —** funkcji konwertuje ciąg znaków wielobajtowych wskazywany przez *mbstr* do znaków szerokich przechowywanych w bufor wskazywany przez *wcstr*. Konwersja będą nadal dla każdego znaku, dopóki nie jest spełniony jeden z następujących warunków:

- Wielobajtowy znak null zostanie osiągnięty.

- Napotkano nieprawidłowy znak wielobajtowy

- Liczba znaków szerokich przechowywanych w *wcstr* buforu equals *liczba*.

Ciąg docelowy jest zawsze zakończony znakiem null (nawet w przypadku błędu).

Jeśli *liczba* jest specjalna wartość [_TRUNCATE](../../c-runtime-library/truncate.md), następnie **mbstowcs_s —** konwertuje tyle ciągu jako będą dopasowania do buforu docelowego pozostawiając nadal miejsca na wartość null Element przerywający.

Jeśli **mbstowcs_s —** pomyślnie konwertuje ciąg źródłowy umieszcza rozmiar w znaki dwubajtowe przekonwertowanego ciągu, łącznie z terminatorem null do  *&#42;pReturnValue* (pod warunkiem *pReturnValue* nie **NULL**). Dzieje się tak nawet wtedy, gdy *wcstr* argument jest **NULL** i zapewnia możliwość określenia wymagany rozmiar buforu. Należy pamiętać, że jeśli *wcstr* jest **NULL**, *liczba* jest ignorowany i *sizeInWords* musi mieć wartość 0.

Jeśli **mbstowcs_s —** napotka nieprawidłowy znak wielobajtowy umieszcza 0 w  *&#42;pReturnValue*, ustawia bufor docelowy pusty ciąg, ustawia **errno** do  **EILSEQ**i zwraca **EILSEQ**.

Jeśli sekwencji wskazywany przez *mbstr* i *wcstr* zachodziły na siebie, zachowanie **mbstowcs_s —** jest niezdefiniowana.

> [!IMPORTANT]
> Upewnij się, że *wcstr* i *mbstr* nie zachodziły na siebie oraz że *liczba* poprawnie odzwierciedla liczbę znaków wielobajtowych do przekonwertowania.

**mbstowcs_s —** używa bieżących ustawień regionalnych dla wszelkich zachowań zależnych od ustawień regionalnych; **_mbstowcs_s_l —** jest identyczna, z tą różnicą, że używa ustawień regionalnych przekazanych w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując potrzebę określenia argumentu rozmiaru) oraz ich mogą automatycznie zastąpić starsze, niezabezpieczone funkcje ich nowsze, bezpieczne odpowiedniki. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mbstowcs_s**|\<stdlib.h>|
|**_mbstowcs_s_l**|\<stdlib.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
