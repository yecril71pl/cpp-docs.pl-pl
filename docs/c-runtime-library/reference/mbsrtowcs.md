---
title: mbsrtowcs
ms.date: 4/2/2020
api_name:
- mbsrtowcs
- _o_mbsrtowcs
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
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: 509046e1c55d89cd78b09076838983691423a1ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338882"
---
# <a name="mbsrtowcs"></a>mbsrtowcs

Konwertuje ciąg znaków wielobajtowych w bieżącym ustawieniach regionalnych na odpowiedni ciąg znaków szerokich, z możliwością ponownego uruchamiania w środku znaku wielobajtowego. Dostępna jest bezpieczniejsza wersja tej funkcji; patrz [mbsrtowcs_s](mbsrtowcs-s.md).

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
Adres do przechowywania wynikowego przekonwertowanego szerokiego ciągu znaków.

*mbstr*<br/>
Wskaźnik pośredni do lokalizacji ciągu znaków wielobajtowego do konwersji.

*Liczba*<br/>
Maksymalna liczba znaków (nie bajtów) do konwersji i przechowywania w *wcstr*.

*mbstate*<br/>
Wskaźnik do obiektu stanu konwersji **mbstate_t.** Jeśli ta wartość jest wskaźnikiem zerowym, używany jest statyczny obiekt stanu konwersji wewnętrznej. Ponieważ obiekt **mbstate_t** wewnętrznej nie jest bezpieczny dla wątków, zaleca się, aby zawsze przekazywać własny parametr *mbstate.*

## <a name="return-value"></a>Wartość zwracana

Zwraca liczbę znaków pomyślnie przekonwertowanych, z wyłączeniem kończącego się znaku null, jeśli istnieje. Zwraca (size_t)(-1), jeśli wystąpił błąd, i ustawia **errno** na EILSEQ.

## <a name="remarks"></a>Uwagi

Funkcja **mbsrtowcs** konwertuje ciąg znaków wielobajtowych pośrednio wskazywana przez *mbstr,* na szerokie znaki przechowywane w buforze wskazywana przez *wcstr,* przy użyciu stanu konwersji zawartego w *mbstate*. Konwersja jest kontynuowana dla każdego znaku, dopóki nie zostanie napotkany kończący się znak wielobajtowy, sekwencja wielobajtowa, która nie odpowiada prawidłowemu znakowi w bieżących ustawieniach regionalnych, lub dopóki nie zostanie przekonwertowana *liczba* znaków. Jeśli **mbsrtowcs** napotka znak null wielobajtowy ("\0") przed lub po wystąpieniu *licznika,* konwertuje go na 16-bitowy kończący się znak null i zatrzymuje.

W związku z tym ciąg znaków szeroki w *wcstr* jest zakończony zerem tylko wtedy, **gdy mbsrtowcs** napotka znak zerowy wielobajtowy podczas konwersji. Jeśli sekwencje wskazane przez *mbstr* i *wcstr* nakładają się na siebie, zachowanie **mbsrtowcs** jest niezdefiniowana. **mbsrtowcs** ma wpływ na kategorię LC_TYPE bieżących ustawień regionalnych.

Funkcja **mbsrtowcs** różni się od [mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md) przez jego możliwości ponownego uruchomienia. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań do tej samej lub innych funkcji, które można ponownie uruchomić. Wyniki są niezdefiniowane podczas mieszania użycia funkcji, które można ponownie uruchomić i niepodważalne.  Na przykład aplikacja powinna używać **mbsrlen** zamiast **mbslen**, jeśli zamiast mbsrtowcs **mbstowcs**jest używane kolejne wywołanie **mbsrtowcs.**

Jeśli *wcstr* nie jest wskaźnikiem null, obiekt wskaźnika wskazywany przez *mbstr* jest przypisywany wskaźnik null, jeśli konwersja została zatrzymana, ponieważ osiągnięto kończący się znak null. W przeciwnym razie jest przypisany adres tuż obok ostatniego znaku wielobajtowego przekonwertowane, jeśli istnieje. Dzięki temu kolejne wywołanie funkcji, aby ponownie uruchomić konwersję, gdzie to wywołanie zatrzymane.

Jeśli argument *wcstr* jest wskaźnikiem null, argument *count* jest ignorowany, a **mbsrtowcs** zwraca wymagany rozmiar w szerokich znakach dla ciągu docelowego. Jeśli *mbstate* jest wskaźnikiem null, funkcja używa nie-wątku bezpieczne statyczne **mbstate_t** obiekt stanu konwersji. Jeśli sekwencja znaków *mbstr* nie ma odpowiedniej reprezentacji znaków wielobajtowych, zwracana jest liczba -1, a **errno** jest ustawione na **EILSEQ**.

Jeśli *mbstr* isa null wskaźnik, nieprawidłowy program obsługi parametrów jest wywoływany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, ta funkcja ustawia **errno** na **EINVAL** i zwraca -1.

W języku C++ ta funkcja ma przeciążenie szablonu, który wywołuje nowszy, bezpieczny odpowiednik tej funkcji. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="exceptions"></a>Wyjątki

Funkcja **mbsrtowcs** jest wielowątkowa, o ile żadna funkcja w bieżącym wątku wywołuje **setlocale,** o ile ta funkcja jest wykonywana, a argument *mbstate* nie jest wskaźnikiem null.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mbsrtowcs**|\<wchar.h>|

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
