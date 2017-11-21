---
title: "mbrtowc — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: mbrtowc
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
f1_keywords: mbrtowc
dev_langs: C++
helpviewer_keywords: mbrtowc function
ms.assetid: a1e87fcc-6de0-4ca1-bf26-508d28490286
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: afbc17fbe93fdead069ca89ebbaf0eee400cd746
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mbrtowc"></a>mbrtowc
Przekonwertuj znaków wielobajtowych w bieżących ustawień regionalnych na równoważne znaków dwubajtowych z możliwością ponownego uruchomienia w środku znaków wielobajtowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
size_t mbrtowc(  
   wchar_t *wchar,  
   const char *mbchar,  
   size_t count,  
   mbstate_t *mbstate  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wchar`  
 Adres znaków dwubajtowych na ciąg znaków typu wide przekonwertowanego (typ `wchar_t`). Ta wartość może być wskaźnika o wartości null, jeśli żadne znaki nie szeroki zwracane są wymagane.  
  
 `mbchar`  
 Adres sekwencję bajtów (znaków wielobajtowych).  
  
 `count`  
 Liczba bajtów do sprawdzenia.  
  
 `mbstate`  
 Wskaźnik do obiektu stanu konwersji. Jeśli ta wartość jest wskaźnika o wartości null, funkcja używa obiektu stanu statyczne wewnętrzne konwersji. Ponieważ wewnętrznej `mbstate_t` obiekt nie jest bezpieczne wątkowo, zaleca się, że należy zawsze przekazuj własne `mbstate` argumentu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jedna z następujących wartości:  
  
 0  
 Następne `count` lub mniej bajtów wykonać znaków wielobajtowych, reprezentujący null znaków dwubajtowych, który jest przechowywany w `wchar`, jeśli `wchar` nie jest wskaźnika o wartości null.  
  
 od 1 do `count`włącznie  
 Następne `count` lub nieprawidłowy znaków wielobajtowych wykonania mniejszej liczby bajtów. Wartość zwracana jest liczba bajtów, które ukończyć znaków wielobajtowych. Znaków dwubajtowych równoważne są przechowywane w `wchar`, jeśli `wchar` nie jest wskaźnika o wartości null.  
  
 (size_t) (-1)  
 Wystąpił błąd kodowania. Następne `count` lub mniej bajtów nie wspierają znaków wielobajtowych pełne i prawidłowe. W takim przypadku `errno` ma ustawioną wartość eilseq — i stan shift konwersji w `mbstate` jest nieokreślony.  
  
 (size_t) -(2)  
 Następne `count` bajtów współtworzyć niekompletne, ale potencjalnie prawidłowy znaków wielobajtowych i wszystkie `count` bajty zostały przetworzone. Wartość nie jest przechowywana w `wchar`, ale `mbstate` jest aktualizowana w celu ponownego uruchomienia funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `mbchar` jest wskaźnika o wartości null, funkcja jest odpowiednikiem wywołania:  
  
 `mbrtowc(NULL, "", 1, &mbstate)`  
  
 W tym przypadku wartości argumentów `wchar` i `count` są ignorowane.  
  
 Jeśli `mbchar` nie jest wskaźnika o wartości null, funkcja sprawdza `count` bajtów z `mbchar` ustalenie wymaganej liczby bajtów, które są wymagane do przeprowadzenia dalej znaków wielobajtowych. Jeśli następny znak jest prawidłowy, odpowiednich znaków wielobajtowych są przechowywane w `wchar` Jeśli nie jest wskaźnika o wartości null. Jeśli znak jest całego null odpowiadającego znaku, Wynikowy stan `mbstate` jest w stanie początkowej konwersji.  
  
 `mbrtowc` Funkcja różni się od [mbtowc —, _mbtowc_l —](../../c-runtime-library/reference/mbtowc-mbtowc-l.md) przez jego restartability. Stan konwersji jest przechowywany w `mbstate` dla kolejnych wywołań w tej samej lub innych funkcji ponownego uruchamiania. Wyniki są niezdefiniowane, gdy mieszanie korzystanie z funkcji ponownego uruchamiania i nonrestartable.  Na przykład, aplikacja, należy użyć `wcsrlen` zamiast `wcslen` Jeśli kolejne wywołanie `wcsrtombs` jest używany zamiast `wcstombs`.  
  
## <a name="example"></a>Przykład  
 Konwertuje znaków wielobajtowych jego odpowiednik znaków dwubajtowych.  
  
```  
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
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
Locale set to: "French_Canada.1252"  
Conversion succeeded!  
Multibyte String: AaBbCcÜïα∩≡xXyYzZ  
WC String: AaBbCcÜïα∩≡xXyYzZ  
```  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`mbrtowc`|\<WChar.h >|  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)