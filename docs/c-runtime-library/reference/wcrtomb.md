---
title: "wcrtomb — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: wcrtomb
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
f1_keywords: wcrtomb
dev_langs: C++
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7c9dfe3b112754d573226fe992d346d57de56406
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="wcrtomb"></a>wcrtomb
Przekonwertuj znaków dwubajtowych na jej reprezentację znaków wielobajtowych. Bezpieczniejsza wersja ta funkcja jest dostępna; zobacz [wcrtomb_s —](../../c-runtime-library/reference/wcrtomb-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 [out]`mbchar`  
 Wynikowa wielobajtowe konwersji znaków.  
  
 [in]`wchar`  
 Szerokie do konwersji.  
  
 [in]`mbstate`  
 Wskaźnik do `mbstate_t` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę bajtów wymaganą do reprezentowania przekonwertowanego znaków wielobajtowych, w przeciwnym razie wartość -1 w przypadku wystąpienia błędu.  
  
## <a name="remarks"></a>Uwagi  
 `wcrtomb` Funkcja konwertuje znaków dwubajtowych, począwszy od określonej konwersji stanie zawartymi w `mbstate`, od wartości zawartych w `wchar`, na adres reprezentowany przez `mbchar`. Wartość zwracana jest liczbę bajtów wymaganą do reprezentowania odpowiednich znaków wielobajtowych, ale nie będzie zwracać więcej niż `MB_CUR_MAX` bajtów.  
  
 Jeśli `mbstate` ma wartość null, wewnętrznego `mbstate_t` obiekt zawierający stan konwersji `mbchar` jest używany. Jeśli sekwencja znaków `wchar` nie ma odpowiedniego wielobajtowe reprezentacji znaków, zwracany jest -1 i `errno` ma ustawioną wartość `EILSEQ`.  
  
 `wcrtomb` Funkcja różni się od [wctomb —, _wctomb_l —](../../c-runtime-library/reference/wctomb-wctomb-l.md) przez jego restartability. Stan konwersji jest przechowywany w `mbstate` dla kolejnych wywołań w tej samej lub innych funkcji ponownego uruchamiania. Wyniki są niezdefiniowane, gdy mieszanie korzystanie z funkcji ponownego uruchamiania i nonrestartable. Na przykład aplikacja może użyć `wcsrlen` zamiast `wcsnlen`, jeśli kolejne wywołanie `wcsrtombs` użyto zamiast `wcstombs`.  
  
 W języku C++ ta funkcja ma przeciążenia szablonów, które wywołuje odpowiedników nowsza, bezpieczne tej funkcji. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="exceptions"></a>Wyjątki  
 `wcrtomb` Funkcji jest bezpieczne wielowątkowe tak długo, jak wywołuje żadnej funkcji w bieżącym wątku `setlocale` podczas wykonywania tej funkcji oraz w trakcie `mbstate` ma wartość null.  
  
## <a name="example"></a>Przykład  
  
```  
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
|`wcrtomb`|\<WChar.h >|  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)