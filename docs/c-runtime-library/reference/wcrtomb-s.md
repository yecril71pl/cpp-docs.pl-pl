---
title: wcrtomb_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a035010c2af49c0d12b4b7f1d6429c66ba9032cc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415611"
---
# <a name="wcrtombs"></a>wcrtomb_s

Przekonwertuj znaków dwubajtowych na jej reprezentację znaków wielobajtowych. Wersja [wcrtomb —](wcrtomb.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Wynikowa wielobajtowe konwersji znaków.

*sizeOfmbchar*<br/>
Rozmiar *mbchar* zmiennej w bajtach.

*WChar*<br/>
Szerokie do konwersji.

*mbstate*<br/>
Wskaźnik do **mbstate_t** obiektu.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość zero lub **errno** wartość, gdy wystąpi błąd.

## <a name="remarks"></a>Uwagi

**Wcrtomb_s —** funkcja konwertuje znaków dwubajtowych, począwszy od określonej konwersji stanie zawartymi w *mbstate*, od wartości zawartych w *wchar*, do adres reprezentowany przez *mbchar*. *PReturnValue* wartość będzie liczba bajtów przekonwertowany, ale nie więcej niż **mb_cur_max —** bajtów lub -1, jeśli wystąpił błąd.

Jeśli *mbstate* ma wartość null, wewnętrznego **mbstate_t** stan konwersji jest używany. Jeśli znak zawarte w *wchar* nie ma odpowiedniego znaków wielobajtowych wartość *pReturnValue* będzie mieć wartość -1, a funkcja zwróci **errno** wartość **eilseq —**.

**Wcrtomb_s —** funkcja różni się od [wctomb_s —, _wctomb_s_l —](wctomb-s-wctomb-s-l.md) przez jego restartability. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań w tej samej lub innych funkcji ponownego uruchamiania. Wyniki są niezdefiniowane, gdy mieszanie korzystanie z funkcji ponownego uruchamiania i nonrestartable. Na przykład aplikacja może użyć **wcsrlen** zamiast **wcslen —**, jeśli kolejne wywołanie **wcsrtombs_s —** użyto zamiast **wcstombs_s —**.

W języku C++ za pomocą tej funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (wyeliminowanie konieczności określania argumentem rozmiaru) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Wyjątki

**Wcrtomb_s —** funkcji jest bezpieczne wielowątkowe tak długo, jak wywołuje żadnej funkcji w bieżącym wątku **setlocale** podczas wykonywania tej funkcji i *mbstate* ma wartość null.

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
|**wcrtomb_s**|\<WChar.h >|

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
