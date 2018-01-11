---
title: "_stricmp —, _wcsicmp —, _mbsicmp —, _stricmp_l —, _wcsicmp_l —, _mbsicmp_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _stricmp_l
- _mbsicmp
- _wcsicmp
- _mbsicmp_l
- _stricmp
- _wcsicmp_l
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ftcsicmp
- _stricmp
- wcsicmp_l
- _wcsicmp
- _tcsicmp
- _strcmpi
- stricmp_l
- _mbsicmp
- _fstricmp
- mbsicmp_l
- mbsicmp
dev_langs: C++
helpviewer_keywords:
- _wcsicmp function
- _stricmp_l function
- fstricmp function
- _tcsicmp function
- ftcsicmp function
- string comparison [C++], lowercase
- _wcsicmp_l function
- _fstricmp function
- strings [C++], comparing
- mbsicmp function
- _ftcsicmp function
- _mbsicmp_l function
- wcsicmp_l function
- _stricmp function
- _mbsicmp function
- tcsicmp function
- stricmp_l function
- mbsicmp_l function
- _strcmpi function
ms.assetid: 0e1ee515-0d75-435a-a445-8875d4669b50
caps.latest.revision: "28"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 15b581d0d47da824f1faaade1214d1320e29bb03
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="stricmp-wcsicmp-mbsicmp-stricmpl-wcsicmpl-mbsicmpl"></a>_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l
Wykonuje bez uwzględniania wielkości liter porównania ciągów.  
  
> [!IMPORTANT]
>  `_mbsicmp`i `_mbsicmp_l` nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _stricmp(  
   const char *string1,  
   const char *string2   
);  
int _wcsicmp(  
   const wchar_t *string1,  
   const wchar_t *string2   
);  
int _mbsicmp(  
   const unsigned char *string1,  
   const unsigned char *string2   
);  
int _stricmp_l(  
   const char *string1,  
   const char *string2,  
   _locale_t locale  
);  
int _wcsicmp_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   _locale_t locale  
);  
int _mbsicmp_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `string1, string2`  
 Ciągi zakończone wartością null do porównania.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartości zwracanej wskazuje stosunek `string1` do `string2` w następujący sposób.  
  
|Wartość zwracana|Opis|  
|------------------|-----------------|  
|< 0|`string1`mniej niż`string2`|  
|0|`string1`taki sam jak`string2`|  
|> 0|`string1`większa niż`string2`|  
  
 W przypadku wystąpienia błędu `_mbsicmp` zwraca `_NLSCMPERROR`, która jest zdefiniowana w \<string.h > i \<mbstring.h >.  
  
## <a name="remarks"></a>Uwagi  
 `_stricmp` Ordinally funkcji porównuje `string1` i `string2` po przekonwertowaniu każdego znaku małe i zwraca wartość wskazującą, ich relacji. `_stricmp`różni się od `_stricoll` w tym `_stricmp` tylko dotyczy porównanie `LC_CTYPE`, która określa, które znaki są wielkich i małych. `_stricoll` Funkcja porównuje ciągi zgodnie z obu `LC_CTYPE` i `LC_COLLATE` kategorii ustawienia regionalne, które zawiera zarówno w przypadku, jak i w kolejności sortowania. Aby uzyskać więcej informacji na temat `LC_COLLATE` kategorii, zobacz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) i [kategorie regionalne](../../c-runtime-library/locale-categories.md). Wersje tych funkcji bez `_l` sufiks Użyj bieżących ustawień regionalnych dla zachowania zależnych od ustawień regionalnych. Wersje wraz z sufiksem są identyczne, z wyjątkiem tego, aby używały przekazano zamiast ustawień regionalnych. Jeśli ustawienia regionalne nie została ustawiona, ustawienia regionalne C jest używany. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
