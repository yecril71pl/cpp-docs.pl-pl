---
title: va_arg, va_copy, va_end, makra va_start | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- va_arg
- va_end
- va_copy
- va_start
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
apitype: DLLExport
f1_keywords:
- va_arg
- va_start
- va_list
- va_alist
- va_dcl
- va_copy
- va_end
dev_langs:
- C++
helpviewer_keywords:
- variable argument lists, accessing
- va_start macro
- va_arg macro
- va_end macro
- arguments [C++], argument lists
- va_list macro
- va_dcl macro
- va_alist macro
- va_copy macro
ms.assetid: a700dbbd-bfe5-4077-87b6-3a07af74a907
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f634e713bcf87aa6d97ed4e49595e4c0f8b72ab3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417236"
---
# <a name="vaarg-vacopy-vaend-vastart"></a>va_arg, va_copy, va_end, va_start

Uzyskuje dostęp do listy zmiennych argumentów.

## <a name="syntax"></a>Składnia

```C
type va_arg(
   va_list arg_ptr,
   type
);
void va_copy(
   va_list dest,
   va_list src
); // (ISO C99 and later)
void va_end(
   va_list arg_ptr
);
void va_start(
   va_list arg_ptr,
   prev_param
); // (ANSI C89 and later)
void va_start(
   arg_ptr
);  // (deprecated Pre-ANSI C89 standardization version)
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
Typ argumentu, które mają zostać pobrane.

*arg_ptr*<br/>
Wskaźnik do listy argumentów.

*dest*<br/>
Wskaźnik do listę argumentów, aby można było zainicjować z *src*

*src*<br/>
Wskaźnik do zainicjowane listę argumentów, aby skopiować do *dest*.

*prev_param*<br/>
Parametr poprzedzający pierwszy argument opcjonalny.

## <a name="return-value"></a>Wartość zwracana

**va_arg** Zwraca bieżące argumentu. **va_copy**, **va_start —** i **va_end** nie zwracają wartości.

## <a name="remarks"></a>Uwagi

**Va_arg**, **va_copy**, **va_end**, i **va_start —** makra umożliwiają przenośnych uzyskać dostęp do argumentów do funkcji podczas Funkcja przyjmuje zmienną liczbę argumentów. Istnieją dwie wersje makr: makra zdefiniowane w STDARG. H odpowiadają C99 ISO standard. makra zdefiniowane w VARARGS. H są przestarzałe, ale zostaną zachowane dla zgodności z poprzednimi wersjami z kodu napisanego przed standardowe C89 ANSI.

Te makra założono, że funkcja przyjmuje stała liczba wymaganych argumentów, a następnie zmienną liczbę argumentów opcjonalnych. Wymagane argumenty są deklarowane jako zwykłej parametrów funkcji i jest możliwy za pośrednictwem nazwy parametrów. Argumenty opcjonalne są dostępne za pośrednictwem makra w STDARG. H (lub VARARGS. H dla kodu napisanego przed standardu ANSI C89), który ustawia wskaźnik do pierwszego argumentu opcjonalne na liście argumentów pobiera argumenty z listy, a po zakończeniu przetwarzania argument resetuje wskaźnika.

C standard makra, zdefiniowane w STDARG. H, są używane w następujący sposób:

- **Makro va_start** ustawia *arg_ptr* do pierwszego argumentu opcjonalna lista argumentów została przekazana do funkcji. Argument *arg_ptr* musi mieć **va_list** typu. Argument *prev_param* jest nazwą wymaganym parametrem, który bezpośrednio przed pierwszym opcjonalny argument w liście argumentów. Jeśli *prev_param* jest zadeklarowana w klasie magazynu rejestru zachowanie makro jest niezdefiniowane. **Makro va_start** musi być używany przed **va_arg** służy po raz pierwszy.

- **va_arg** pobiera wartość *typu* z lokalizacji, która jest określany przez *arg_ptr*i zwiększa *arg_ptr* wskaż dalej argumentu na liście przez przy użyciu rozmiaru *typu* ustalenie, gdzie argument dalej uruchamiana. **va_arg** może być używana dowolna liczba razy w funkcji do pobrania z listy argumentów.

- **va_copy** tworzy kopię listy argumentów w jego bieżącym stanie. *Src* parametru już musi zostać zainicjowany z **va_start —**; zostały zaktualizowane z **va_arg** wywołuje, ale nie musi być zresetowana z zastosowaniem **va_end** . Argument dalej, które są pobierane przez **va_arg** z *dest* jest taki sam jak argument dalej, które są pobierane z *src*.

- Po pobraniu wszystkich argumentów **va_end** resetuje wskaźnik do **NULL**. **va_end** musi zostać wywołana w każdym listy argumentów, który został zainicjowany przy **va_start —** lub **va_copy** przed funkcja zwraca wartość.

> [!NOTE]
> Makra w VARARGS. H są przestarzałe i są przechowywane tylko dla zapewnienia zgodności z kodu napisanego przed standardu ANSI C89. We wszystkich innych przypadkach użyj makra w STDARGS. H.

Gdy są one kompilowane przy użyciu [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md), programów korzystających z tych makr może generować nieoczekiwane wyniki z powodu różnic między systemami typu środowiska uruchomieniowego (języka wspólnego CLR) natywnych i wspólnego języka. Należy wziąć pod uwagę program:

```C
#include <stdio.h>
#include <stdarg.h>

