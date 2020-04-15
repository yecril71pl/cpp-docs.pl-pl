---
title: mbsrtowcs_s
ms.date: 4/2/2020
api_name:
- mbsrtowcs_s
- _o_mbsrtowcs_s
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
- mbsrtowcs_s
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
ms.openlocfilehash: 62ae534e8080b74ada49cca005811a049055cb65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338901"
---
# <a name="mbsrtowcs_s"></a>mbsrtowcs_s

Konwertuj ciąg znaków wielobajtowych w bieżącym otoczeniu na jego szeroką reprezentację ciągu znaków. Wersja [mbsrtowcs](mbsrtowcs.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t * wcstr,
   size_t sizeInWords,
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
);
template <size_t size>
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t (&wcstr)[size],
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*pZawąkaWartość*<br/>
Liczba przekonwertowanych znaków.

*wcstr*<br/>
Adres buforu do przechowywania wynikowego przekonwertowanego szerokiego ciągu znaków.

*rozmiarWłasna*<br/>
Rozmiar *wcstr* w słowach (znaki szerokie).

*mbstr*<br/>
Wskaźnik pośredni do lokalizacji wielobajtowego ciągu znaków, który ma zostać przekonwertowany.

*Liczba*<br/>
Maksymalna liczba znaków szerokich do przechowywania w buforze *wcstr,* z wyłączeniem kończącej się wartości null lub [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Wskaźnik do obiektu stanu konwersji **mbstate_t.** Jeśli ta wartość jest wskaźnikiem zerowym, używany jest statyczny obiekt stanu konwersji wewnętrznej. Ponieważ obiekt **mbstate_t** wewnętrznej nie jest bezpieczny dla wątków, zaleca się, aby zawsze przekazywać własny parametr *mbstate.*

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli konwersja zakończy się pomyślnie, lub kod błędu w przypadku awarii.

|Błąd|Zwracana wartość i **errno**|
|---------------------|------------------------------|
|*wcstr* jest wskaźnikiem null i *sizeInWords* > 0|**Einval**|
|*mbstr* jest wskaźnikiem zerowym|**Einval**|
|Ciąg pośrednio wskazywana przez *mbstr* zawiera sekwencję wielobajtową, która nie jest prawidłowa dla bieżących ustawień regionalnych.|**OKRĘG WYBORCZY EILSEQ**|
|Bufor docelowy jest zbyt mały, aby zawierał przekonwertowany ciąg (chyba że *liczba* jest **_TRUNCATE**; aby uzyskać więcej informacji, zobacz Uwagi)|**Układ ERANGE**|

Jeśli wystąpi którykolwiek z tych warunków, nieprawidłowy wyjątek parametru jest wywoływany zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie jest dozwolone, funkcja zwraca kod błędu i ustawia **errno** jak wskazano w tabeli.

## <a name="remarks"></a>Uwagi

Funkcja **mbsrtowcs_s** konwertuje ciąg znaków wielobajtowych pośrednio wskazywana przez *mbstr* na szerokie znaki przechowywane w buforze wskazywana przez *wcstr,* przy użyciu stanu konwersji zawartego w *mbstate*. Konwersja będzie kontynuowana dla każdego znaku, dopóki nie zostanie spełniony jeden z następujących warunków:

- Napotkany znak null wielobajtowy

- Napotkany nieprawidłowy znak wielobajtowy

- Liczba szerokich znaków przechowywanych w buforze *wcstr* jest równa *liczbie*.

Ciąg docelowy *wcstr* jest zawsze zakończony zerem, nawet w przypadku błędu, chyba że *wcstr* jest wskaźnikiem null.

Jeśli *count* jest specjalną wartością [_TRUNCATE](../../c-runtime-library/truncate.md), **mbsrtowcs_s** konwertuje tyle ciągu, ile zmieści się w buforze docelowym, pozostawiając jednocześnie miejsce na terminator zerowy.

Jeśli **mbsrtowcs_s** pomyślnie konwertuje ciąg źródłowy, umieszcza rozmiar w szerokich znaków przekonwertowanego ciągu i null terminator do *&#42;pReturnValue*, pod warunkiem *pReturnValue* nie jest wskaźnik null. Dzieje się tak, nawet jeśli *argument wcstr* jest wskaźnikiem null i pozwala określić rozmiar buforu wymagane. Należy zauważyć, że jeśli *wcstr* jest wskaźnik null, *liczba* jest ignorowana.

Jeśli *wcstr* nie jest wskaźnikiem null, obiekt wskaźnika wskazywany przez *mbstr* jest przypisywany wskaźnik null, jeśli konwersja została zatrzymana, ponieważ osiągnięto kończący się znak null. W przeciwnym razie jest przypisany adres tuż obok ostatniego znaku wielobajtowego przekonwertowane, jeśli istnieje. Dzięki temu kolejne wywołanie funkcji, aby ponownie uruchomić konwersję, gdzie to wywołanie zatrzymane.

Jeśli *mbstate* jest wskaźnikiem zerowym, używana jest wewnętrzna **mbstate_t** obiekt statyczny stanu konwersji biblioteki. Ponieważ ten wewnętrzny obiekt statyczny nie jest bezpieczny dla wątków, zaleca się przekazanie własnej wartości *mbstate.*

Jeśli **mbsrtowcs_s** napotka znak wielobajtowy, który nie jest prawidłowy w bieżącym ustawieniach regionalnych, umieszcza -1 w *&#42;pReturnValue*, ustawia bufor docelowy *wcstr* na pusty ciąg, ustawia **errno** na **EILSEQ**i zwraca **EILSEQ**.

Jeśli sekwencje wskazane przez *mbstr* i *wcstr* pokrywają się, zachowanie **mbsrtowcs_s** jest niezdefiniowana. **mbsrtowcs_s** ma wpływ LC_TYPE kategorii bieżących ustawień regionalnych.

> [!IMPORTANT]
> Upewnij się, że *wcstr* i *mbstr* nie nakładają się na siebie, a *liczba ta* poprawnie odzwierciedla liczbę znaków wielobajtowych do konwersji.

Funkcja **mbsrtowcs_s** różni się od [mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md) możliwością ponownego uruchomienia. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań do tej samej lub innych funkcji, które można ponownie uruchomić. Wyniki są niezdefiniowane podczas mieszania użycia funkcji, które można ponownie uruchomić i niepodważalne. Na przykład aplikacja powinna używać **mbsrlen** zamiast **mbslen**, jeśli zamiast **mbstowcs_s**jest używane kolejne wywołanie **mbsrtowcs_s.**

W języku C++ użycie tej funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia można wywnioskować długość buforu automatycznie (eliminując wymóg, aby określić argument rozmiaru) i mogą automatycznie zastąpić starsze, niezabezpieczone funkcje przy użyciu ich nowszych, bezpiecznych odpowiedników. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="exceptions"></a>Wyjątki

Funkcja **mbsrtowcs_s** jest wielowątkowa, jeśli żadna funkcja w bieżącym wątku wywołuje **setlocale,** o ile ta funkcja jest wykonywana, a argument *mbstate* nie jest wskaźnikiem null.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mbsrtowcs_s**|\<wchar.h>|

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
