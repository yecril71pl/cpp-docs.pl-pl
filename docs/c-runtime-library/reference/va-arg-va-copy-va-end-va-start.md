---
title: va_arg, va_copy, va_end, va_start
ms.date: 11/04/2016
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
ms.openlocfilehash: cc0a903f6bc4895f7d2ea6e80990dea94f28c6c2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506356"
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
Typ argumentu do pobrania.

*arg_ptr*<br/>
Wskaźnik do listy argumentów.

*dest*<br/>
Wskaźnik do listy argumentów z *src*

*src*<br/>
Wskaźnik do zainicjowane lista argumentów do skopiowania do *dest*.

*prev_param*<br/>
Parametr, który poprzedza pierwszy argument opcjonalny.

## <a name="return-value"></a>Wartość zwracana

**va_arg** Zwraca bieżące argumentu. **va_copy**, **va_start** i **va_end** nie zwracają wartości.

## <a name="remarks"></a>Uwagi

**Va_arg**, **va_copy**, **va_end**, i **va_start** makra umożliwiają przenośnych dostępu argumenty do funkcji po Funkcja przyjmuje zmienną liczbę argumentów. Istnieją dwie wersje makra: makra zdefiniowane w STDARG. H są zgodne z ISO C99 standard. makra zdefiniowane w VARARGS. H są przestarzałe, ale zostaną zachowane dla zgodności z poprzednimi wersjami z kodem, który został napisany przed standardowa C89 ANSI.

Te makra przyjęto założenie, że funkcja przyjmuje stałą liczbą wymaganych argumentów, a następnie zmienną liczbę argumentów opcjonalnych. Wymagane argumenty są deklarowane jako zwykłe parametrów funkcji i jest możliwy za pośrednictwem nazw parametrów. Argumenty opcjonalne są dostępne za pośrednictwem makra w STDARG. H (lub VARARG). Godz. dla kodu, który został napisany przed standard ANSI C89), który ustawia wskaźnik do pierwszego opcjonalny argument na liście argumentów pobiera argumenty z listy i resetuje wskaźnik po ukończeniu przetwarzanie argumentów.

C standard makra, zdefiniowane w pliku STDARG. Godz., są używane w następujący sposób:

- **va_start** ustawia *arg_ptr* aby pierwszy argument opcjonalne w liście argumentów, który jest przekazywany do funkcji. Argument *arg_ptr* musi mieć **va_list** typu. Argument *prev_param* nazywa się wymaganym parametrem, który bezpośrednio poprzedzające pierwszy argument opcjonalne na liście argumentów. Jeśli *prev_param* jest zadeklarowana z klasą magazynu rejestru jego zachowanie jest niezdefiniowane. **va_start** należy wykonać przed **va_arg** jest używany po raz pierwszy.

- **va_arg** pobiera wartość *typu* z lokalizacji, która została przez *arg_ptr*i zwiększa odczyt *arg_ptr* wskaż następny argument na liście według przy użyciu rozmiaru *typu* ustalenie, gdzie rozpoczyna się następny argument. **va_arg** może być używany w funkcji dowolną liczbę razy, można pobrać argumenty z listy.

- **va_copy** tworzy kopię listy argumentów w jego bieżącym stanie. *Src* parametru już musi zostać zainicjowany z **va_start**; został zaktualizowany przy użyciu **va_arg** wywołań, ale nie musi mieć zresetować za pomocą **va_end** . Następny argument, który jest pobierany przez **va_arg** z *dest* jest taka sama jak następny argument, który jest pobierany z *src*.

- Po pobraniu wszystkich argumentów **va_end** resetuje wskaźnik do **NULL**. **va_end** musi zostać wywołana w każdej listy argumentów, który jest inicjowany za pomocą **va_start** lub **va_copy** zanim funkcja zwróci.

> [!NOTE]
> Makra w VARARGS. H są przestarzałe i są przechowywane tylko wstecznej zgodności z kodem, który został napisany przed standard ANSI C89. We wszystkich innych przypadkach należy użyć makra w STDARGS. H.

Kiedy są kompilowane przy użyciu [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md), programów, które używają tych makr może generować nieoczekiwane wyniki z powodu różnic między systemami typu środowiska uruchomieniowego (języka wspólnego CLR) macierzystych i wspólnego języka. Należy wziąć pod uwagę ten program:

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

Należy zauważyć, że **testit** oczekuje, że jej drugi parametr albo **int** lub **char**<strong>\*</strong>. Argumenty przekazywane są 0xffffffff ( **niepodpisane** **int**, a nie **int**) i **NULL** (faktycznie **int**, a nie **char**<strong>\*</strong>). Gdy program jest skompilowany dla kodu natywnego, produkuje następujące dane wyjściowe:

```Output
-1

(null)
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<stdio.h > i \<stdarg.h >

**Nagłówek przestarzałe:** \<varargs.h >

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

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
