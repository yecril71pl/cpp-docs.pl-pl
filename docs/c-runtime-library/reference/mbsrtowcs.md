---
title: mbsrtowcs
ms.date: 11/04/2016
apiname:
- mbsrtowcs
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
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: 2bc0c8c9e2d871b6d1748c42dc02c627244dbf69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331145"
---
# <a name="mbsrtowcs"></a>mbsrtowcs

Konwertuje ciąg znaków wielobajtowych przy bieżących ustawieniach regionalnych odpowiedni ciąg znaków dwubajtowych, z możliwością ponownego uruchomienia w środku znaków wielobajtowych. Bardziej bezpieczna wersja ta funkcja jest dostępna; zobacz [mbsrtowcs_s —](mbsrtowcs-s.md).

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
Adres, aby zapisać w wynikowym przekonwertować ciąg znaku dwubajtowego.

*mbstr*<br/>
Pośredni wskaźnik do lokalizacji ciąg znaków wielobajtowych do przekonwertowania.

*Liczba*<br/>
Maksymalna liczba znaków (nie w bajtach), aby przekonwertować i przechowywać w *wcstr*.

*mbstate*<br/>
Wskaźnik do **mbstate_t** konwersji stan obiektu. Jeśli ta wartość jest wskaźnikiem typu null, jest używany obiekt stanu konwersji statycznej wewnętrznego. Ponieważ wewnętrzny **mbstate_t** obiekt nie jest metodą o bezpiecznych wątkach, zaleca się, że należy zawsze przekazuj parametr własne *mbstate* parametru.

## <a name="return-value"></a>Wartość zwracana

Zwraca liczbę znaków, pomyślnie przekonwertowany, nie wliczając kończącego znaku null, jeśli istnieje. Zwraca (size_t)(-1), jeśli wystąpił błąd i ustawia **errno** do EILSEQ.

## <a name="remarks"></a>Uwagi

**Mbsrtowcs —** funkcji konwertuje ciąg znaków wielobajtowych pośrednio wskazywany przez *mbstr*, do znaków szerokich przechowywanych w bufor wskazywany przez *wcstr*, za pomocą stan konwersji, zawarte w *mbstate*. Konwersja jest kontynuowane dla każdego znaku aż do napotkania albo kończącego null znak wielobajtowy napotkano wielobajtowych sekwencji, która nie odpowiada znakowi przy bieżących ustawieniach regionalnych lub do momentu *liczba* znaki zostały przekonwertowane. Jeśli **mbsrtowcs —** napotka wielobajtowy znak null (\0) przed lub po *liczba* występuje i konwertuje go do 16-bitowych kończącego znaku null i zatrzymuje.

W związku z tym, ciąg znaków dwubajtowych w *wcstr* jest zakończony znakiem null tylko wtedy, gdy **mbsrtowcs —** napotka znak wielobajtowy o wartości null podczas konwersji. Jeśli sekwencji wskazywany przez *mbstr* i *wcstr* zachodziły na siebie, zachowanie **mbsrtowcs —** jest niezdefiniowana. **mbsrtowcs —** jest zależna od kategorii LC_TYPE bieżących ustawień regionalnych.

**Mbsrtowcs —** funkcja różni się od [mbstowcs, _mbstowcs_l —](mbstowcs-mbstowcs-l.md) przez jego restartability. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań tej samej lub innych funkcji ponownego uruchamiania. Podczas korzystania z funkcji ponownego uruchamiania i nonrestartable mieszania, wyniki są niezdefiniowane.  Na przykład, aplikacja powinna używać **mbsrlen** zamiast **mbslen —**, jeśli kolejne wywołanie **mbsrtowcs —** jest używana zamiast **mbstowcs**.

Jeśli *wcstr* nie jest wskaźnikiem typu null, obiekt wskaźnika wskazywany przez *mbstr* przypisano wskaźnikiem typu null, jeśli konwersja została zatrzymana, ponieważ osiągnięto kończącego znaku null. W przeciwnym razie jest przypisany adres przeszłości tylko ostatni znak wielobajtowy jest konwertowany, jeśli istnieje. Dzięki temu wywołania funkcji późniejszego ponownego uruchomienia konwersji, w którym to wywołanie jest zatrzymana.

Jeśli *wcstr* argument jest wskaźnikiem typu null, *liczba* jest ignorowany i **mbsrtowcs —** zwraca wymagany rozmiar znaków dwubitowych, dla ciągu docelowego. Jeśli *mbstate* jest pustym wskaźnikiem, funkcja używa statycznego bez wątkowo wewnętrzny **mbstate_t** konwersji stan obiektu. Jeśli sekwencja znaków *mbstr* nie ma odpowiedniego znaków wielobajtowych reprezentacji znaków, jest zwracana wartość -1 i **errno** ustawiono **EILSEQ**.

Jeśli *mbstr* isa pustym wskaźnikiem, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ta ustawia **errno** do **EINVAL** i zwraca wartość -1.

W języku C++ funkcja ta ma przeciążenia szablonu, które wywołuje nowsze, bezpieczne odpowiednika tej funkcji. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Wyjątki

**Mbsrtowcs —** funkcja jest bezpieczna wielowątkowych, tak długo, jak wywołania funkcji, nie w bieżącym wątku **setlocale** tak długo, jak ta funkcja jest wykonywany i *mbstate* argument nie jest wskaźnikiem typu null.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mbsrtowcs**|\<wchar.h>|

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
