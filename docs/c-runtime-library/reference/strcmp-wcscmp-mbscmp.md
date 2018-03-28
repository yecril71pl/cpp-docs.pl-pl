---
title: strcmp —, wcscmp —, _mbscmp — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- wcscmp
- _mbscmp
- strcmp
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _mbscmp
- wcscmp
- strcmp
- _tcscmp
- _ftcscmp
dev_langs:
- C++
helpviewer_keywords:
- tcscmp function
- strcmp function
- strings [C++], comparing
- mbscmp function
- string comparison [C++]
- _mbscmp function
- wcscmp function
- _tcscmp function
- _ftcscmp function
- ftcscmp function
ms.assetid: 5d216b57-7a5c-4cb3-abf0-0f4facf4396d
caps.latest.revision: ''
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: addc2c215d0c914e3caee3dba4d32f94ca91e62c
ms.sourcegitcommit: 604907f77eb6c5b1899194a9877726f3e8c2dabc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="strcmp-wcscmp-mbscmp"></a>strcmp, wcscmp, _mbscmp
Porównywanie ciągów.  
  
> [!IMPORTANT]
>  `_mbscmp` Nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
int strcmp(  
   const char *string1,  
   const char *string2   
);  
int wcscmp(  
   const wchar_t *string1,  
   const wchar_t *string2   
);  
int _mbscmp(  
   const unsigned char *string1,  
   const unsigned char *string2   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `string1`, `string2`  
 Ciągi zakończone wartością null do porównania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość zwracana dla każdej z tych funkcji wskazuje stosunek liczby porządkowej `string1` do `string2`.  
  
|Wartość|Relacja ciąg1 do ciąg2|  
|-----------|----------------------------------------|  
|< 0|`string1` Jest mniejsza niż `string2`|  
|0|`string1` jest taka sama jak `string2`|  
|> 0|`string1` Jest większa niż `string2`|  
  
 Parametr błędu sprawdzania poprawności `_mbscmp` zwraca `_NLSCMPERROR`, która jest zdefiniowana w \<string.h > i \<mbstring.h >.  
  
## <a name="remarks"></a>Uwagi  
 `strcmp` Funkcja przeprowadza porównanie liczby porządkowej `string1` i `string2` i zwraca wartość wskazującą, ich relacji. `wcscmp` i `_mbscmp` są odpowiednio znaków dwubajtowych i znaków wielobajtowych wersje `strcmp`. `_mbscmp` rozpoznaje wielobajtowych sekwencji znaków zgodnie z bieżącej strony kodowe wielobajtowe i zwraca `_NLSCMPERROR` w przypadku wystąpienia błędu. Aby uzyskać więcej informacji, zobacz [stron kodowych](../../c-runtime-library/code-pages.md). Ponadto jeśli `string1` lub `string2` wskaźnika o wartości null, jest `_mbscmp` wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `_mbscmp` zwraca `_NLSCMPERROR` i ustawia `errno` do `EINVAL`. `strcmp` i `wcscmp` nie weryfikują ich parametrów. Te trzy funkcje działają tak samo w przeciwnym razie wartość.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcscmp`|`strcmp`|`_mbscmp`|`wcscmp`|  
  
 `strcmp` Funkcji różnią się od `strcoll` funkcje, w tym `strcmp` porównania są porządkowej i są niezależne od ustawień regionalnych. `strcoll` Porównanie ciągów lexicographically przy użyciu `LC_COLLATE` kategorii bieżące ustawienia regionalne. Aby uzyskać więcej informacji na temat `LC_COLLATE` kategorii, zobacz [setlocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
 Zgodnie z ustawieniami regionalnymi "C" kolejność znaków w zestawie znaków (zestaw znaków ASCII) jest taka sama jak kolejność lexicographic znaków. Jednak w innych lokalizacjach kolejność znaków w zestawie znaków mogą się różnić od lexicographic kolejności. Na przykład w niektórych lokalizacjach Europejskich, znak "" (wartość 0x61) znajduje się przed znak "ź" (wartość 0xE4) w zestawie znaków, ale przed znakiem "ź" zawiera znak "" lexicographically.  
  
 W których zestaw znaków i kolejność znaków lexicographic inne ustawienia regionalne, można użyć `strcoll` zamiast `strcmp` lexicographic porównywania ciągów. Alternatywnie można użyć `strxfrm` na ciągi oryginalny, a następnie użyć `strcmp` wynikowy ciągów.  
  
 `strcmp` Funkcji jest rozróżniana wielkość liter. `_stricmp`, `_wcsicmp`, i `_mbsicmp` porównywanie ciągów przez pierwszy konwersję na małe litery formularzy. Dwa ciągi, które zawierają znaki, które znajdują się między "Z" i "" w tabeli ASCII ("[","`\`", "]","`^`","`_`", i "") porównania w różny sposób, w zależności od ich przypadku. Na przykład dwa ciągi `"ABCDE"` i `"ABCD^"` porównanie jedną z metod, jeśli wynikiem porównania jest małe litery (`"abcde"` > `"abcd^"`) i w inny sposób (`"ABCDE"` < `"ABCD^"`) Jeśli jest to wielkie litery.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`strcmp`|<string.h>|  
|`wcscmp`|< string.h > lub < wchar.h >|  
|`_mbscmp`|\<mbstring.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_strcmp.c  
  
#include <string.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
char string1[] = "The quick brown dog jumps over the lazy fox";  
char string2[] = "The QUICK brown dog jumps over the lazy fox";  
  
int main( void )  
{  
   char tmp[20];  
   int result;  
  
   // Case sensitive  
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );  
   result = strcmp( string1, string2 );  
   if( result > 0 )  
      strcpy_s( tmp, _countof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, _countof (tmp), "less than" );  
   else  
      strcpy_s( tmp, _countof (tmp), "equal to" );  
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );  
  
   // Case insensitive (could use equivalent _stricmp)  
   result = _stricmp( string1, string2 );  
   if( result > 0 )  
      strcpy_s( tmp, _countof (tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, _countof (tmp), "less than" );  
   else  
      strcpy_s( tmp, _countof (tmp), "equal to" );  
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );  
}  
```  
  
```Output  
Compare strings:  
   The quick brown dog jumps over the lazy fox  
   The QUICK brown dog jumps over the lazy fox  
  
   strcmp:   String 1 is greater than string 2  
   _stricmp:  String 1 is equal to string 2  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)   
 [funkcji memcmp, wmemcmp —](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [_memicmp, _memicmp_l](../../c-runtime-library/reference/memicmp-memicmp-l.md)   
 [strcoll — funkcje](../../c-runtime-library/strcoll-functions.md)   
 [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)   
 [strncmp —, wcsncmp —, _mbsncmp — _mbsncmp_l —](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr —, wcsrchr —, _mbsrchr — _mbsrchr_l —](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn —, wcsspn —, _mbsspn — _mbsspn_l —](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)   
 [strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)