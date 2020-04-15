---
title: qsort_s
ms.date: 4/2/2020
api_name:
- qsort_s
- _o_qsort_s
api_location:
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- qsort_s
helpviewer_keywords:
- arrays [C++], sorting
- quick-sort algorithm
- qsort_s function
- sorting arrays
ms.assetid: 6ee817b0-4408-4355-a5d4-6605e419ab91
ms.openlocfilehash: 6013098199e1b69d03dc9cf2780cbf4376abcc0d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332971"
---
# <a name="qsort_s"></a>qsort_s

Wykonuje szybkie sortowanie. Wersja [qsort](qsort.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*base*<br/>
Początek tablicy docelowej.

*numer*<br/>
Rozmiar tablicy w elementach.

*Szerokość*<br/>
Rozmiar elementu w bajtach.

*Porównać*<br/>
Funkcja porównania. Pierwszym argumentem jest wskaźnik *kontekstu.* Drugi argument jest wskaźnikiem do *klucza* wyszukiwania. Trzeci argument jest wskaźnikiem do elementu tablicy, który ma być porównywany z *kluczem*.

*Kontekście*<br/>
Wskaźnik do kontekstu, który może być dowolny obiekt, który *procedury porównania* musi uzyskać dostęp.

## <a name="remarks"></a>Uwagi

Funkcja **qsort_s** implementuje algorytm szybkiego sortowania do sortowania tablicy elementów *liczbowych,* każdy z bajtów *szerokości.* *Podstawa* argumentu jest wskaźnikiem do podstawy tablicy, która ma zostać posortowana. **qsort_s** zastępuje tę tablicę posortowanymi elementami. *Porównanie* argumentów jest wskaźnikiem do procedury dostarczonej przez użytkownika, która porównuje dwa elementy tablicy i zwraca wartość określającą ich relację. **qsort_s** wywołuje procedurę *porównywania* jeden lub więcej razy podczas sortowania, przekazując wskaźniki do dwóch elementów tablicy w każdym wywołaniu:

```C
compare( context, (void *) & elem1, (void *) & elem2 );
```

Procedura musi porównać elementy, a następnie zwrócić jedną z następujących wartości:

|Wartość zwracana|Opis|
|------------------|-----------------|
|< 0|**elem1** mniej niż **elem2**|
|0|**elem1** odpowiednik **elem2**|
|> 0|**elem1** większy niż **elem2**|

Tablica jest sortowana w kolejności zwiększania, zgodnie z definicją funkcji porównania. Aby posortować tablicę w kolejności malejącej, należy odwrócić poczucie "większe niż" i "mniej niż" w funkcji porównania.

Jeśli nieprawidłowe parametry są przekazywane do funkcji, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie jest dozwolone, funkcja zwraca i **errno** jest ustawiona na **EINVAL**. Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="error-conditions"></a>Warunki błędu

|key|base|compare|num|szerokość|Errno|
|---------|----------|-------------|---------|-----------|-----------|
|**Null**|Wszelki|Wszelki|Wszelki|Wszelki|**Einval**|
|Wszelki|**Null**|Wszelki|!= 0|Wszelki|**Einval**|
|Wszelki|Wszelki|Wszelki|Wszelki|<= 0|**Einval**|
|Wszelki|Wszelki|**Null**|Wszelki|Wszelki|**Einval**|

**qsort_s** ma takie samo zachowanie jak **qsort,** ale ma parametr *kontekstu* i ustawia **errno**. Przekazując parametr *kontekstu,* funkcje porównania można użyć wskaźnika obiektu, aby uzyskać dostęp do funkcji obiektu lub inne informacje niedostępne za pośrednictwem wskaźnika elementu. Dodanie *parametru kontekstu* sprawia, **że qsort_s** bardziej bezpieczne, ponieważ *kontekst* może służyć do uniknięcia błędów reentrancy wprowadzone przy użyciu zmiennych statycznych, aby udostępnić udostępnione informacje do funkcji *porównania.*

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**qsort_s**|\<> i \<search.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

**Biblioteki:** Wszystkie wersje [funkcji biblioteki CRT](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać parametru *kontekstu* w **funkcji qsort_s.** Parametr *context* ułatwia wykonywanie sortowania bezpiecznych dla wątków. Zamiast używać zmiennych statycznych, które muszą być zsynchronizowane w celu zapewnienia bezpieczeństwa wątku, należy przekazać inny parametr *kontekstu* w każdym sortowaniu. W tym przykładzie obiekt ustawień regionalnych jest używany jako parametr *kontekstu.*

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

## <a name="see-also"></a>Zobacz też

[Wyszukiwanie i sortowanie](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
[qsort](qsort.md)<br/>
