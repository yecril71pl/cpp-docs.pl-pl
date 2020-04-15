---
title: mbrtowc
ms.date: 4/2/2020
api_name:
- mbrtowc
- _o_mbrtowc
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
- mbrtowc
helpviewer_keywords:
- mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
ms.openlocfilehash: be46c3f3c728b70c7cbf060572acc24662637a81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340930"
---
# <a name="mbrtowc"></a>mbrtowc

Konwertuj znak wielobajtowy w bieżącym ustawieniach regionalnych na równoważny znak szeroki, z możliwością ponownego uruchamiania w środku znaku wielobajtowego.

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

*Wchar*<br/>
Adres szerokiego znaku, aby otrzymać przekonwertowany ciąg znaków szerokich (wpisz **wchar_t**). Ta wartość może być wskaźnikiem zerowym, jeśli nie jest wymagany szeroki znak powrotu.

*mbchar*<br/>
Adres sekwencji bajtów (znak wielobajtowy).

*Liczba*<br/>
Liczba bajtów do sprawdzenia.

*mbstate*<br/>
Wskaźnik do obiektu stanu konwersji. Jeśli ta wartość jest wskaźnikiem zerowym, funkcja używa statycznego obiektu stanu konwersji wewnętrznej. Ponieważ obiekt **mbstate_t** wewnętrznej nie jest bezpieczny dla wątków, zaleca się, aby zawsze przechodzić własny argument *mbstate.*

## <a name="return-value"></a>Wartość zwracana

Jedna z następujących wartości:

0 Następna *liczba* lub mniej bajtów zakończy znak wielobajtowy reprezentujący znak o szerokości null, który jest przechowywany w *wchar*, jeśli *wchar* nie jest wskaźnikiem null.

1 do *zliczania*, włącznie Następna *liczba* lub mniej bajtów zakończyć prawidłowy znak wielobajtowy. Zwrócona wartość to liczba bajtów, które wypełniają znak wielobajtowy. Odpowiednik znaku szerokiego jest przechowywany w *wchar*, jeśli *wchar* nie jest wskaźnikiem null.

(size_t) (-1) Wystąpił błąd kodowania. Następna *liczba* lub mniej bajtów nie przyczyniają się do pełnego i prawidłowego znaku wielobajtowego. W takim przypadku **errno** jest ustawiona na EILSEQ i stan zmiany konwersji w *mbstate* jest nieokreślony.

(size_t) (-2) Następna *liczba* bajtów przyczyniają się do niekompletnego, ale potencjalnie prawidłowego znaku wielobajtowego, a wszystkie bajty *count* zostały przetworzone. Żadna wartość nie jest przechowywana w *wchar*, ale *mbstate* jest aktualizowana, aby ponownie uruchomić funkcję.

## <a name="remarks"></a>Uwagi

Jeśli *mbchar* jest wskaźnikiem null, funkcja jest równoważna wywołaniu:

`mbrtowc(NULL, "", 1, &mbstate)`

W takim przypadku wartość argumentów *wchar* i *count* są ignorowane.

Jeśli *mbchar* nie jest wskaźnikiem null, funkcja sprawdza *liczbę* bajtów z *mbchar,* aby określić wymaganą liczbę bajtów, które są wymagane do ukończenia następnego znaku wielobajtowego. Jeśli następny znak jest prawidłowy, odpowiedni znak wielobajtowy jest przechowywany w *wchar,* jeśli nie jest wskaźnikiem null. Jeśli znak jest odpowiadający szeroki znak null, wynikowy stan *mbstate* jest stan konwersji początkowej.

Funkcja **mbrtowc** różni się od [mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md) od możliwości ponownego uruchomienia. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań do tej samej lub innych funkcji, które można ponownie uruchomić. Wyniki są niezdefiniowane podczas mieszania użycia funkcji, które można ponownie uruchomić i niepodważalne.  Na przykład aplikacja powinna używać **wcsrlen** zamiast **wcslen,** jeśli zamiast **wcstombs**jest używane kolejne wywołanie **wcsrtombs.**

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="example"></a>Przykład

Konwertuje znak wielobajtowy na jego odpowiednik znaków szerokich.

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
|**mbrtowc**|\<wchar.h>|

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
