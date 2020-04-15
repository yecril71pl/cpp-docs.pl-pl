---
title: zakończenie (CRT)
ms.date: 4/2/2020
api_name:
- terminate
- _o_terminate
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- terminate
helpviewer_keywords:
- terminate function
- exception handling, termination
ms.assetid: 90e67402-08e9-4b2a-962c-66a8afd3ccb4
ms.openlocfilehash: 1aa95daeab424c933f10060fb4f87cb317aa188c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362544"
---
# <a name="terminate-crt"></a>zakończenie (CRT)

Wywołuje [przerwanie](abort.md) lub funkcję określoną za pomocą **set_terminate**.

## <a name="syntax"></a>Składnia

```C
void terminate( void );
```

## <a name="remarks"></a>Uwagi

Funkcja **zakończenia** jest używana z obsługą wyjątków języka C++ i jest wywoływana w następujących przypadkach:

- Nie można odnaleźć odpowiedniego programu obsługi catch dla zgłaszanego wyjątku C++.

- Wyjątek jest zgłaszany przez funkcję destruktora podczas odwijania stosu.

- Stos jest uszkodzony po zrzucie wyjątku.

**domyślnie kończyć** [połączenia przerywać.](abort.md) Tę wartość domyślną można zmienić, pisząc własną funkcję zakończenia i wywołując **set_terminate** z nazwą funkcji jako argumentem. **zakończyć** wywołuje ostatnią funkcję podana jako argument do **set_terminate**. Aby uzyskać więcej informacji, zobacz [Nieobsługiwalne wyjątki C++](../../cpp/unhandled-cpp-exceptions.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Zakończyć**|\<eh.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Procedury obsługi wyjątków](../../c-runtime-library/exception-handling-routines.md)<br/>
[Przerwać](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Nieoczekiwane](unexpected-crt.md)<br/>
