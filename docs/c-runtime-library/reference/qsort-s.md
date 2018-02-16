---
title: "qsort_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- qsort_s
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
- qsort_s
dev_langs:
- C++
helpviewer_keywords:
- arrays [C++], sorting
- quick-sort algorithm
- qsort_s function
- sorting arrays
ms.assetid: 6ee817b0-4408-4355-a5d4-6605e419ab91
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 31615609ad233f68b6caa78b85cd5efc0ca2dc71
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="qsorts"></a>qsort_s
Wykonuje szybkie sortowanie. Wersja [qsort —](../../c-runtime-library/reference/qsort.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
void qsort_s(  
   void *base,  
   size_t num,  
   size_t width,  
   int (__cdecl *compare )(void *, const void *, const void *),  
   void * context  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `base`  
 Początek tablicy docelowej.  
  
 `num`  
 Rozmiar tablicy w elementach.  
  
 `width`  
 Element rozmiar w bajtach.  
  
 `compare`  
 Porównanie funkcji. Pierwszy argument jest `context` wskaźnika. Drugi argument jest wskaźnikiem do `key` wyszukiwania. Trzeci argument jest wskaźnik do elementu tablicy, która ma zostać porównane z `key`.  
  
 `context`  
 Wskaźnik do kontekstu, która może być dowolny obiekt, który `compare` procedura musi mieć dostęp.  
  
## <a name="remarks"></a>Uwagi  
 `qsort_s` Funkcja implementuje algorytm szybkiego sortowania, aby posortować tablicę `num` z elementów `width` bajtów. Argument `base` wskaźnik do podstawy tablicy ma zostać posortowana. `qsort_s` zastępuje posortowane elementy tej tablicy. Argument `compare` wskaźnik do procedury dostarczone przez użytkownika, który porównuje dwa elementy tablicy i zwraca wartość określającą ich relacji. `qsort_s` wywołania `compare` rutynowych jeden lub więcej razy podczas sortowania, przekazywanie wskaźników do dwóch elementów tablicy przy każdym wywołaniu:  
  
```  
compare( context, (void *) & elem1, (void *) & elem2 );  
```  
  
 Procedura należy porównać elementy, a następnie wróć jedną z następujących wartości:  
  
|Wartość zwracana|Opis|  
|------------------|-----------------|  
|< 0|`elem1` Mniej niż `elem2`|  
|0|`elem1` Wartość równoważna wartości `elem2`|  
|> 0|`elem1` Większa niż `elem2`|  
  
 Tablicy jest sortowany w kolejności rosnącej, zgodnie z definicją przez funkcję porównania. Sortowanie tablicy w kolejności malejącej, należy wycofać rozumieniu "większe niż" i "poniżej" w funkcji porównania.  
  
 Jeśli nieprawidłowe parametry są przekazywane do funkcji, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, a następnie funkcja zwraca i `errno` ma ustawioną wartość `EINVAL`. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|klawisz|base|compare|NUM|szerokość|errno|  
|---------|----------|-------------|---------|-----------|-----------|  
|`NULL`|wszystkie|wszystkie|wszystkie|wszystkie|`EINVAL`|  
|wszystkie|`NULL`|wszystkie|!= 0|wszystkie|`EINVAL`|  
|wszystkie|wszystkie|wszystkie|wszystkie|<= 0|`EINVAL`|  
|wszystkie|wszystkie|`NULL`|wszystkie|wszystkie|`EINVAL`|  
  
 `qsort_s` zachowanie jest takie samo jak `qsort` , ale ma `context` parametru i zestawy `errno`. Przez przekazanie `context` parametru porównanie funkcji za pomocą obiektu wskaźnika uzyskać dostęp do funkcji obiektu lub inne informacje, które nie jest dostępna za pośrednictwem elementu wskaźnika. Dodanie `context` sprawia, że parametr `qsort_s` bardziej bezpieczne, ponieważ `context` pozwala uniknąć błędów wielobieżność wprowadzone za pomocą zmienne statyczne, aby udostępnić informacje udostępniane w `compare` funkcji.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`qsort_s`|\<stdlib.h > i \<search.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
 **Biblioteki:** wszystkie wersje [Biblioteka CRT — funkcje](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `context` parametru w `qsort_s` funkcji. `context` Parametr ułatwia wykonanie sortowania wątkowo. Zamiast używać zmiennych statycznych, które musi zostać zsynchronizowana w celu zapewnienia bezpieczeństwa wątków, Przekaż inną `context` parametr w każdej sortowania. W tym przykładzie obiekt ustawień regionalnych jest używany jako `context` parametru.  
  
```  
// crt_qsort_s.cpp  
// compile with: /EHsc /MT  
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
// so \x00e1 is the German Sharp S in that codepage and \x00a4  
// is the n tilde.  
  
char *array1[] = { "wei\x00e1", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
char *array2[] = { "Espa\x00a4ol", "Espa\x00a4" "a", "espantado" };  
char *array3[] = { "table", "tableux", "tablet" };  
  
#define GERMAN_LOCALE "German_Germany.850"  
#define SPANISH_LOCALE "Spanish_Spain.850"  
#define ENGLISH_LOCALE "English_US.850"  
  
#endif  
  
#ifdef CODEPAGE_1252  
   // If using codepage 1252 (ISO 8859-1, Latin-1), use \x00df  
   // for the German Sharp S and \x001f for the n tilde.  
char *array1[] = { "wei\x00df", "weis", "annehmen", "weizen", "Zeit",  
                   "weit" };  
char *array2[] = { "Espa\x00f1ol", "Espa\x00f1" "a", "espantado" };  
char *array3[] = { "table", "tableux", "tablet" };  
  
#define GERMAN_LOCALE "German_Germany.1252"  
#define SPANISH_LOCALE "Spanish_Spain.1252"  
#define ENGLISH_LOCALE "English_US.1252"  
  
#endif  
  
// The context parameter lets you create a more generic compare.  
// Without this parameter, you would have stored the locale in a  
// static variable, thus making sort_array vulnerable to thread  
// conflicts.  
  
int compare( void *pvlocale, const void *str1, const void *str2)  
{  
    char s1[256];  
    char s2[256];  
    strcpy_s(s1, 256, *(char**)str1);  
    strcpy_s(s2, 256, *(char**)str2);  
    _strlwr_s( s1, sizeof(s1) );  
    _strlwr_s( s2, sizeof(s2) );  
  
    locale& loc = *( reinterpret_cast< locale * > ( pvlocale));  
  
    return use_facet< collate<char> >(loc).compare(s1,   
       &s1[strlen(s1)], s2, &s2[strlen(s2)]);  
  
}  
  
void sort_array(char *array[], int num, locale &loc)  
{  
    qsort_s(array, num, sizeof(char*), compare, &loc);  
}  
  
void print_array(char *a[], int c)  
{  
   for (int i = 0; i < c; i++)  
     printf("%s ", a[i]);  
   printf("\n");  
  
}  
  
void sort_german(void * Dummy)  
{  
   sort_array(array1, 6, locale(GERMAN_LOCALE));  
}  
  
void sort_spanish(void * Dummy)  
{     
   sort_array(array2, 3, locale(SPANISH_LOCALE));       
}  
  
void sort_english(void * Dummy)  
{     
   sort_array(array3, 3, locale(ENGLISH_LOCALE));     
}  
  
int main( )  
{  
  
   int i;  
   HANDLE threads[3];  
  
   printf("Unsorted input:\n");  
   print_array(array1, 6);  
   print_array(array2, 3);  
   print_array(array3, 3);  
  
   // Create several threads that perform sorts in different  
   // languages at the same time.   
  
   threads[0] = reinterpret_cast<HANDLE>(  
                 _beginthread( sort_german , 0, NULL));  
   threads[1] = reinterpret_cast<HANDLE>(  
                 _beginthread( sort_spanish, 0, NULL));  
   threads[2] = reinterpret_cast<HANDLE>(  
                 _beginthread( sort_english, 0, NULL));  
  
   for (i = 0; i < 3; i++)  
   {  
      if (threads[i] == reinterpret_cast<HANDLE>(-1))  
      {  
         printf("Error creating threads.\n");  
         exit(1);  
      }  
   }  
  
   // Wait until all threads have terminated.  
   WaitForMultipleObjects(3, threads, true, INFINITE);  
  
   printf("Sorted output: \n");  
  
   print_array(array1, 6);  
   print_array(array2, 3);  
   print_array(array3, 3);  
  
}  
```  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
  
```  
Unsorted input:  
weiß weis annehmen weizen Zeit weit   
Español España espantado   
table tableux tablet   
Sorted output:   
annehmen weiß weis weit weizen Zeit   
España Español espantado   
table tablet tableux  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch_s —](../../c-runtime-library/reference/bsearch-s.md)   
 [_lsearch_s —](../../c-runtime-library/reference/lsearch-s.md)   
 [qsort](../../c-runtime-library/reference/qsort.md)