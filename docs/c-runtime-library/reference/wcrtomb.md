---
title: wcrtomb
ms.date: 11/04/2016
apiname:
- wcrtomb
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
- wcrtomb
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
ms.openlocfilehash: a5fad3f41c7ed459a1af3fae7c6a5a85c867d5ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659254"
---
# <a name="wcrtomb"></a>wcrtomb

Przekonwertuj znakiem dwubajtowym na jego reprezentację w postaci znaku wielobajtowego. Bardziej bezpieczna wersja ta funkcja jest dostępna; zobacz [wcrtomb_s —](wcrtomb-s.md).

## <a name="syntax"></a>Składnia

```C
size_t wcrtomb(
   char *mbchar,
   wchar_t wchar,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcrtomb(
   char (&mbchar)[size],
   wchar_t wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*mbchar*<br/>
Wynikowy znaków wielobajtowych konwersji znaków.

*WChar*<br/>
Szeroki znak do przekształcenia.

*mbstate*<br/>
Wskaźnik do **mbstate_t** obiektu.

## <a name="return-value"></a>Wartość zwracana

Zwraca liczbę bajtów wymaganą do reprezentowania przekonwertowany znak wielobajtowy, w przeciwnym razie -1 w przypadku wystąpienia błędu.

## <a name="remarks"></a>Uwagi

**Wcrtomb —** funkcja konwertuje znakiem dwubajtowym, począwszy od stanu określonej konwersji zawarte w *mbstate*, od wartości zawarte w *wchar*, do adres jest reprezentowany przez *mbchar*. Wartość zwracana jest liczba bajtów potrzebnych do reprezentowania odpowiedniego znaku wielobajtowego, ale nie zwróci więcej niż **MB_CUR_MAX** bajtów.

Jeśli *mbstate* ma wartość null, wewnętrzny **mbstate_t** obiekt, który zawiera stan konwersji *mbchar* jest używany. Jeśli sekwencja znaków *wchar* nie ma odpowiedniego znaków wielobajtowych reprezentacji znaków, jest zwracana wartość -1 i **errno** ustawiono **EILSEQ**.

**Wcrtomb —** funkcja różni się od [wctomb —, _wctomb_l —](wctomb-wctomb-l.md) przez jego restartability. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań tej samej lub innych funkcji ponownego uruchamiania. Podczas korzystania z funkcji ponownego uruchamiania i nonrestartable mieszania, wyniki są niezdefiniowane. Na przykład, aplikacja będzie używać **wcsrlen** zamiast **wcsnlen —**, jeśli kolejne wywołanie **wcsrtombs —** były używane zamiast **wcstombs —**.

W języku C++ funkcja ta ma przeciążenia szablonu, który wywołuje nowsze, bezpieczne odpowiedniki tej funkcji. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Wyjątki

**Wcrtomb —** funkcja jest bezpieczna wielowątkowych, tak długo, jak wywołania funkcji, nie w bieżącym wątku **setlocale** podczas wykonywania tej funkcji oraz w trakcie *mbstate* ma wartość null.

## <a name="example"></a>Przykład

```C
// crt_wcrtomb.c
// compile with: /W3
// This program converts a wide character
// to its corresponding multibyte character.

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    size_t      sizeOfCovertion = 0;
    mbstate_t   mbstate;
    char        mbStr = 0;
    wchar_t*    wcStr = L"Q";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    sizeOfCovertion = wcrtomb(&mbStr, *wcStr, &mbstate); // C4996
    // Note: wcrtomb is deprecated; consider using wcrtomb_s instead
    if (sizeOfCovertion > 0)
    {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wcStr);
        printf(" was converted to the \"%c\" ", mbStr);
        printf("multibyte character.\n");
    }
    else
    {
        printf("No corresponding multibyte character "
               "was found.\n");
    }
}
```

```Output
The corresponding wide character "Q" was converted to the "Q" multibyte character.
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wcrtomb**|\<WChar.h >|

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