> [!NOTE]
>  `_stricmp`jest odpowiednikiem `_strcmpi`. Mogą być używane zamiennie, ale `_stricmp` jest preferowanym standard.  
  
 `_strcmpi` Funkcji jest odpowiednikiem `_stricmp` i jest dostępne tylko w przypadku zgodności z poprzednimi wersjami.  
  
 Ponieważ `_stricmp` małe porównań, może spowodować nieoczekiwane zachowanie.  
  
 Aby zilustrować, kiedy przypadek konwersji `_stricmp` ma wpływ na wynik porównania, założono, że użytkownik ma dwa ciągi JOHNSTON i JOHN_HENRY. JOHNSTON ciąg JOHN_HENRY będą uznawane za mniej niż ponieważ "_" ma wartość ASCII niższe niż S. małe litery W rzeczywistości dowolny znak, który ma wartość ASCII między 91 i 96 będą uznawane za mniej niż dowolnej litery.  
  
 Jeśli [strcmp —](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md) funkcja jest używana zamiast `_stricmp`, JOHN_HENRY będą większe niż JOHNSTON.  
  
 `_wcsicmp`i `_mbsicmp` znaków dwubajtowych i znaków wielobajtowych wersji `_stricmp`. Argumenty i zwracana wartość `_wcsicmp` są znaków dwubajtowych ciągi; tych `_mbsicmp` są ciągami znaków wielobajtowych. `_mbsicmp`rozpoznaje wielobajtowych sekwencji znaków zgodnie z bieżącej strony kodowe wielobajtowe i zwraca `_NLSCMPERROR` w przypadku wystąpienia błędu. Aby uzyskać więcej informacji, zobacz [stron kodowych](../../c-runtime-library/code-pages.md). Te trzy funkcje działają tak samo w przeciwnym razie wartość.  
  
 `_wcsicmp`i `wcscmp` zachowują się tak samo, z wyjątkiem `wcscmp` nie konwertuje argumenty na małe litery przed ich porównaniem. `_mbsicmp`i `_mbscmp` zachowują się tak samo, z wyjątkiem `_mbscmp` nie konwertuje argumenty na małe litery przed ich porównaniem.  
  
 Należy wywołać [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) dla `_wcsicmp` do pracy z znaki alfabetu łacińskiego 1. Ustawienia regionalne C jest obowiązująca domyślnie tak, na przykład ä nie zostanie porównany równa Ä. Wywołanie `setlocale` z dowolnych ustawień regionalnych innych niż ustawień regionalnych C przed wywołaniem do `_wcsicmp`. W poniższym przykładzie pokazano sposób `_wcsicmp` jest wrażliwe na ustawienia regionalne:  
  
```  
// crt_stricmp_locale.c  
#include <string.h>  
#include <stdio.h>  
#include <locale.h>  
  
int main() {  
   setlocale(LC_ALL,"C");   // in effect by default  
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare fails  
   setlocale(LC_ALL,"");  
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare succeeds  
}  
```  
  
 Alternatywą jest wywołać [_create_locale, _wcreate_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md) i przekazać obiekt ustawień regionalnych zwrócony jako parametr `_wcsicmp_l`.  
  
 Wszystkie te funkcje walidację ich parametrów. Jeśli dowolny `string1` lub `string2` są wskaźniki o wartości null, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają `_NLSCMPERROR` i ustaw `errno` do `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsicmp`|`_stricmp`|`_mbsicmp`|`_wcsicmp`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_stricmp`, `_stricmp_l`|\<String.h >|  
|`_wcsicmp`, `_wcsicmp_l`|\<String.h > lub \<wchar.h >|  
|`_mbsicmp`, `_mbsicmp_l`|\<mbstring.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_stricmp.c  
  
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
      strcpy_s( tmp, _countof(tmp), "less than" );  
   else  
      strcpy_s( tmp, _countof(tmp), "equal to" );  
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );  
  
   // Case insensitive (could use equivalent _stricmp)  
   result = _stricmp( string1, string2 );  
   if( result > 0 )  
      strcpy_s( tmp, _countof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, _countof(tmp), "less than" );  
   else  
      strcpy_s( tmp, _countof(tmp), "equal to" );  
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
 [_memicmp —, _memicmp_l —](../../c-runtime-library/reference/memicmp-memicmp-l.md)   
 [strcmp —, wcscmp —, _mbscmp —](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcoll — funkcje](../../c-runtime-library/strcoll-functions.md)   
 [strncmp —, wcsncmp —, _mbsncmp — _mbsncmp_l —](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [_strnicmp —, _wcsnicmp —, _mbsnicmp —, _strnicmp_l — _wcsnicmp_l —, _mbsnicmp_l —](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr —, wcsrchr —, _mbsrchr — _mbsrchr_l —](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [_strset —, _strset_l —, _wcsset —, _wcsset_l — _mbsset —, _mbsset_l —](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn, wcsspn, _mbsspn, _mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)