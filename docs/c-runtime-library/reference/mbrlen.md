---
title: "mbrlen — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- mbrlen
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbrlen
dev_langs:
- C++
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c5c110c1fc5917614514b4e4fd7e474569026207
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="mbrlen"></a>mbrlen
Określ liczbę bajtów, które są wymagane do przeprowadzenia znaków wielobajtowych w bieżących ustawień regionalnych, z możliwością ponownego uruchomienia w środku znaków wielobajtowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
size_t mbrlen(  
   const char * str,  
   size_t count,  
   mbstate_t * mbstate  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Wskaźnik do następnego bajtu, aby sprawdzić w ciągu znaków wielobajtowych.  
  
 `count`  
 Maksymalna liczba bajtów do sprawdzenia.  
  
 `mbstate`  
 Wskaźnik do bieżącego stanu przesunięcia początkowego bajt `str`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jedna z następujących wartości:  
  
 0  
 Następne `count` lub mniej bajtów wykonać znaków wielobajtowych, reprezentujący znaków dwubajtowych wartości null.  
  
 od 1 do `count`włącznie  
 Następne `count` lub nieprawidłowy znaków wielobajtowych wykonania mniejszej liczby bajtów. Wartość zwracana jest liczba bajtów, które ukończyć znaków wielobajtowych.  
  
 (size_t)(-2)  
 Następne `count` bajtów współtworzyć niekompletne, ale potencjalnie prawidłowy znaków wielobajtowych i wszystkie `count` bajty zostały przetworzone.  
  
 (size_t)(-1)  
 Wystąpił błąd kodowania. Następne `count` lub mniej bajtów nie wspierają znaków wielobajtowych pełne i prawidłowe. W takim przypadku `errno` ma ustawioną wartość eilseq — i stan konwersji w `mbstate` jest nieokreślony.  
  
## <a name="remarks"></a>Uwagi  
 `mbrlen` Funkcja sprawdza co najwyżej `count` bajtów, począwszy od bajtu wskazywana przez `str` można określić liczbę bajtów, które są wymagane do zakończenia następnego znaków wielobajtowych, w tym wszystkie sekwencje shift. Jest to odpowiednik wywołania `mbrtowc(NULL, str, count, &mbstate)` gdzie `mbstate` jest albo określonego przez użytkownika `mbstate_t` albo statyczne obiekt wewnętrzny pochodzącymi z biblioteki.  
  
 `mbrlen` Funkcja zapisuje i używa stanu shift niekompletne znaków wielobajtowych w `mbstate` parametru. Dzięki temu `mbrlen` możliwość ponownego uruchomienia środku znaków wielobajtowych, jeśli muszą być co najwyżej badanie `count` bajtów. Jeśli `mbstate` wskaźnika o wartości null, jest `mbrlen` używa wewnętrznego, statycznej `mbstate_t` obiektu do przechowywania stanu shift. Ponieważ wewnętrznej `mbstate_t` obiekt nie jest bezpieczne wątkowo, zalecamy zawsze przydzielić i przekazać swoje własne `mbstate` parametru.  
  
 `mbrlen` Funkcja różni się od [_mbclen —, mblen —, _mblen_l —](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md) przez jego restartability. Stan shift jest przechowywany w `mbstate` dla kolejnych wywołań w tej samej lub innych funkcji ponownego uruchamiania. Wyniki są niezdefiniowane, gdy mieszanie korzystanie z funkcji ponownego uruchamiania i nonrestartable.  Na przykład, aplikacja, należy użyć `wcsrlen` zamiast `wcslen` Jeśli kolejne wywołanie `wcsrtombs` jest używany zamiast `wcstombs.`  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|Nie dotyczy|Nie dotyczy|`mbrlen`|Nie dotyczy|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`mbrlen`|\<wchar.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano sposób interpretacji znaków wielobajtowych zależy od bieżącej stronie kodowej i pokazuje możliwości wznawianie `mbrlen`.  
  
```C  
// crt_mbrlen.c  
// Compile by using: cl crt_mbrlen.c  
#include <stdlib.h>  
#include <stdio.h>  
#include <string.h>  
#include <locale.h>  
#include <wchar.h>  
  
size_t Example(const char * pStr)  
{  
    size_t      charLen = 0;  
    size_t      charCount = 0;  
    mbstate_t   mbState = {0};  
  
    while ((charLen = mbrlen(pStr++, 1, &mbState)) != 0 &&  
            charLen != (size_t)-1)  
    {  
        if (charLen != (size_t)-2) // if complete mbcs char,  
        {  
            charCount++;  
        }  
    }   
    return (charCount);  
}   
  
int main( void )  
{  
    int         cp;  
    size_t      charCount = 0;  
    const char  *pSample =   
        "\x82\xD0\x82\xE7\x82\xAA\x82\xC8: Shift-jis hiragana.";  
  
    cp = _getmbcp();  
    charCount = Example(pSample);  
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",   
        cp, pSample, charCount);  
  
    setlocale(LC_ALL, "ja-JP"); // Set Japanese locale  
    _setmbcp(932); // and Japanese multibyte code page  
    cp = _getmbcp();  
    charCount = Example(pSample);  
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",   
        cp, pSample, charCount);  
}  
```  
  
```Output  
  
Code page: 0  
é╨éτé¬é╚: Shift-jis hiragana.  
Character count: 29  
  
Code page: 932  
????: Shift-jis hiragana.  
Character count: 25  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)   
 [Wersja regionalna](../../c-runtime-library/locale.md)