---
title: mbrtowc
ms.date: 11/04/2016
apiname:
- mbrtowc
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
- mbrtowc
helpviewer_keywords:
- mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
ms.openlocfilehash: bd719e7b336333f6e06a1db9b1e34784575a1602
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581834"
---
# <a name="mbrtowc"></a>mbrtowc

Konwertuj znaków wielobajtowych przy bieżących ustawieniach regionalnych równoważne znak dwubajtowy, z możliwością ponownego uruchomienia w środku znaków wielobajtowych.

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

*WChar*<br/>
Adres na ciąg przekonwertowany szerokich znaków dwubajtowych (typ **wchar_t**). Ta wartość może być wskaźnikiem typu null, jeśli wymagana jest nie zwracanej szerokich znaków.

*mbchar*<br/>
Adres sekwencji bajtów (znak wielobajtowy).

*Liczba*<br/>
Liczba bajtów do wyboru.

*mbstate*<br/>
Wskaźnik do konwersji stan obiektu. Jeśli ta wartość jest wskaźnikiem typu null, funkcja używa obiektu stanu konwersji statycznej wewnętrznego. Ponieważ wewnętrzny **mbstate_t** obiekt nie jest metodą o bezpiecznych wątkach, zaleca się, że należy zawsze przekazuj parametr własne *mbstate* argumentu.

## <a name="return-value"></a>Wartość zwracana

Jeden z następujących wartości:

0 następnego *liczba* czy znak wielobajtowy, który reprezentuje wartość null znak dwubajtowy, który jest przechowywany w mniejszą liczbę bajtów *wchar*, jeśli *wchar* nie jest wskaźnikiem typu null.

1, aby *liczba*włącznie następnego *liczba* lub mniejsza liczba bajtów Zakończ prawidłowym znakiem wielobajtowym. Wartość zwracana jest liczba bajtów, kończące znaki wielobajtowe. Znak dwubajtowy równoważne są przechowywane w *wchar*, jeśli *wchar* nie jest wskaźnikiem typu null.

(size_t) (-1) Wystąpił błąd kodowania. Następne *liczba* lub mniejszej liczby bajtów nie przyczyniają się do kompletne i prawidłowy znak wielobajtowy. W tym przypadku **errno** jest ustawiona na EILSEQ i stan shift konwersji w *mbstate* jest nieokreślona.

(size_t) -(2) Następne *liczba* bajtów Współtworzenie niekompletne, ale potencjalnie prawidłowy znak wielobajtowy i wszystkie *liczba* bajty zostały przetworzone. Wartość nie jest przechowywany w *wchar*, ale *mbstate* zostanie zaktualizowany w celu ponownego uruchomienia tej funkcji.

## <a name="remarks"></a>Uwagi

Jeśli *mbchar* jest pustym wskaźnikiem, funkcja jest odpowiednikiem wywołania:

`mbrtowc(NULL, "", 1, &mbstate)`

W tym przypadku wartość z podanych argumentów *wchar* i *liczba* są ignorowane.

Jeśli *mbchar* nie jest wskaźnikiem typu null, funkcja sprawdza *liczba* bajtów z *mbchar* ustalenie wymaganej liczby bajtów, które są wymagane do wykonania następnego znak wielobajtowy. Jeśli następny znak jest prawidłowy, odpowiedniego znaku wielobajtowego są przechowywane w *wchar* Jeśli nie jest wskaźnikiem typu null. Jeśli znak jest odpowiadającego szeroki null znaku, Wynikowy stan *mbstate* jest stan początkowy konwersji.

**Mbrtowc —** funkcja różni się od [mbtowc, _mbtowc_l —](mbtowc-mbtowc-l.md) przez jego restartability. Stan konwersji jest przechowywany w *mbstate* dla kolejnych wywołań tej samej lub innych funkcji ponownego uruchamiania. Podczas korzystania z funkcji ponownego uruchamiania i nonrestartable mieszania, wyniki są niezdefiniowane.  Na przykład, aplikacja powinna używać **wcsrlen** zamiast **wcslen —** Jeśli kolejne wywołanie **wcsrtombs —** jest używana zamiast **wcstombs —**.

## <a name="example"></a>Przykład

Konwertuje jej równoważne znak dwubajtowy znak wielobajtowy.

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
|**mbrtowc**|\<WChar.h >|

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
