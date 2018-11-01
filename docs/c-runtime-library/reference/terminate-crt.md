---
title: zakończenie (CRT)
ms.date: 11/04/2016
apiname:
- terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- terminate
helpviewer_keywords:
- terminate function
- exception handling, termination
ms.assetid: 90e67402-08e9-4b2a-962c-66a8afd3ccb4
ms.openlocfilehash: 1f655d328b4d97a2989ad49005ed8a9f44fd9d79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438642"
---
# <a name="terminate-crt"></a>zakończenie (CRT)

Wywołania [przerwać](abort.md) funkcji można określić za pomocą **set_terminate**.

## <a name="syntax"></a>Składnia

```C
void terminate( void );
```

## <a name="remarks"></a>Uwagi

**Zakończyć** funkcja jest używana z obsługi wyjątków C++ i jest wywoływana w następujących przypadkach:

- Nie można odnaleźć pasującego obsługi catch zgłoszonego wyjątku C++.

- Wyjątek jest generowany przez funkcję destruktor podczas odwijania stosu.

- Stos jest uszkodzony po zostanie zgłoszony wyjątek.

**Zakończenie** wywołania [przerwać](abort.md) domyślnie. Możesz zmienić to ustawienie domyślne, pisanie funkcji zakończenia i wywołanie **set_terminate** o nazwie funkcji jako argumentem. **Zakończenie** wywołuje funkcję ostatniego podawana jako argument do **set_terminate**. Aby uzyskać więcej informacji, zobacz [nieobsługiwanych wyjątków C++](../../cpp/unhandled-cpp-exceptions.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Zakończenie**|\<eh.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```cpp
// crt_terminate.cpp
// compile with: /EHsc
#include <eh.h>
#include <process.h>
#include <iostream>
using namespace std;

void term_func();

int main()
{
    int i = 10, j = 0, result;
    set_terminate( term_func );
    try
    {
        if( j == 0 )
            throw "Divide by zero!";
        else
            result = i/j;
    }
    catch( int )
    {
        cout << "Caught some integer exception.\n";
    }
    cout << "This should never print.\n";
}

void term_func()
{
    cout << "term_func() was called by terminate().\n";

    // ... cleanup tasks performed here

    // If this function does not exit, abort is called.

    exit(-1);
}
```

```Output
term_func() was called by terminate().
```

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków — procedury](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Nieoczekiwany](unexpected-crt.md)<br/>
