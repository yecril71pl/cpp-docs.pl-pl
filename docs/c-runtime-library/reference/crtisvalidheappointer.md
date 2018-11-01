---
title: _CrtIsValidHeapPointer
ms.date: 11/04/2016
apiname:
- _CrtIsValidHeapPointer
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
- CrtlsValidHeapPointer
- _CrtIsValidHeapPointer
helpviewer_keywords:
- _CrtIsValidHeapPointer function
- CrtIsValidHeapPointer function
ms.assetid: caf597ce-1b05-4764-9f37-0197a982bec5
ms.openlocfilehash: cdfb02c622cddc4c86a99f614e469abc527d8845
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662010"
---
# <a name="crtisvalidheappointer"></a>_CrtIsValidHeapPointer

Weryfikuje, czy określony wskaźnik w stercie przydzielone przez niektóre biblioteki wykonawczej języka C, ale niekoniecznie przez bibliotekę CRT obiektu wywołującego. W wersjach CRT przed Visual Studio 2010 weryfikuje, że określony wskaźnik myszy znajduje się w lokalnej sterty (tylko wersja debugowania).

## <a name="syntax"></a>Składnia

```C
int _CrtIsValidHeapPointer(
   const void *userData
);
```

### <a name="parameters"></a>Parametry

*danych użytkownika*<br/>
Wskaźnik do początku blok pamięci przydzielony.

## <a name="return-value"></a>Wartość zwracana

**_Crtisvalidheappointer —** zwraca wartość PRAWDA, jeśli określony wskaźnik znajduje się w stosie współużytkowane przez wszystkie wystąpienia biblioteki CRT. W wersjach CRT przed Visual Studio 2010 to zwraca wartość PRAWDA, jeśli określony wskaźnik myszy znajduje się w lokalnej sterty. W przeciwnym razie funkcja zwraca wartość FALSE.

## <a name="remarks"></a>Uwagi

Aby użyć tej funkcji nie jest zalecane. Począwszy od biblioteki CRT 2010 w usłudze Visual Studio, wszystkie biblioteki CRT udostępnianie jednego systemu operacyjnego sterty, *sterty procesu*. **_Crtisvalidheappointer —** funkcja zgłasza, czy wskaźnik został przydzielony w stercie CRT, ale nie która została przydzielona przez bibliotekę CRT obiektu wywołującego. Na przykład należy wziąć pod uwagę bloku przydzielane przy użyciu programu Visual Studio 2010 biblioteki CRT. Jeśli **_crtisvalidheappointer —** funkcji eksportowanych przez bibliotekę CRT w wersji programu Visual Studio 2012 badania wskaźnik, zwraca wartość TRUE. To nie jest już przydatna testu. W wersjach biblioteki CRT przed Visual Studio 2010 funkcja służy do upewnij się, że adres pamięci określonych w ramach lokalnej sterty. Lokalnej sterty odnosi się do sterty tworzony i zarządzany przez konkretnego wystąpienia biblioteki wykonawczej C. Jeśli biblioteki dołączanej (dynamicznie DLL) zawiera statyczne łącze do biblioteki czasu wykonywania, ma własne wystąpienie sterty czasu wykonywania, a tym samym własnego stosu, niezależnie od aplikacji lokalnej sterty. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_crtisvalidheappointer —** są usuwane podczas przetwarzania wstępnego.

Ponieważ ta funkcja zwraca wartość PRAWDA lub FAŁSZ, mogą być przekazywane do jednego z [_ASSERT](assert-asserte-assert-expr-macros.md) makra, aby utworzyć prosty błąd debugowania mechanizm obsługi. Poniższy przykład powoduje błąd potwierdzenia, jeśli określony adres nie znajduje się w obrębie lokalnej sterty:

```C
_ASSERTE( _CrtIsValidHeapPointer( userData ) );
```

Aby uzyskać więcej informacji o tym, jak **_crtisvalidheappointer —** mogą być używane z innych funkcji debugowania i makr, zobacz [makra dla raportowania](/visualstudio/debugger/macros-for-reporting). Aby dowiedzieć się jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania podstawowej sterty, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtIsValidHeapPointer**|\<crtdbg.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md) tylko.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak sprawdzić, czy pamięć jest prawidłowa w przypadku, gdy jest używany z biblioteki wykonawczej C przed Visual Studio 2010. Ten przykład podano dla użytkowników starszego kodu biblioteki CRT.

```C
// crt_isvalid.c
// This program allocates a block of memory using _malloc_dbg
// and then tests the validity of this memory by calling
// _CrtIsMemoryBlock,_CrtIsValidPointer, and _CrtIsValidHeapPointer.

#include <stdio.h>
#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

#define  TRUE   1
#define  FALSE  0

int main( void )
{
    char *my_pointer;

    // Call _malloc_dbg to include the filename and line number
    // of our allocation request in the header information
    my_pointer = (char *)_malloc_dbg( sizeof(char) * 10,
        _NORMAL_BLOCK, __FILE__, __LINE__ );

    // Ensure that the memory got allocated correctly
    _CrtIsMemoryBlock((const void *)my_pointer, sizeof(char) * 10,
        NULL, NULL, NULL );

    // Test for read/write accessibility
    if (_CrtIsValidPointer((const void *)my_pointer,
        sizeof(char) * 10, TRUE))
        printf("my_pointer has read and write accessibility.\n");
    else
        printf("my_pointer only has read access.\n");

    // Make sure my_pointer is within the local heap
    if (_CrtIsValidHeapPointer((const void *)my_pointer))
        printf("my_pointer is within the local heap.\n");
    else
        printf("my_pointer is not located within the local"
               " heap.\n");

    free(my_pointer);
}
```

```Output
my_pointer has read and write accessibility.
my_pointer is within the local heap.
```

## <a name="see-also"></a>Zobacz także

[Procedury debugowania](../../c-runtime-library/debug-routines.md)<br/>
