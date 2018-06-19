---
title: qsort_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4aad6fdd96df22375e93207e70dfd0f7cf1f44c4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405604"
---
# <a name="qsorts"></a>qsort_s

Wykonuje szybkie sortowanie. Wersja [qsort —](qsort.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
void qsort_s(
   void *base,
   size_t num,
   size_t width,
   int (__cdecl *compare )(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>Parametry

*podstawowy* Start tablicy docelowej.

*numer* rozmiar w elementach tablicy.

*szerokość* Element rozmiar w bajtach.

*Porównaj* porównanie funkcji. Pierwszy argument jest *kontekstu* wskaźnika. Drugi argument jest wskaźnikiem do *klucza* wyszukiwania. Trzeci argument jest wskaźnik do elementu tablicy, która ma zostać porównane z *klucza*.

*kontekst* wskaźnik do kontekstu, która może być dowolny obiekt, który *porównania* procedura musi mieć dostęp.

## <a name="remarks"></a>Uwagi

**Qsort_s —** funkcja implementuje algorytm szybkiego sortowania, aby posortować tablicę *numer* z elementów *szerokość* bajtów. Argument *podstawowej* wskaźnik do podstawy tablicy ma zostać posortowana. **qsort_s —** zastępuje posortowane elementy tej tablicy. Argument *porównania* wskaźnik do procedury dostarczone przez użytkownika, który porównuje dwa elementy tablicy i zwraca wartość określającą ich relacji. **qsort_s —** wywołania *porównania* rutynowych jeden lub więcej razy podczas sortowania, przekazywanie wskaźników do dwóch elementów tablicy przy każdym wywołaniu:

```C
compare( context, (void *) & elem1, (void *) & elem2 );
```

Procedura należy porównać elementy, a następnie wróć jedną z następujących wartości:

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|**elem1** mniej niż **elem2**|
|0|**elem1** odpowiednikiem **elem2**|
|> 0|**elem1** większa niż **elem2**|

Tablicy jest sortowany w kolejności rosnącej, zgodnie z definicją przez funkcję porównania. Sortowanie tablicy w kolejności malejącej, należy wycofać rozumieniu "większe niż" i "poniżej" w funkcji porównania.

Jeśli nieprawidłowe parametry są przekazywane do funkcji, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, a następnie funkcja zwraca i **errno** ustawiono **einval —**. Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Warunki błędów

|klawisz|base|compare|NUM|szerokość|errno|
|---------|----------|-------------|---------|-----------|-----------|
|**NULL**|wszystkie|wszystkie|wszystkie|wszystkie|**EINVAL —**|
|wszystkie|**NULL**|wszystkie|!= 0|wszystkie|**EINVAL —**|
|wszystkie|wszystkie|wszystkie|wszystkie|<= 0|**EINVAL —**|
|wszystkie|wszystkie|**NULL**|wszystkie|wszystkie|**EINVAL —**|

**qsort_s —** zachowanie jest takie samo jak **qsort —** , ale ma *kontekstu* parametru i zestawy **errno**. Przez przekazanie *kontekstu* parametru porównanie funkcji za pomocą obiektu wskaźnika uzyskać dostęp do funkcji obiektu lub inne informacje, które nie jest dostępna za pośrednictwem elementu wskaźnika. Dodanie *kontekstu* sprawia, że parametr **qsort_s —** bardziej bezpieczne, ponieważ *kontekstu* może służyć do usterki wielobieżność wprowadzone za pomocą zmienne statyczne, aby uniknąć informacje są dostępne do udostępnionego *porównania* funkcji.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**qsort_s**|\<stdlib.h > i \<search.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

**Biblioteki:** wszystkie wersje [Biblioteka CRT — funkcje](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób użycia *kontekstu* parametru w **qsort_s —** funkcji. *Kontekstu* parametr ułatwia wykonanie sortowania wątkowo. Zamiast używać zmiennych statycznych, które musi zostać zsynchronizowana w celu zapewnienia bezpieczeństwa wątków, Przekaż inną *kontekstu* parametr w każdej sortowania. W tym przykładzie obiekt ustawień regionalnych jest używany jako *kontekstu* parametru.

```cpp
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

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
Unsorted input:
weiß weis annehmen weizen Zeit weit
Español España espantado
table tableux tablet
Sorted output:
annehmen weiß weis weit weizen Zeit
España Español espantado
table tablet tableux
```

## <a name="see-also"></a>Zobacz także

[Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort](qsort.md)<br/>
