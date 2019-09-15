---
title: va_arg, va_copy, va_end, va_start
ms.date: 11/04/2016
api_name:
- va_arg
- va_end
- va_copy
- va_start
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 47bd9e3913c6664a52c970dd8a190636683d214e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957364"
---
# <a name="va_arg-va_copy-va_end-va_start"></a>va_arg, va_copy, va_end, va_start

Uzyskuje dostęp do list argumentów zmiennych.

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

*type*<br/>
Typ argumentu do pobrania.

*arg_ptr*<br/>
Wskaźnik na listę argumentów.

*dest*<br/>
Wskaźnik do listy argumentów, które mają zostać zainicjowane z elementu *src*

*SRC*<br/>
Wskaźnik na zainicjowaną listę argumentów do skopiowania do miejsca *docelowego*.

*prev_param*<br/>
Parametr poprzedzający pierwszy argument opcjonalny.

## <a name="return-value"></a>Wartość zwracana

**va_arg** zwraca bieżący argument. **va_copy**, **va_start** i **va_end** nie zwracają wartości.

## <a name="remarks"></a>Uwagi

Makra **va_arg**, **va_copy**, **va_end**i **va_start** zapewniają przenośny sposób dostępu do argumentów do funkcji, gdy funkcja przyjmuje zmienną liczbę argumentów. Istnieją dwie wersje makr: Makra zdefiniowane w STDARG. H jest zgodna ze standardem ISO C99; makra zdefiniowane w VARARGS. H są przestarzałe, ale są zachowywane w celu zachowania zgodności z poprzednimi wersjami z kodem, który został zapisany przed standardem ANSI c89.

W tych makrach przyjęto założenie, że funkcja przyjmuje określoną liczbę wymaganych argumentów, a następnie zmienną liczbę argumentów opcjonalnych. Wymagane argumenty są deklarowane jako parametry zwykłe do funkcji i można do nich uzyskać dostęp za pomocą nazw parametrów. Opcjonalne argumenty są dostępne za pomocą makr w STDARG. H (lub VARARGS. H dla kodu, który został zapisany przed standardem ANSI C89), który ustawia wskaźnik do pierwszego opcjonalnego argumentu na liście argumentów, pobiera argumenty z listy i resetuje wskaźnik po zakończeniu przetwarzania argumentów.

Standardowe makra języka C zdefiniowane w STDARG. H, są używane w następujący sposób:

- **va_start** ustawia *arg_ptr* na pierwszy opcjonalny argument na liście argumentów, które są przekazane do funkcji. Argument *arg_ptr* musi mieć typ **va_list** . Argument *prev_param* jest nazwą wymaganego parametru, który bezpośrednio poprzedza pierwszy opcjonalny argument na liście argumentów. Jeśli *prev_param* jest zadeklarowana z klasą magazynu rejestru, zachowanie makra jest niezdefiniowane. **va_start** należy użyć przed użyciem **va_arg** po raz pierwszy.

- **va_arg** Pobiera wartość *typu* z lokalizacji, która jest określona przez *arg_ptr*, i zwiększa *arg_ptr* , aby wskazywała na następny argument na liście przy użyciu rozmiaru *typu* , aby określić, gdzie zostanie uruchomiony następny argument. do pobierania argumentów z listy **va_arg** można użyć dowolnej liczby razy w funkcji.

- **va_copy** tworzy kopię listy argumentów w bieżącym stanie. Parametr *src* musi już być zainicjowany przy użyciu **va_start**; mógł zostać zaktualizowany przy użyciu wywołań **va_arg** , ale nie może zostać zresetowany przy użyciu **va_end**. Następny argument pobrany przez **va_arg** z miejsca *docelowego* jest taki sam jak następny argument pobrany z elementu *src*.

- Po pobraniu wszystkich argumentów **va_end** resetuje wskaźnik do **wartości null**. **va_end** musi być wywołana dla każdej listy argumentów, która została zainicjowana z **va_start** lub **va_copy** przed zwróceniem funkcji.

> [!NOTE]
> Makra w VARARGS. H są przestarzałe i są zachowywane tylko w celu zapewnienia zgodności z poprzednimi wersjami z kodem, który został zapisany przed standardem ANSI c89. We wszystkich innych przypadkach Użyj makr w STDARGS. C.

Gdy są kompilowane przy użyciu opcji [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md), programy korzystające z tych makr mogą generować nieoczekiwane wyniki ze względu na różnice między systemami typów środowiska uruchomieniowego języka macierzystego (CLR). Weź pod uwagę następujący program:

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

Należy zauważyć, że **testit** oczekuje, że drugi parametr jest typu **int** lub **char**<strong>\*</strong>. Przekazane argumenty to 0xFFFFFFFF ( **niepodpisane** **int**, nie **int**) i **null** (w rzeczywistości **int**, not a **char**<strong>\*</strong>). Gdy program jest kompilowany do kodu natywnego, generuje następujące dane wyjściowe:

```Output
-1

(null)
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** stdio. h > i \<STDARG. h > \<

**Przestarzały nagłówek:** \<> VarArgs. h

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

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
