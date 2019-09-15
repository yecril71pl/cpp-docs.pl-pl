---
title: mbrtowc
ms.date: 11/04/2016
api_name:
- mbrtowc
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
- mbrtowc
helpviewer_keywords:
- mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
ms.openlocfilehash: b4c68ae8df9821d862b9f742d8a8ef7ace19c981
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952446"
---
# <a name="mbrtowc"></a>mbrtowc

Konwertowanie znaku wielobajtowego w bieżących ustawieniach regionalnych na równoważny znak szeroki, z możliwością ponownego uruchomienia w środku znaku wielobajtowego.

## <a name="syntax"></a>Składnia

```C
size_t mbrtowc(
   wchar_t *wchar,
   const char *mbchar,
   size_t count,
   mbstate_t *mbstate
);
```

### <a name="parameters"></a>Parametry

*WCHAR*<br/>
Adres znaku dwubajtowego, który ma zostać wyświetlony przekonwertowany ciąg znaków dwubajtowych (typ **wchar_t**). Ta wartość może być pustym wskaźnikiem, jeśli nie jest wymagany żaden znak dwubajtowy.

*mbchar*<br/>
Adres sekwencji bajtów (znak wielobajtowy).

*liczbą*<br/>
Liczba bajtów do sprawdzenia.

*mbstate*<br/>
Wskaźnik do obiektu stanu konwersji. Jeśli ta wartość jest wskaźnikiem typu null, funkcja używa statycznego obiektu stanu konwersji wewnętrznego. Ponieważ wewnętrzny obiekt **mbstate_t** nie jest bezpieczny wątkowo, zalecamy, aby zawsze przekazać własny argument *mbstate* .

## <a name="return-value"></a>Wartość zwracana

Jedna z następujących wartości:

0 *Liczba* następnych lub mniej bajtów kończy się znakiem wielobajtowym, który reprezentuje znak szerokości zerowej, który jest przechowywany w *WCHAR*, jeśli *WCHAR* nie jest wskaźnikiem o wartości null.

1 do *zliczenia*, włącznie z kolejną *liczbą* lub mniejszą liczbą bajtów, uzupełnij prawidłowy znak wielobajtowy. Zwracana wartość to liczba bajtów zakończonych znakiem wielobajtowym. Odpowiednik znaku dwubajtowego jest przechowywany w *WCHAR*, jeśli *WCHAR* nie jest wskaźnikiem o wartości null.

(size_t) (-1) Wystąpił błąd kodowania. Kolejna lub mniejsza *Liczba* bajtów nie przyczyniają się do pełnego i prawidłowego znaku wielobajtowego. W tym przypadku **errno** jest ustawiony na EILSEQ, a stan przesunięcia konwersji w *mbstate* jest nieokreślony.

(size_t) (-2) Następna *Liczba* bajtów przyczynia się do niekompletnego, ale potencjalnie prawidłowego znaku wielobajtowego, a wszystkie bajty *licznika* zostały przetworzone. Żadna wartość nie jest przechowywana w *WCHAR*, ale *mbstate* jest aktualizowana w celu ponownego uruchomienia funkcji.

## <a name="remarks"></a>Uwagi

Jeśli *mbchar* jest wskaźnikiem typu null, funkcja jest równoważna z wywołaniem:

`mbrtowc(NULL, "", 1, &mbstate)`

W takim przypadku wartość argumentów *WCHAR* i *Count* jest ignorowana.

Jeśli *mbchar* nie jest wskaźnikiem o wartości null, funkcja sprawdza *liczbę* bajtów z *mbchar* , aby określić wymaganą liczbę bajtów, które są wymagane do ukończenia następnego znaku wielobajtowego. Jeśli następny znak jest prawidłowy, odpowiedni znak wielobajtowy jest przechowywany w *WCHAR* , jeśli nie jest pustym wskaźnikiem. Jeśli znak jest odpowiednim szerokim znakiem null, wynikiem stanu *mbstate* jest pierwotny stan konwersji.

Funkcja **mbrtowc** różni się od [mbtowc, _mbtowc_l,](mbtowc-mbtowc-l.md) dzięki czemu można jej uruchomić. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań do tych samych lub innych funkcji, które można uruchomić ponownie. Wyniki są niezdefiniowane podczas mieszania użycia funkcji ponownego uruchamiania i nieuruchomionych ponownie.  Na przykład aplikacja powinna używać **wcsrlen** zamiast **wcslen** , jeśli podczas kolejnego wywołania **wcsrtombs** zostanie użyta wartość **wcstombs**.

## <a name="example"></a>Przykład

Konwertuje znak wielobajtowy na odpowiedni znak większości.

```cpp
// crt_mbrtowc.cpp

#include <stdio.h>
#include <mbctype.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

#define BUF_SIZE 100

int Sample(char* szIn, wchar_t* wcOut, int nMax)
{
    mbstate_t   state = {0}; // Initial state
    size_t      nConvResult,
                nmbLen = 0,
                nwcLen = 0;
    wchar_t*    wcCur = wcOut;
    wchar_t*    wcEnd = wcCur + nMax;
    const char* mbCur = szIn;
    const char* mbEnd = mbCur + strlen(mbCur) + 1;
    char*       szLocal;

    // Sets all locale to French_Canada.1252
    szLocal = setlocale(LC_ALL, "French_Canada.1252");
    if (!szLocal)
    {
        printf("The fuction setlocale(LC_ALL, \"French_Canada.1252\") failed!\n");
        return 1;
    }

    printf("Locale set to: \"%s\"\n", szLocal);

    // Sets the code page associated current locale's code page
    // from a previous call to setlocale.
    if (_setmbcp(_MB_CP_SBCS) == -1)
    {
        printf("The fuction _setmbcp(_MB_CP_SBCS) failed!");
        return 1;
    }

    while ((mbCur < mbEnd) && (wcCur < wcEnd))
    {
        //
        nConvResult = mbrtowc(wcCur, mbCur, 1, &state);
        switch (nConvResult)
        {
            case 0:
            {  // done
                printf("Conversion succeeded!\nMultibyte String: ");
                printf(szIn);
                printf("\nWC String: ");
                wprintf(wcOut);
                printf("\n");
                mbCur = mbEnd;
                break;
            }

            case -1:
            {  // encoding error
                printf("The call to mbrtowc has detected an encoding error.\n");
                mbCur = mbEnd;
                break;
            }

            case -2:
            {  // incomplete character
                if   (!mbsinit(&state))
                {
                    printf("Currently in middle of mb conversion, state = %x\n", state);
                    // state will contain data regarding lead byte of mb character
                }

                ++nmbLen;
                ++mbCur;
                break;
            }

            default:
            {
                if   (nConvResult > 2) // The multibyte should never be larger than 2
                {
                    printf("Error: The size of the converted multibyte is %d.\n", nConvResult);
                }

                ++nmbLen;
                ++nwcLen;
                ++wcCur;
                ++mbCur;
            break;
            }
        }
    }

   return 0;
}

int main(int argc, char* argv[])
{
    char    mbBuf[BUF_SIZE] = "AaBbCc\x9A\x8B\xE0\xEF\xF0xXyYzZ";
    wchar_t wcBuf[BUF_SIZE] = {L''};

    return Sample(mbBuf, wcBuf, BUF_SIZE);
}
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
Locale set to: "French_Canada.1252"
Conversion succeeded!
Multibyte String: AaBbCcÜïα∩≡xXyYzZ
WC String: AaBbCcÜïα∩≡xXyYzZ
```

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**mbrtowc**|\<WCHAR. h >|

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
