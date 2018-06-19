---
title: Zakończenie (CRT) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- terminate function
- exception handling, termination
ms.assetid: 90e67402-08e9-4b2a-962c-66a8afd3ccb4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c743439b487f091b760e3747c47b471832e1ff3d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408677"
---
# <a name="terminate-crt"></a>zakończenie (CRT)

Wywołania [przerwać](abort.md) lub funkcję należy ją określić za pomocą **set_terminate —**.

## <a name="syntax"></a>Składnia

```C
void terminate( void );
```

## <a name="remarks"></a>Uwagi

**Przerwanie** funkcja jest używana z C++, obsługa wyjątków i jest wywoływana w następujących przypadkach:

- Nie można odnaleźć pasującego obsługi catch dla zwrócony wyjątek C++.

- Wyjątek jest generowane przez funkcję destruktora podczas unwind stosu.

- Stos jest uszkodzony po zgłoszeniu wyjątku.

**przerwanie** wywołania [przerwać](abort.md) domyślnie. To ustawienie domyślne można zmienić, pisanie funkcji zakończenia i wywołanie **set_terminate —** z nazwą funkcji jako jej argument. **przerwanie** wywołuje ostatniej podany jako argument do funkcji **set_terminate —**. Aby uzyskać więcej informacji, zobacz [nieobsługiwanych wyjątków C++](../../cpp/unhandled-cpp-exceptions.md).

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
[set_terminate —](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Nieoczekiwany](unexpected-crt.md)<br/>
