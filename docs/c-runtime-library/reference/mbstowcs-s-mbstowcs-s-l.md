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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 07d694a7430f23e2f9600a5d2b147bcee2ef0e09
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338809"
---
# <a name="mbstowcs_s-_mbstowcs_s_l"></a>mbstowcs_s, _mbstowcs_s_l

Konwertuje sekwencję znaków wielobajtowych na odpowiednią sekwencję znaków szerokich. Wersje [mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*pZawąkaWartość*<br/>
Liczba przekonwertowanych znaków.

*wcstr*<br/>
Adres buforu dla wynikowego przekonwertowanego szerokiego ciągu znaków.

*rozmiarWłasna*<br/>
Rozmiar buforu *wcstr* w słowach.

*mbstr*<br/>
Adres sekwencji znaków wielobajtowych zakończonych wartościami null.

*Liczba*<br/>
Maksymalna liczba znaków szerokich do przechowywania w buforze *wcstr,* z wyłączeniem kończącej się wartości null lub [_TRUNCATE](../../c-runtime-library/truncate.md).

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie, kod błędu w przypadku awarii.

|Błąd|Zwracana wartość i **errno**|
|---------------------|------------------------------|
|*wcstr* jest **NULL** i *sizeInWords* > 0|**Einval**|
|*mbstr* ma **wartość NULL**|**Einval**|
|Bufor docelowy jest zbyt mały, aby zawierał przekonwertowany ciąg (chyba że *liczba* jest **_TRUNCATE**; patrz Uwagi poniżej)|**Układ ERANGE**|
|*wcstr* nie jest **NULL** i *sizeInWords* == 0|**Einval**|

Jeśli wystąpi którykolwiek z tych warunków, nieprawidłowy wyjątek parametru jest wywoływany zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie jest dozwolone, funkcja zwraca kod błędu i ustawia **errno** jak wskazano w tabeli.

## <a name="remarks"></a>Uwagi

Funkcja **mbstowcs_s** konwertuje ciąg znaków wielobajtowych wskazywalnych przez *mbstr* na szerokie znaki przechowywane w buforze wskazywowym przez *wcstr*. Konwersja będzie kontynuowana dla każdego znaku, dopóki nie zostanie spełniony jeden z następujących warunków:

- Napotkany znak null wielobajtowy

- Napotkany nieprawidłowy znak wielobajtowy

- Liczba szerokich znaków przechowywanych w buforze *wcstr* jest równa *liczbie*.

Ciąg docelowy jest zawsze zakończony zerem (nawet w przypadku błędu).

Jeśli *count* jest specjalną wartością [_TRUNCATE](../../c-runtime-library/truncate.md), następnie **mbstowcs_s** konwertuje tyle ciągu, ile zmieści się w buforze docelowym, pozostawiając jednocześnie miejsce na zerowy terminator.

Jeśli **mbstowcs_s** pomyślnie konwertuje ciąg źródłowy, umieszcza rozmiar w szerokich znakach przekonwertowanego ciągu, w tym terminatora zerowego, na *&#42;pReturnValue* (pod warunkiem, że *wartość zwrotu* nie jest **null).** Dzieje się tak, nawet jeśli *argument wcstr* jest **NULL** i zapewnia sposób określenia rozmiaru buforu wymagane. Należy zauważyć, że jeśli *wcstr* jest **NULL**, *liczba* jest ignorowana, a *sizeInWords* musi być 0.

Jeśli **mbstowcs_s** napotka nieprawidłowy znak wielobajtowy, umieszcza 0 w *&#42;pReturnValue*, ustawia bufor docelowy na pusty ciąg, ustawia **errno** na **EILSEQ**i zwraca **EILSEQ**.

Jeśli sekwencje wskazane przez *mbstr* i *wcstr* pokrywają się, zachowanie **mbstowcs_s** jest niezdefiniowana.

> [!IMPORTANT]
> Upewnij się, że *wcstr* i *mbstr* nie nakładają się na siebie, a *liczba ta* poprawnie odzwierciedla liczbę znaków wielobajtowych do konwersji.

**mbstowcs_s** używa bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; **_mbstowcs_s_l** jest identyczna, z tą różnicą, że używa ustawień regionalnych przekazanych zamiast. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia można wywnioskować długość buforu automatycznie (eliminując konieczność określenia argumentu rozmiaru) i mogą automatycznie zastąpić starsze, niezabezpieczone funkcje z ich nowszych, bezpiecznych odpowiedników. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mbstowcs_s**|\<>|
|**_mbstowcs_s_l**|\<>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Multibytetowidechar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
