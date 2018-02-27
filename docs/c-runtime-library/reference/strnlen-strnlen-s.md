---
title: "strnlen —, strnlen_s —, wcsnlen —, wcsnlen_s —, _mbsnlen —, _mbsnlen_l —, _mbstrnlen —, _mbstrnlen_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- wcsnlen
- strnlen_s
- _mbstrnlen
- _mbsnlen_l
- _mbstrnlen_l
- strnlen
- wcsnlen_s
- _mbsnlen
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcsnlen
- strnlen_s
- _mbsnlen
- _mbsnlen_l
- _tcsnlen
- _tcscnlen
- _mbstrnlen_l
- wcsnlen_s
- _mbstrnlen
- strnlen
- _tcscnlen_l
dev_langs:
- C++
helpviewer_keywords:
- _tcscnlen function
- _mbstrnlen function
- _mbsnlen_l function
- lengths, strings
- mbstrnlen function
- mbsnlen_l function
- _mbstrnlen_l function
- _tcscnlen_l function
- wcsnlen_l function
- _tcsnlen function
- _mbsnlen function
- strnlen function
- mbsnlen function
- wcsnlen_s function
- strnlen_s function
- mbstrnlen_l function
- wcsnlen function
- string length
- strnlen_l function
ms.assetid: cc05ce1c-72ea-4ae4-a7e7-4464e56e5f80
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 080b1688146d73c4f75d17a4eabe4ab977c45a42
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="strnlen-strnlens-wcsnlen-wcsnlens-mbsnlen-mbsnlenl-mbstrnlen-mbstrnlenl"></a>strnlen — strnlen_s —, wcsnlen —, wcsnlen_s —, _mbsnlen —, _mbsnlen_l —, _mbstrnlen —, _mbstrnlen_l —
Pobiera długość ciągu przy użyciu bieżących ustawień regionalnych lub taki, który został przekazany w. Są to bezpieczniejsza wersje [strlen —, wcslen —, _mbslen —, _mbslen_l —, _mbstrlen —, _mbstrlen_l —](../../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md).  
  
