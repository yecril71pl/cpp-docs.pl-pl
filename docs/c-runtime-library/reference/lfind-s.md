---
title: "_lfind_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _lfind_s
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- lfind_s
- _lfind_s
dev_langs: C++
helpviewer_keywords:
- linear searching
- keys, finding in arrays
- lfind_s function
- arrays [CRT], searching
- searching, linear
- _lfind_s function
ms.assetid: f1d9581d-5c9d-4222-a31c-a6dfafefa40d
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a49c732be3c1f378340d00c414acee91e6e62978
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="lfinds"></a>_lfind_s
Wykonuje wyszukiwanie liniowe dla określonego klucza. Wersja [_lfind —](../../c-runtime-library/reference/lfind.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
void *_lfind_s(  
   const void *key,  
   const void *base,  
   unsigned int *num,  
   size_t size,  
   int (__cdecl *compare)(void *, const void *, const void *),  
   void * context  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `key`  
 Obiekt do wyszukania.  
  
 `base`  
 Wskaźnik do bazy danych wyszukiwania.  
  
 `num`  
 Liczba elementów tablicy.  
  
 `size`  
 Rozmiar elementów tablicy w bajtach.  
  
 `compare`  
 Wskaźnik do porównania procedury. Pierwszym parametrem jest `context` wskaźnika. Drugi parametr jest wskaźnik do klucza dla wyszukiwania. Trzeci parametr jest wskaźnik do elementu tablicy ma zostać porównane z kluczem.  
  
 `context`  
 Wskaźnik do obiektu, który mogą być używane w funkcji porównania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli klucz zostanie znaleziony, `_lfind_s` zwraca wskaźnik do elementu tablicy w `base` , które odpowiadają `key`. Jeśli klucz nie zostanie znaleziony, `_lfind_s` zwraca `NULL`.  
  
 Jeśli nieprawidłowe parametry są przekazywane do funkcji, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EINVAL` i funkcja zwraca `NULL`.  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|klawisz|base|compare|NUM|size|errno|  
|---------|----------|-------------|---------|----------|-----------|  
|`NULL`|wszystkie|wszystkie|wszystkie|wszystkie|`EINVAL`|  
|wszystkie|`NULL`|wszystkie|!= 0|wszystkie|`EINVAL`|  
|wszystkie|wszystkie|wszystkie|wszystkie|zero|`EINVAL`|  
|wszystkie|wszystkie|`NULL`|Wystąpił|wszystkie|`EINVAL`|  
  
## <a name="remarks"></a>Uwagi  
 `_lfind_s` Funkcja wykonuje wyszukiwanie liniowe dla wartości `key` w tablicy `num` z elementów `width` bajtów. W odróżnieniu od `bsearch_s`, `_lfind_s` nie wymaga tablicy ma zostać posortowana. `base` Argument jest wskaźnik do podstawy tablicy do wyszukania. `compare` Argument jest wskaźnik do procedury dostarczone przez użytkownika, która porównuje dwa elementy tablicy, a następnie zwraca wartość określającą ich relacji. `_lfind_s`wywołania `compare` rutynowych jeden lub więcej razy podczas wyszukiwania przekazywanie `context` wskaźnik i wskaźniki do dwóch elementów tablicy przy każdym wywołaniu. `compare` Procedury należy porównać elementy, a następnie wróć różną od zera (, co oznacza, że elementy różnią się) lub wartość 0 (tzn. elementy są identyczne).  
  
 `_lfind_s`przypomina `_lfind` z wyjątkiem dodawania `context` wskaźnik do argumentów funkcji porównania i listy parametrów funkcji. `context` Wskaźnika może być przydatna, jeśli struktura przeszukane danych jest częścią obiektu i `compare` funkcji ma dostęp do elementów członkowskich obiektu. `compare` Funkcji można rzutować wskaźnika void do odpowiedniego obiektu członków typu i dostępu do tego obiektu. Dodanie `context` sprawia, że parametr `_lfind_s` bardziej bezpieczne, ponieważ dodatkowy kontekst mogą zostać użyte w celu uniknięcia ponownego rozpoczęcia błędów związanych z użyciem zmienne statyczne, aby udostępnić dane `compare` funkcji.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_lfind_s`|\<Search.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_lfind_s.cpp  
// This program uses _lfind_s to search a string array,  
// passing a locale as the context.  
// compile with: /EHsc  
#include <stdlib.h>  
#include <stdio.h>  
#include <search.h>  
#include <process.h>  
#include <locale.h>  
#include <locale>  
#include <windows.h>  
using namespace std;  
  
// The sort order is dependent on the code page.  Use 'chcp' at the  
// command line to change the codepage.  When executing this application,  
// the command prompt codepage must match the codepage used here:  
  
#define CODEPAGE_850  
  
#ifdef CODEPAGE_850  
// Codepage 850 is the OEM codepage used by the command line,  
// so \x00e1 is the German Sharp S  
  
char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
  
#define GERMAN_LOCALE "German_Germany.850"  
  
#endif  
  
#ifdef CODEPAGE_1252  
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df  
   // for the German Sharp S  
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
  
#define GERMAN_LOCALE "German_Germany.1252"  
  
#endif  
  
// The context parameter lets you create a more generic compare.  
// Without this parameter, you would have stored the locale in a  
// static variable, thus making it vulnerable to thread conflicts  
// (if this were a multithreaded program).  
  
int compare( void *pvlocale, const void *str1, const void *str2)  
{  
    char *s1 = *(char**)str1;  
    char *s2 = *(char**)str2;  
  
    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));  
  
    return use_facet< collate<char> >(loc).compare(  
       s1, s1+strlen(s1),  
       s2, s2+strlen(s2) );  
}  
  
void find_it( char *key, char *array[], unsigned int num, locale &loc )  
{  
   char **result = (char **)_lfind_s( &key, array,   
                      &num, sizeof(char *), compare, &loc );  
   if( result )  
      printf( "%s found\n", *result );  
   else  
      printf( "%s not found\n", key );  
}  
  
int main( )  
{  
   find_it( "weit", array1, sizeof(array1)/sizeof(char*), locale(GERMAN_LOCALE) );  
}  
```  
  
```Output  
weit found  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch_s —](../../c-runtime-library/reference/bsearch-s.md)   
 [_lsearch_s —](../../c-runtime-library/reference/lsearch-s.md)   
 [qsort_s —](../../c-runtime-library/reference/qsort-s.md)   
 [_lfind —](../../c-runtime-library/reference/lfind.md)