void testit (int i, ...)
{
    va_list argptr;
    va_start(argptr, i);

    if (i == 0)
    {
        int n = va_arg(argptr, int);
        printf("%d\n", n);
    }
    else
    {
        char *s = va_arg(argptr, char*);
        printf("%s\n", s);
    }

    va_end(argptr);
}

int main()
{
    testit(0, 0xFFFFFFFF); // 1st problem: 0xffffffff is not an int
    testit(1, NULL);       // 2nd problem: NULL is not a char*
}
```

Zwróć uwagę, że **testit** oczekuje, że jej drugi parametr musi mieć przypisany **int** lub **char\***. Argumenty przekazywany są 0xffffffff ( **niepodpisane** **int**, a nie **int**) i **NULL** (faktycznie **int**, a nie **char\***). Gdy program jest kompilowany dla kodu natywnego, tworzy te dane wyjściowe:

```Output
-1

(null)
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<stdio.h > i \<stdarg.h >

**Nagłówek przestarzałe:** \<varargs.h >

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_va.c
// Compile with: cl /W3 /Tc crt_va.c
// The program below illustrates passing a variable
// number of arguments using the following macros:
//      va_start            va_arg              va_copy
//      va_end              va_list

#include <stdio.h>
#include <stdarg.h>
#include <math.h>

double deviation(int first, ...);

int main( void )
{
    /* Call with 3 integers (-1 is used as terminator). */
    printf("Deviation is: %f\n", deviation(2, 3, 4, -1 ));

    /* Call with 4 integers. */
    printf("Deviation is: %f\n", deviation(5, 7, 9, 11, -1));

    /* Call with just -1 terminator. */
    printf("Deviation is: %f\n", deviation(-1));
}

/* Returns the standard deviation of a variable list of integers. */
double deviation(int first, ...)
{
    int count = 0, i = first;
    double mean = 0.0, sum = 0.0;
    va_list marker;
    va_list copy;

    va_start(marker, first);     /* Initialize variable arguments. */
    va_copy(copy, marker);       /* Copy list for the second pass */
    while (i != -1)
    {
        sum += i;
        count++;
        i = va_arg(marker, int);
    }
    va_end(marker);              /* Reset variable argument list. */
    mean = sum ? (sum / count) : 0.0;

    i = first;                  /* reset to calculate deviation */
    sum = 0.0;
    while (i != -1)
    {
        sum += (i - mean)*(i - mean);
        i = va_arg(copy, int);
    }
    va_end(copy);               /* Reset copy of argument list. */
    return count ? sqrt(sum / count) : 0.0;
}
```

```Output
Deviation is: 0.816497
Deviation is: 2.236068
Deviation is: 0.000000
```

## <a name="see-also"></a>Zobacz także

[Dostęp do argumentów](../../c-runtime-library/argument-access.md)<br/>
[vfprintf, _vfprintf_l, vfwprintf, _vfwprintf_l](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)<br/>