> [!IMPORTANT]
>  `_mbsnlen`, `_mbsnlen_l`, `_mbstrnlen`, i `_mbstrnlen_l` nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
size_t strnlen(  
   const char *str,  
   size_t numberOfElements   
);  
size_t strnlen_s(  
   const char *str,  
   size_t numberOfElements   
);  
size_t wcsnlen(  
   const wchar_t *str,  
   size_t numberOfElements  
);  
size_t wcsnlen_s(  
   const wchar_t *str,  
   size_t numberOfElements  
);  
size_t _mbsnlen(  
   const unsigned char *str,  
   size_t numberOfElements  
);  
size_t _mbsnlen_l(  
   const unsigned char *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
size_t _mbstrnlen(  
   const char *str,  
   size_t numberOfElements  
);  
size_t _mbstrnlen_l(  
   const char *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Ciąg znaków zakończony znakiem null.  
  
 `numberOfElements`  
 Rozmiar buforu ciągu.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Te funkcje zwraca liczbę znaków w ciągu, nie włączając znak końcowy null. Jeśli nie istnieje żadne terminatorem null w pierwszym `numberOfElements` bajtów ciągu (lub znaki dwubajtowe dla `wcsnlen`), następnie `numberOfElements` jest zwracany w celu wskazania błędu; ciągi zakończone wartością null są długości, które są ściśle mniejsza niż `numberOfElements`.  
  
 `_mbstrnlen` i `_mbstrnlen_l` Zwróć -1, jeśli ciąg zawiera nieprawidłowy znak wielobajtowe.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  `strnlen` nie zastępuje ona dla `strlen`; `strnlen` jest przeznaczona do użycia tylko w celu obliczenia rozmiaru przychodzące niezaufanych dane w buforze rozmiaru znane — na przykład pakiet sieciowy. `strnlen` oblicza długość, ale nie objaśniono poza koniec bufora, jeśli jest niezakończony ciąg. W innych sytuacjach należy użyć `strlen`. (To samo dotyczy `wcsnlen`, `_mbsnlen`, i `_mbstrnlen`.)  
  
 Każda z tych funkcji zwraca liczbę znaków w `str`, bez uwzględniania znak końcowy null. Jednak `strnlen` i `strnlen_s` interpretacji ciągu jako ciąg znaków jednobajtowych i w związku z tym zwracana wartość jest zawsze równa liczbie bajtów, nawet jeśli ciąg zawiera znaki wielobajtowe. `wcsnlen` i `wcsnlen_s` wersji znaków dwubajtowych `strnlen` i `strnlen_s` argumenty `wcsnlen` i `wcsnlen_s` są ciągami znaków dwubajtowych i liczbę znaków w jednostki znaków dwubajtowych. W przeciwnym razie `wcsnlen` i `strnlen` zachowują się tak samo, jak `strnlen_s` i `wcsnlen_s`.  
  
 `strnlen`, `wcsnlen`, i `_mbsnlen` nie weryfikują ich parametrów. Jeśli `str` jest `NULL`, nastąpi naruszenie zasad dostępu.  
  
 `strnlen_s` i `wcsnlen_s` walidację ich parametrów. Jeśli `str` jest `NULL`, funkcje zwracają wartość 0.  
  
 `_mbstrnlen` jest również sprawdzane, jego parametrów. Jeśli `str` jest `NULL`, lub jeśli `numberOfElements` jest większa niż `INT_MAX`, `_mbstrnlen` generuje wyjątek nieprawidłowy parametr zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `_mbstrnlen` ustawia `errno` do `EINVAL` i zwraca wartość -1.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsnlen`|`strnlen`|`strnlen`|`wcsnlen`|  
|`_tcscnlen`|`strnlen`|`_mbsnlen`|`wcsnlen`|  
|`_tcscnlen_l`|`strnlen`|`_mbsnlen_l`|`wcsnlen`|  
  
 `_mbsnlen` i `_mbstrnlen` zwraca liczbę znaków wielobajtowych w ciągu znaków wielobajtowych. `_mbsnlen` rozpoznaje wielobajtowych sekwencji znaków zgodnie ze strony kodowe wielobajtowe, który jest obecnie w użyciu lub zgodnie z ustawień regionalnych, który jest przekazywany w; nie sprawdza poprawność znaków wielobajtowych. `_mbstrnlen` sprawdza poprawność znaków wielobajtowych i rozpoznaje wielobajtowych sekwencji znaków. Jeśli ciąg, który jest przekazywany do `_mbstrnlen` zawiera nieprawidłowych znaków wielobajtowych `errno` ma ustawioną wartość `EILSEQ`.  
  
 Wartość wyjściowa jest zagrożony ustawienie `LC_CTYPE` ustawienie kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje te funkcje są identyczne, z tą różnicą, że te nie mają `_l` sufiks Użyj bieżących ustawień regionalnych dla tego zachowania zależnych od ustawień regionalnych i wersje, które mają `_l` sufiks zamiast tego użyj parametru ustawienia regionalne to jest Przekazano. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`strnlen`, `strnlen_s`|\<string.h>|  
|`wcsnlen`, `wcsnlen_s`|\<String.h > lub \<wchar.h >|  
|`_mbsnlen`, `_mbsnlen_l`|\<mbstring.h>|  
|`_mbstrnlen`, `_mbstrnlen_l`|\<stdlib.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```C  
// crt_strnlen.c  
  
#include <string.h>  
  
int main()  
{  
   // str1 is 82 characters long. str2 is 159 characters long   
  
   char* str1 = "The length of a string is the number of characters\n"  
               "excluding the terminating null.";  
   char* str2 = "strnlen takes a maximum size. If the string is longer\n"  
                "than the maximum size specified, the maximum size is\n"  
                "returned rather than the actual size of the string.";  
   size_t len;  
   size_t maxsize = 100;  
  
   len = strnlen(str1, maxsize);  
   printf("%s\n Length: %d \n\n", str1, len);  
  
   len = strnlen(str2, maxsize);  
   printf("%s\n Length: %d \n", str2, len);  
}  
```  
  
```Output  
The length of a string is the number of characters  
excluding the terminating null.  
 Length: 82   
  
strnlen takes a maximum size. If the string is longer  
than the maximum size specified, the maximum size is  
returned rather than the actual size of the string.  
 Length: 100   
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [setLocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strncat —, _strncat_l, wcsncat —, _wcsncat_l _mbsncat —, _mbsncat_l —](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp —, wcsncmp —, _mbsncmp — _mbsncmp_l —](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strcoll — funkcje](../../c-runtime-library/strcoll-functions.md)   
 [strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)   
 [strrchr —, wcsrchr —, _mbsrchr — _mbsrchr_l —](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn, wcsspn, _mbsspn, _mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)