---
title: "tmpnam_s —, _wtmpnam_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- tmpnam_s
- _wtmpnam_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- tmpnam_s
- _wtmpnam_s
- L_tmpnam_s
dev_langs: C++
helpviewer_keywords:
- tmpnam_s function
- file names [C++], creating temporary
- _wtmpnam_s function
- L_tmpnam_s constant
- temporary files, creating
- file names [C++], temporary
- wtmpnam_s function
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b19cbd69d5045ee51b3a1a8ae621300b0ba4b545
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="tmpnams-wtmpnams"></a>tmpnam_s, _wtmpnam_s
Generowania nazw, który służy do tworzenia plików tymczasowych. Są to wersje [tmpnam — i _wtmpnam —](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t tmpnam_s(  
   char * str,  
   size_t sizeInChars   
);  
errno_t _wtmpnam_s(  
   wchar_t *str,  
   size_t sizeInChars   
);  
template <size_t size>  
errno_t tmpnam_s(  
   char (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _wtmpnam_s(  
   wchar_t (&str)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`str`  
 Wskaźnik, w którym będą przechowywane wygenerowana nazwa.  
  
 [in]`sizeInChars`  
 Rozmiar buforu w znakach.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku niepowodzenia obu tych funkcji zwraca 0 w przypadku powodzenia lub numer błędu.  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|||||  
|-|-|-|-|  
|`str`|`sizeInChars`|**Wartość zwracana**|**Zawartość**  `str`|  
|`NULL`|wszystkie|`EINVAL`|Nie zmodyfikowano|  
|nie `NULL` (wskazuje prawidłowy pamięci)|zbyt krótki|`ERANGE`|Nie zmodyfikowano|  
  
 Jeśli `str` jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL` i zwracać `EINVAL`.  
  
## <a name="remarks"></a>Uwagi  
 Każda z tych funkcji zwraca nazwę pliku, który obecnie nie istnieje. `tmpnam_s`Zwraca nazwę unikatową w bieżącym katalogu roboczym. Należy zauważyć, że jeśli nazwa pliku jest pre oczekującego ukośnika odwrotnego i nie informacji ścieżki, takich jak \fname21, oznacza to, że nazwa jest nieprawidłowa dla bieżącego katalogu roboczego.  
  
 Aby uzyskać `tmpnam_s`, można przechowywać tej nazwy pliku wygenerowanego w `str`. Maksymalna długość ciągu zwróconego przez `tmpnam_s` jest `L_tmpnam_s`zdefiniowanej w stdio —. H. Jeśli `str` jest `NULL`, następnie `tmpnam_s` pozostawia wynik w statycznej buforu wewnętrznego. W związku z tym kolejnych wywołań zniszczyć tej wartości. Nazwa wygenerowana przez `tmpnam_s` składa się nazwy pliku generowanych przez program i po pierwszym wywołaniu `tmpnam_s`, rozszerzenie pliku numerów sekwencyjnych w podstawowej 32 (.1 .1vvvvvu, gdy `TMP_MAX_S` w stdio —. Int_max — jest H).  
  
 `tmpnam_s`automatycznie obsługuje argumentów ciągów znaków wielobajtowych zgodnie z potrzebami, rozpoznawanie wielobajtowych sekwencji znaków zgodnie ze strony kodowej OEM uzyskane z systemu operacyjnego. `_wtmpnam_s`jest to wersja znaków dwubajtowych `tmpnam_s`; argumentów i wartości `_wtmpnam_s` są ciągami znaków dwubajtowych. `_wtmpnam_s`i `tmpnam_s` zachowują się tak samo, z wyjątkiem `_wtmpnam_s` nie obsługuje ciągów znaków wielobajtowych.  
  
 W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można wnioskować o długości buforu automatycznie, co eliminuje konieczność określić argument rozmiar. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ttmpnam_s`|`tmpnam_s`|`tmpnam_s`|`_wtmpnam_s`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`tmpnam_s`|\<stdio.h >|  
|`_wtmpnam_s`|\<stdio.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_tmpnam_s.c  
// This program uses tmpnam_s to create a unique filename in the  
// current working directory.   
//  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{     
   char name1[L_tmpnam_s];  
   errno_t err;  
   int i;  
  
   for (i = 0; i < 15; i++)  
   {  
      err = tmpnam_s( name1, L_tmpnam_s );  
      if (err)  
      {  
         printf("Error occurred creating unique filename.\n");  
         exit(1);  
      }  
      else  
      {  
         printf( "%s is safe to use as a temporary file.\n", name1 );  
      }  
   }    
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [_getmbcp —](../../c-runtime-library/reference/getmbcp.md)   
 [— funkcja malloc](../../c-runtime-library/reference/malloc.md)   
 [_setmbcp —](../../c-runtime-library/reference/setmbcp.md)   
 [tmpfile_s —](../../c-runtime-library/reference/tmpfile-s.md)