---
title: wcsrtombs — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d2ea0252714803fe8cad48635486d2011275407
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415471"
---
# <a name="wcsrtombs"></a>wcsrtombs

Konwertowanie ciągu znaków typu wide reprezentacji ciągu znaków wielobajtowych. Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [wcsrtombs_s —](wcsrtombs-s.md).

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
Powstałe w ten sposób przekonwertować ciągu znaków wielobajtowych adresu.

*wcstr*<br/>
Pośrednio wskazuje lokalizację ciąg znaków typu wide do skonwertowania.

*Liczba*<br/>
Liczba znaków, które ma zostać przekonwertowany.

*mbstate*<br/>
Wskaźnik do **mbstate_t** konwersji stanu obiektu.

## <a name="return-value"></a>Wartość zwracana

Zwraca liczbę bajtów pomyślnie przekonwertowany, nie tym null przerywanie bajtem null (jeśli istnieje), w przeciwnym razie wartość -1, jeśli wystąpił błąd.

## <a name="remarks"></a>Uwagi

**Wcsrtombs —** funkcja konwertuje ciąg znaki dwubajtowe, począwszy od określonej konwersji stanie zawartymi w *mbstate*, pośrednie wartości wskazywana w *wcstr*, do adresu *mbstr*. Konwersja będzie dla każdego znaku do: po napotkano wartość null, przerywanie znaków dwubajtowych po napotkaniu z systemem innym niż odpowiedni znak lub gdy następny znak przekroczyłby limit zawarte w *liczba*. Jeśli **wcsrtombs —** napotka znak null znaków dwubajtowych (L '\0'), przed lub po *liczba* występuje i konwertuje ją na 8-bitowej 0 i powoduje zatrzymanie.

W związku z tym ciąg znaków wielobajtowych *mbstr* jest zakończony wartością null tylko wtedy, gdy **wcsrtombs —** napotka znak null znaków typu wide podczas konwersji. Jeśli sekwencje wskazywana przez *wcstr* i *mbstr* nakładają się zachowanie **wcsrtombs —** jest niezdefiniowana. **wcsrtombs —** dotyczy kategorii LC_TYPE bieżące ustawienia regionalne.

**Wcsrtombs —** funkcja różni się od [wcstombs —, _wcstombs_l —](wcstombs-wcstombs-l.md) przez jego restartability. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań w tej samej lub innych funkcji ponownego uruchamiania. Wyniki są niezdefiniowane, gdy mieszanie korzystanie z funkcji ponownego uruchamiania i nonrestartable.  Na przykład aplikacja może użyć **wcsrlen** zamiast **wcsnlen —**, jeśli kolejne wywołanie **wcsrtombs —** użyto zamiast **wcstombs —**.

Jeśli *mbstr* argument jest **NULL**, **wcsrtombs —** zwraca wymagany rozmiar w bajtach ciągu docelowego. Jeśli *mbstate* ma wartość null, wewnętrznego **mbstate_t** stan konwersji jest używany. Jeśli sekwencja znaków *wchar* nie ma odpowiedniego wielobajtowe reprezentacji znaków, zwracany jest -1 i **errno** ma ustawioną wartość **eilseq —**.

W języku C++ ta funkcja ma przeciążenia szablonów, które wywołuje nowsza, bezpieczne odpowiednikiem tej funkcji. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Wyjątki

**Wcsrtombs —** funkcji jest bezpieczne wielowątkowe tak długo, jak wywołuje żadnej funkcji w bieżącym wątku **setlocale** podczas wykonywania tej funkcji i *mbstate* nie jest zerowa.

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
