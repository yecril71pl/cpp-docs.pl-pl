---
title: mbsrtowcs
ms.date: 11/04/2016
api_name:
- mbsrtowcs
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
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: de7b25ea8a520dfe2c9cb26ec8989624b670dcb9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952048"
---
# <a name="mbsrtowcs"></a>mbsrtowcs

Konwertuje ciąg znaków wielobajtowych w bieżących ustawieniach regionalnych na odpowiadający ciąg znaków szerokiego, z możliwością ponownego uruchomienia w środku znaku wielobajtowego. Dostępna jest bezpieczniejsza wersja tej funkcji; Zobacz [mbsrtowcs_s](mbsrtowcs-s.md).

## <a name="syntax"></a>Składnia

```C
size_t mbsrtowcs(
   wchar_t *wcstr,
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t mbsrtowcs(
   wchar_t (&wcstr)[size],
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*wcstr*<br/>
Adres do przechowywania wyniku przekonwertowanego ciągu znaków dwubajtowych.

*mbstr*<br/>
Pośredni wskaźnik do lokalizacji ciągu znaków wielobajtowych do przekonwertowania.

*liczbą*<br/>
Maksymalna liczba znaków (nie bajtów) do przekonwertowania i zapisania w *wcstr*.

*mbstate*<br/>
Wskaźnik do obiektu stanu konwersji **mbstate_t** . Jeśli ta wartość jest wskaźnikiem typu null, zostanie użyty statyczny obiekt stanu konwersji wewnętrznej. Ponieważ wewnętrzny obiekt **mbstate_t** nie jest bezpieczny wątkowo, zalecamy, aby zawsze przekazać własny parametr *mbstate* .

## <a name="return-value"></a>Wartość zwracana

Zwraca liczbę znaków, które zostały pomyślnie przekonwertowane, bez uwzględnienia kończącego znaku null, jeśli istnieje. Zwraca (size_t) (-1), jeśli wystąpił błąd, i ustawia **errno** na EILSEQ.

## <a name="remarks"></a>Uwagi

Funkcja **mbsrtowcs** konwertuje ciąg znaków wielobajtowych pośrednio wskazany przez *mbstr*, na znaki szerokie przechowywane w buforze wskazywanym przez *wcstr*, przy użyciu stanu konwersji zawartego w *mbstate*. Konwersja będzie kontynuowana dla każdego znaku, dopóki nie zostanie osiągnięty kończący się znak wielobajtowy o wartości null, zostanie wykryta sekwencja wielobajtowa, która nie odpowiada prawidłowemu znakowi w bieżących ustawieniach regionalnych lub dopóki nie zostanie *wyliczona liczba* znaków skonwertowana. Jeśli **mbsrtowcs** napotka znak wielobajtowy o wartości null (' \ 0 ') przed lub *w czasie* występowania, konwertuje go na 16-bitowy kończący znak null i zostaje zatrzymany.

W ten sposób ciąg znaków dwubajtowych w *wcstr* jest zakończony wartością null tylko wtedy, gdy **mbsrtowcs** napotka znak null o wartości wieloróżnej podczas konwersji. Jeśli sekwencje wskazywane przez *mbstr* i *wcstr* nakładają się na siebie, zachowanie **mbsrtowcs** jest niezdefiniowane. na **mbsrtowcs** ma wpływ Kategoria LC_TYPE bieżących ustawień regionalnych.

Funkcja **mbsrtowcs** różni się od [mbstowcs, _mbstowcs_l,](mbstowcs-mbstowcs-l.md) dzięki czemu można jej uruchomić. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań do tych samych lub innych funkcji, które można uruchomić ponownie. Wyniki są niezdefiniowane podczas mieszania użycia funkcji ponownego uruchamiania i nieuruchomionych ponownie.  Na przykład aplikacja powinna używać **mbsrlen** zamiast **mbslen**, jeśli podczas kolejnego wywołania **mbsrtowcs** jest używana zamiast **mbstowcs**.

Jeśli *wcstr* nie jest pustym wskaźnikiem, obiekt wskaźnika wskazywany przez *mbstr* jest przypisanym wskaźnikiem null, jeśli konwersja została zatrzymana, ponieważ został osiągnięty kończący znak null. W przeciwnym razie jest przypisywany adres tylko do ostatniego przekonwertowanego znaku wielobajtowego (jeśli istnieje). Umożliwia to kolejne wywołanie funkcji w celu ponownego uruchomienia konwersji, w której to wywołanie zostało zatrzymane.

Jeśli argument *wcstr* jest wskaźnikiem o wartości null, argument *Count* jest ignorowany, a **mbsrtowcs** zwraca wymagany rozmiar w postaci znaków dwubajtowych dla ciągu docelowego. Jeśli *mbstate* jest wskaźnikiem o wartości null, funkcja używa obiektu **stanu konwersji** statycznej nieopartego na wątku, który jest bezwątkowy. Jeśli *mbstr* sekwencji znaków nie ma odpowiadającej reprezentacji znaków wielobajtowych, zwracana jest wartość-1, a **errno** jest ustawiona na **EILSEQ**.

Jeśli *mbstr* pusty wskaźnik "ISA", zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, ta funkcja ustawia **errno** na **EINVAL** i zwraca wartość-1.

W C++programie ta funkcja ma Przeciążenie szablonu, które wywołuje nowszy, bezpieczny odpowiednik tej funkcji. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Wyjątki

Funkcja **mbsrtowcs** jest wielowątkowej bezpieczna, dopóki żadna funkcja w bieżącym wątku nie wywołuje metody **setlocaling** , dopóki ta funkcja jest wykonywana, a argument *mbstate* nie jest wskaźnikiem typu null.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mbsrtowcs**|\<WCHAR. h >|

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
