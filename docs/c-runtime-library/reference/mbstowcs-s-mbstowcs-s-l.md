---
title: mbstowcs_s, _mbstowcs_s_l
ms.date: 4/2/2020
api_name:
- _mbstowcs_s_l
- mbstowcs_s
- _o__mbstowcs_s_l
- _o_mbstowcs_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbstowcs_s_l
- mbstowcs_s
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
ms.openlocfilehash: 4a6e86e1122a7392862fa34a59042c32560fd69d
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915454"
---
# <a name="mbstowcs_s-_mbstowcs_s_l"></a>mbstowcs_s, _mbstowcs_s_l

Konwertuje sekwencję znaków wielobajtowych na odpowiadającą sekwencję szerokich znaków. Wersje programu [mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Liczba konwertowanych znaków.

*wcstr*<br/>
Adres buforu dla obliczonego ciągu znaków dwubajtowych.

*sizeInWords*<br/>
Rozmiar buforu *wcstr* w słowach.

*mbstr*<br/>
Adres sekwencji znaków wielobajtowych zakończony wartością null.

*liczbą*<br/>
Maksymalna liczba znaków dwubajtowych do przechowywania w buforze *wcstr* , bez uwzględnienia kończących wartości null lub [_TRUNCATE](../../c-runtime-library/truncate.md).

*locale*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie, kod błędu w przypadku niepowodzenia.

|Błąd|Wartość zwracana i **errno**|
|---------------------|------------------------------|
|*wcstr* ma **wartość NULL** i *sizeInWords* > 0|**EINVAL**|
|*mbstr* ma **wartość null**|**EINVAL**|
|Bufor docelowy jest zbyt mały, aby zawierał przekonwertowany ciąg (chyba że *licznik* jest **_TRUNCATE**; Zobacz uwagi poniżej)|**ERANGE**|
|*wcstr* nie ma **wartości null** i *sizeInWords* = = 0|**EINVAL**|

Jeśli wystąpi którykolwiek z tych warunków, wyjątek nieprawidłowego parametru jest wywoływany zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, funkcja zwraca kod błędu i ustawia **errno** , jak wskazano w tabeli.

## <a name="remarks"></a>Uwagi

Funkcja **mbstowcs_s** konwertuje ciąg znaków wielobajtowych wskazanych przez *mbstr* na znaki szerokie przechowywane w buforze wskazywanym przez *wcstr*. Konwersja będzie kontynuowana dla każdego znaku do momentu spełnienia jednego z następujących warunków:

- Napotkano znak wielobajtowy o wartości null

- Napotkano nieprawidłowy znak wielobajtowy

- Liczba znaków dwubajtowych przechowywanych w buforze *wcstr* jest równa *Count*.

Ciąg docelowy jest zawsze zakończony wartością null (nawet w przypadku błędu).

Jeśli *Liczba* jest wartością specjalną [_TRUNCATE](../../c-runtime-library/truncate.md), wówczas **mbstowcs_s** konwertuje tyle ciągu jako ciąg, jak zmieści się w buforze docelowym, pozostawiając nadal miejsce na terminator o wartości null.

Jeśli **mbstowcs_s** pomyślnie przekonwertuje ciąg źródłowy, umieści rozmiar w postaci dwubajtowej przekonwertowanego ciągu, łącznie z terminatorem null, na *&#42;PReturnValue* (podany *pReturnValue* nie ma **wartości null**). Dzieje się tak nawet wtedy, gdy argument *wcstr* ma **wartość null** i umożliwia określenie wymaganego rozmiaru buforu. Należy pamiętać, że jeśli *wcstr* ma **wartość null**, *Count* jest ignorowany, a *sizeInWords* musi mieć wartość 0.

Jeśli **mbstowcs_s** napotka nieprawidłowy znak wielobajtowy, umieszcza 0 w *&#42;pReturnValue*, ustawia bufor docelowy na pusty ciąg, ustawia **errno** na **EILSEQ**i zwraca **EILSEQ**.

Jeśli sekwencje wskazywane przez *mbstr* i *wcstr* nakładają się na siebie, zachowanie **mbstowcs_s** jest niezdefiniowane.

> [!IMPORTANT]
> Upewnij się, że *wcstr* i *mbstr* nie nakładają się na siebie, i że *licznik* poprawnie odzwierciedla liczbę znaków wielobajtowych do przekonwertowania.

**mbstowcs_s** używa bieżących ustawień regionalnych dla wszelkich zachowań zależnych od ustawień regionalnych; **_mbstowcs_s_l** jest identyczny, z tą różnicą, że w zamian korzysta z przekazaną ustawieniami regionalnymi. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując konieczność określenia argumentu rozmiaru) i mogą automatycznie zastąpić starsze, niezabezpieczone funkcje z ich nowszymi, bezpiecznymi odpowiednikami. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mbstowcs_s**|\<STDLIB. h>|
|**_mbstowcs_s_l**|\<STDLIB. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienie](../../c-runtime-library/locale.md)<br/>
[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
