---
title: _CrtIsValidHeapPointer
ms.date: 11/04/2016
api_name:
- _CrtIsValidHeapPointer
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
- CrtlsValidHeapPointer
- _CrtIsValidHeapPointer
helpviewer_keywords:
- _CrtIsValidHeapPointer function
- CrtIsValidHeapPointer function
ms.assetid: caf597ce-1b05-4764-9f37-0197a982bec5
ms.openlocfilehash: 9a8746eb2da90ac5515d92113b977011a4647fe6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942381"
---
# <a name="_crtisvalidheappointer"></a>_CrtIsValidHeapPointer

Sprawdza, czy określony wskaźnik znajduje się w stercie przydzielonej przez część biblioteki wykonawczej C, ale niekoniecznie przez bibliotekę CRT obiektu wywołującego. W wersjach CRT przed Visual Studio 2010 sprawdza, czy określony wskaźnik znajduje się w stercie lokalnym (tylko wersja do debugowania).

## <a name="syntax"></a>Składnia

```C
int _CrtIsValidHeapPointer(
   const void *userData
);
```

### <a name="parameters"></a>Parametry

*userData*<br/>
Wskaźnik na początek przydzielony blok pamięci.

## <a name="return-value"></a>Wartość zwracana

**_CrtIsValidHeapPointer** zwraca wartość true, jeśli określony wskaźnik znajduje się w stercie współdzielonym przez wszystkie wystąpienia biblioteki CRT. W wersjach CRT przed Visual Studio 2010 zwraca wartość TRUE, jeśli określony wskaźnik znajduje się na stercie lokalnej. W przeciwnym razie funkcja zwraca wartość FALSE.

## <a name="remarks"></a>Uwagi

Nie zalecamy korzystania z tej funkcji. Począwszy od biblioteki CRT programu Visual Studio 2010, wszystkie biblioteki CRT korzystają z jednej sterty systemu operacyjnego, *sterty procesu*. Funkcja **_CrtIsValidHeapPointer** określa, czy wskaźnik został przydzielony w stercie CRT, ale nie jest przydzielany przez bibliotekę CRT obiektu wywołującego. Rozważmy na przykład blok alokowany przy użyciu wersji programu Visual Studio 2010 biblioteki CRT. Jeśli funkcja **_CrtIsValidHeapPointer** wyeksportowana przez wersję programu Visual Studio 2012 biblioteki CRT testuje wskaźnik, zwraca wartość true. Nie jest to już przydatny test. W wersjach biblioteki CRT przed Visual Studio 2010 funkcja służy do upewnienia się, że określony adres pamięci znajduje się w stercie lokalnej. Sterta lokalna dotyczy sterty utworzonej i zarządzanej przez określone wystąpienie biblioteki wykonawczej C. Jeśli biblioteka dołączana dynamicznie (DLL) zawiera statyczny link do biblioteki wykonawczej, ma własne wystąpienie sterty czasu wykonywania i w związku z tym jego własne sterty niezależnie od sterty lokalnej aplikacji. Gdy [_DEBUG](../../c-runtime-library/debug.md) nie jest zdefiniowany, wywołania **_CrtIsValidHeapPointer** są usuwane podczas przetwarzania wstępnego.

Ponieważ ta funkcja zwraca wartość TRUE lub FALSE, można ją przesłać do jednego z makr [_ASSERT](assert-asserte-assert-expr-macros.md) w celu utworzenia prostego mechanizmu obsługi błędów debugowania. Poniższy przykład powoduje niepowodzenie potwierdzenia, jeśli określony adres nie znajduje się na stercie lokalnej:

```C
_ASSERTE( _CrtIsValidHeapPointer( userData ) );
```

Aby uzyskać więcej informacji o tym, jak **_CrtIsValidHeapPointer** może być używany z innymi funkcjami i makrami debugowania, zobacz [MACROS for Reporting](/visualstudio/debugger/macros-for-reporting). Aby uzyskać informacje o tym, jak bloki pamięci są przydzielane, inicjowane i zarządzane w wersji debugowania sterty podstawowej, zobacz [szczegóły sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_CrtIsValidHeapPointer**|\<crtdbg.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Debuguj wersje wyłącznie [bibliotek uruchomieniowych C](../../c-runtime-library/crt-library-features.md) .

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak sprawdzić, czy pamięć jest prawidłowa, gdy jest używana z bibliotekami uruchomieniowymi C przed programem Visual Studio 2010. Ten przykład jest dostarczany dla użytkowników starszego kodu biblioteki CRT.

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
