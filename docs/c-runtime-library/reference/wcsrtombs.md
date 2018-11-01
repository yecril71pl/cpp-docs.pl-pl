---
title: wcsrtombs
ms.date: 11/04/2016
apiname:
- wcsrtombs
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
- wcsrtombs
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
ms.openlocfilehash: 46ef195ec4685c327c4b5951ec44e5c363214b59
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494422"
---
# <a name="wcsrtombs"></a>wcsrtombs

Konwertuj ciąg znaku dwubajtowego na jego reprezentację ciągu znaków wielobajtowych. Bardziej bezpieczna wersja ta funkcja jest dostępna; zobacz [wcsrtombs_s —](wcsrtombs-s.md).

## <a name="syntax"></a>Składnia

```C
size_t wcsrtombs(
   char *mbstr,
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcsrtombs(
   char (&mbstr)[size],
   const wchar_t **wcstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*mbstr*<br/>
Wartość wynikowa konwersji ciągu znaków wielobajtowych adres lokalizacji.

*wcstr*<br/>
Pośrednio wskazuje lokalizację ciąg znaków dwubajtowych do konwersji.

*Liczba*<br/>
Liczba znaków, które ma zostać przekonwertowany.

*mbstate*<br/>
Wskaźnik do **mbstate_t** konwersji stan obiektu.

## <a name="return-value"></a>Wartość zwracana

Zwraca liczbę bajtów pomyślnie przekonwertowany, nie wliczając null zakończenie bajt typu null (jeśli istnieje), w przeciwnym razie -1, jeśli wystąpił błąd.

## <a name="remarks"></a>Uwagi

**Wcsrtombs —** funkcji konwertuje ciąg znaków dwubajtowych, począwszy od stanu określonej konwersji zawarte w *mbstate*, ze wskazanym w wartości pośrednich *wcstr*, pod adres *mbstr*. Konwersja będą nadal dla każdego znaku, aż do: po napotkaniu o wartości null zakończenie znaków dwubajtowych, po napotkaniu bez odpowiedniego znaku lub gdy następny znak spowoduje przekroczenie limitu zawarte w *liczba*. Jeśli **wcsrtombs —** napotka znaków dwubajtowych znakiem null (L '\0'), przed lub po *liczba* występuje i konwertuje ją do 8-bitową 0 i kończy działanie.

W związku z tym ciągu znaków wielobajtowych *mbstr* jest zakończony znakiem null tylko wtedy, gdy **wcsrtombs —** napotka znaku dwubajtowego znaku null podczas konwersji. Jeśli sekwencji wskazywany przez *wcstr* i *mbstr* zachodziły na siebie, zachowanie **wcsrtombs —** jest niezdefiniowana. **wcsrtombs —** jest zależna od kategorii LC_TYPE bieżących ustawień regionalnych.

**Wcsrtombs —** funkcja różni się od [wcstombs —, _wcstombs_l —](wcstombs-wcstombs-l.md) przez jego restartability. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań tej samej lub innych funkcji ponownego uruchamiania. Podczas korzystania z funkcji ponownego uruchamiania i nonrestartable mieszania, wyniki są niezdefiniowane.  Na przykład, aplikacja będzie używać **wcsrlen** zamiast **wcsnlen —**, jeśli kolejne wywołanie **wcsrtombs —** były używane zamiast **wcstombs —**.

Jeśli *mbstr* argument jest **NULL**, **wcsrtombs —** zwraca wymagany rozmiar w bajtach ciągu docelowego. Jeśli *mbstate* ma wartość null, wewnętrzny **mbstate_t** stan konwersji jest używany. Jeśli sekwencja znaków *wchar* nie ma odpowiedniego znaków wielobajtowych reprezentacji znaków, jest zwracana wartość -1 i **errno** ustawiono **EILSEQ**.

W języku C++ funkcja ta ma przeciążenia szablonu, które wywołuje nowsze, bezpieczne odpowiednika tej funkcji. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Wyjątki

**Wcsrtombs —** funkcja jest bezpieczna wielowątkowych, tak długo, jak wywołania funkcji, nie w bieżącym wątku **setlocale** podczas wykonywania tej funkcji i *mbstate* nie ma wartości null.

## <a name="example"></a>Przykład

```cpp
// crt_wcsrtombs.cpp
// compile with: /W3
// This code example converts a wide
// character string into a multibyte
// character string.

#include <stdio.h>
#include <memory.h>
#include <wchar.h>
#include <errno.h>

#define MB_BUFFER_SIZE 100

int main()
{
    const wchar_t   wcString[] =
                    {L"Every good boy does fine."};
    const wchar_t   *wcsIndirectString = wcString;
    char            mbString[MB_BUFFER_SIZE];
    size_t          countConverted;
    mbstate_t       mbstate;

    // Reset to initial shift state
    ::memset((void*)&mbstate, 0, sizeof(mbstate));

    countConverted = wcsrtombs(mbString, &wcsIndirectString,
                               MB_BUFFER_SIZE, &mbstate); // C4996
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s
    if (errno == EILSEQ)
    {
        printf( "An encoding error was detected in the string.\n" );
    }
    else
    {
        printf( "The string was successfuly converted.\n" );
    }
}
```

```Output
The string was successfuly converted.
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wcsrtombs**|\<WChar.h >|

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
