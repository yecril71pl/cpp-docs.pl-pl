---
title: mbsrtowcs_s
ms.date: 11/04/2016
api_name:
- mbsrtowcs_s
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsrtowcs_s
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
ms.openlocfilehash: d79cceaf923c1da126a1d133a8d2eb8752883457
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952100"
---
# <a name="mbsrtowcs_s"></a>mbsrtowcs_s

Przekonwertuj ciąg znaków wielobajtowych w bieżących ustawieniach regionalnych na swoją reprezentację ciągu znaków szerokich. Wersja [mbsrtowcs](mbsrtowcs.md) z ulepszeniami zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*pReturnValue*<br/>
Liczba konwertowanych znaków.

*wcstr*<br/>
Adres buforu do przechowywania wyniku przekonwertowanego ciągu znaków dwubajtowych.

*sizeInWords*<br/>
Rozmiar *wcstr* w wyrazach (znaki dwubajtowe).

*mbstr*<br/>
Pośredni wskaźnik do lokalizacji ciągu znaków wielobajtowych do przekonwertowania.

*liczbą*<br/>
Maksymalna liczba znaków dwubajtowych do przechowywania w buforze *wcstr* , bez uwzględnienia zakończenia null lub [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Wskaźnik do obiektu stanu konwersji **mbstate_t** . Jeśli ta wartość jest wskaźnikiem typu null, zostanie użyty statyczny obiekt stanu konwersji wewnętrznej. Ponieważ wewnętrzny obiekt **mbstate_t** nie jest bezpieczny wątkowo, zalecamy, aby zawsze przekazać własny parametr *mbstate* .

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli konwersja zakończyła się pomyślnie lub kod błędu w przypadku niepowodzenia.

|Warunek błędu|Wartość zwracana i **errno**|
|---------------------|------------------------------|
|*wcstr* jest wskaźnikiem o wartości null i *sizeInWords* > 0|**EINVAL**|
|*mbstr* jest wskaźnikiem o wartości null|**EINVAL**|
|Ciąg pośrednio wskazywany przez *mbstr* zawiera sekwencję wielobajtową, która nie jest prawidłowa dla bieżących ustawień regionalnych.|**EILSEQ**|
|Bufor docelowy jest zbyt mały, aby zawierał przekonwertowany ciąg (chyba że *licznik* jest **_TRUNCATE**; Aby uzyskać więcej informacji, zobacz uwagi).|**ERANGE**|

Jeśli wystąpi którykolwiek z tych warunków, wyjątek nieprawidłowego parametru jest wywoływany zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, funkcja zwraca kod błędu i ustawia **errno** , jak wskazano w tabeli.

## <a name="remarks"></a>Uwagi

Funkcja **mbsrtowcs_s** konwertuje ciąg znaków wielobajtowych pośrednio wskazany przez *mbstr* na znaki szerokie przechowywane w buforze wskazywanym przez *wcstr*, przy użyciu stanu konwersji zawartego w *mbstate*. Konwersja będzie kontynuowana dla każdego znaku do momentu spełnienia jednego z następujących warunków:

- Napotkano znak wielobajtowy o wartości null

- Napotkano nieprawidłowy znak wielobajtowy

- Liczba znaków dwubajtowych przechowywanych w buforze *wcstr* jest równa *Count*.

Ciąg docelowy *wcstr* jest zawsze zakończony wartością null, nawet w przypadku błędu, chyba że *wcstr* jest wskaźnikiem o wartości null.

Jeśli *Count* jest wartością specjalną [_TRUNCATE](../../c-runtime-library/truncate.md), **mbsrtowcs_s** konwertuje tyle ciągu jako ciąg, jak zmieści się w buforze docelowym, pozostawiając nadal miejsce na terminator o wartości null.

Jeśli **mbsrtowcs_s** pomyślnie konwertuje ciąg źródłowy, umieści rozmiar w postaci dwubajtowej przekonwertowanego ciągu i terminatora o wartości null na  *&#42;pReturnValue*, podany *pReturnValue* nie jest wskaźnikiem o wartości null. Dzieje się tak nawet wtedy, gdy argument *wcstr* jest wskaźnikiem o wartości null i pozwala określić wymagany rozmiar buforu. Należy pamiętać, że jeśli *wcstr* jest wskaźnikiem o wartości null, *Count* jest ignorowany.

Jeśli *wcstr* nie jest pustym wskaźnikiem, obiekt wskaźnika wskazywany przez *mbstr* jest przypisanym wskaźnikiem null, jeśli konwersja została zatrzymana, ponieważ został osiągnięty kończący znak null. W przeciwnym razie jest przypisywany adres tylko do ostatniego przekonwertowanego znaku wielobajtowego (jeśli istnieje). Umożliwia to kolejne wywołanie funkcji w celu ponownego uruchomienia konwersji, w której to wywołanie zostało zatrzymane.

Jeśli *mbstate* jest pustym wskaźnikiem, używany jest obiekt statyczny wewnętrznego stanu konwersji **mbstate_t** . Ponieważ ten wewnętrzny obiekt statyczny nie jest bezpieczny wątkowo, zalecamy przekazanie własnej wartości *mbstate* .

Jeśli **mbsrtowcs_s** napotka znak wielobajtowy, który jest nieprawidłowy w bieżących ustawieniach regionalnych, umieszcza-1 w  *&#42;pReturnValue*, ustawia bufor docelowy *wcstr* do pustego ciągu, ustawia **errno** na **EILSEQ**i zwraca **EILSEQ**.

Jeśli sekwencje wskazywane przez *mbstr* i *wcstr* nakładają się na siebie, zachowanie **mbsrtowcs_s** jest niezdefiniowane. na **mbsrtowcs_s** ma wpływ Kategoria LC_TYPE bieżących ustawień regionalnych.

> [!IMPORTANT]
> Upewnij się, że *wcstr* i *mbstr* nie nakładają się na siebie, i że *licznik* poprawnie odzwierciedla liczbę znaków wielobajtowych do przekonwertowania.

Funkcja **mbsrtowcs_s** różni się od [mbstowcs_s, _mbstowcs_s_l,](mbstowcs-s-mbstowcs-s-l.md) dzięki czemu można jej uruchomić. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań do tych samych lub innych funkcji, które można uruchomić ponownie. Wyniki są niezdefiniowane podczas mieszania użycia funkcji ponownego uruchamiania i nieuruchomionych ponownie. Na przykład aplikacja powinna używać **mbsrlen** zamiast **mbslen**, jeśli podczas kolejnego wywołania **mbsrtowcs_s** jest używana zamiast **mbstowcs_s**.

W C++programie korzystanie z tej funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując wymaganie, aby określić argument rozmiaru) i automatycznie zastąpić starsze, niezabezpieczone funkcje przy użyciu ich nowszych, bezpiecznych odpowiedników. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Wyjątki

Funkcja **mbsrtowcs_s** jest bezpieczna wielowątkowej, jeśli żadna funkcja w bieżącym wątku nie wywołuje metody **setlocaling** , dopóki ta funkcja jest wykonywana, a argument *mbstate* nie jest wskaźnikiem typu null.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mbsrtowcs_s**|\<WCHAR. h >|

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
