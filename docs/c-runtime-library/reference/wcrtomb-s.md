---
title: wcrtomb_s
ms.date: 11/04/2016
apiname:
- wcrtomb_s
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
- wcrtomb_s
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
ms.openlocfilehash: 7fe7fba861eecec562928cf381973f62a4db60fb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155475"
---
# <a name="wcrtombs"></a>wcrtomb_s

Przekonwertuj znakiem dwubajtowym na jego reprezentację w postaci znaku wielobajtowego. Wersja [wcrtomb —](wcrtomb.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char *mbchar,
   size_t sizeOfmbchar,
   wchar_t *wchar,
   mbstate_t *mbstate
);
template <size_t size>
errno_t wcrtomb_s(
   size_t *pReturnValue,
   char (&mbchar)[size],
   wchar_t *wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parametry

*pReturnValue*<br/>
Zwraca liczbę bajtów zapisanych lub wartość -1, jeśli wystąpił błąd.

*mbchar*<br/>
Wynikowy znaków wielobajtowych konwersji znaków.

*sizeOfmbchar*<br/>
Rozmiar *mbchar* zmiennej w bajtach.

*WChar*<br/>
Szeroki znak do przekształcenia.

*mbstate*<br/>
Wskaźnik do **mbstate_t** obiektu.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero lub **errno** wartość, jeśli wystąpi błąd.

## <a name="remarks"></a>Uwagi

**Wcrtomb_s —** funkcja konwertuje znakiem dwubajtowym, począwszy od stanu określonej konwersji zawarte w *mbstate*, od wartości zawarte w *wchar*, do adres jest reprezentowany przez *mbchar*. *PReturnValue* wartość będzie liczba bajtów przekonwertowany, ale nie więcej niż **MB_CUR_MAX** bajtów lub wartość -1, jeśli wystąpił błąd.

Jeśli *mbstate* ma wartość null, wewnętrzny **mbstate_t** stan konwersji jest używany. Jeśli znak zawarty w *wchar* nie ma odpowiedniego znaku wielobajtowego wartość *pReturnValue* będzie mieć wartość -1, a funkcja zwróci **errno** wartość **EILSEQ**.

**Wcrtomb_s —** funkcja różni się od [wctomb_s —, _wctomb_s_l —](wctomb-s-wctomb-s-l.md) przez jego restartability. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań tej samej lub innych funkcji ponownego uruchamiania. Podczas korzystania z funkcji ponownego uruchamiania i nonrestartable mieszania, wyniki są niezdefiniowane. Na przykład, aplikacja będzie używać **wcsrlen** zamiast **wcslen —**, jeśli kolejne wywołanie **wcsrtombs_s —** były używane zamiast **wcstombs_s —**.

W języku C++ za pomocą tej funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując potrzebę określenia argumentu rozmiaru) oraz ich mogą automatycznie zastąpić starsze, niezabezpieczone funkcje ich nowsze, bezpieczne odpowiedniki. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Wyjątki

**Wcrtomb_s —** funkcja jest bezpieczna wielowątkowych, tak długo, jak wywołania funkcji, nie w bieżącym wątku **setlocale** podczas wykonywania tej funkcji i *mbstate* ma wartość null.

## <a name="example"></a>Przykład

```C
// crt_wcrtomb_s.c
// This program converts a wide character
// to its corresponding multibyte character.
//

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    errno_t     returnValue;
    size_t      pReturnValue;
    mbstate_t   mbstate;
    size_t      sizeOfmbStr = 1;
    char        mbchar = 0;
    wchar_t*    wchar = L"Q\0";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    returnValue = wcrtomb_s(&pReturnValue, &mbchar, sizeof(char),
                            *wchar, &mbstate);
    if (returnValue == 0) {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wchar);
        printf(" was converted to a the \"%c\" ", mbchar);
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
The corresponding wide character "Q" was converted to a the "Q" multibyte character.
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**wcrtomb_s**|\<wchar.h>|

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
