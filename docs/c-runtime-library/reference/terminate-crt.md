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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 1ec4e27096dd6b5fea089e21c95022542d7adc82
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912222"
---
# <a name="terminate-crt"></a>zakończenie (CRT)

Wywołania [Abort](abort.md) lub funkcja określona przy użyciu **set_terminate**.

## <a name="syntax"></a>Składnia

```C
void terminate( void );
```

## <a name="remarks"></a>Uwagi

Funkcja **Terminate** jest używana z obsługą wyjątków C++ i jest wywoływana w następujących przypadkach:

- Nie można odnaleźć zgodnej procedury obsługi catch dla zgłoszonego wyjątku C++.

- Wyjątek jest zgłaszany przez funkcję destruktora podczas operacji unwindy stosu.

- Stos jest uszkodzony po wystąpieniu wyjątku.

**przerywaj wywołania domyślnie** . [abort](abort.md) Można zmienić to ustawienie domyślne, pisząc własną funkcję zakończenia i wywołując **set_terminate** z nazwą funkcji jako argumentem. **Przerwij** wywołuje ostatnią funkcję podaną jako argument do **set_terminate**. Aby uzyskać więcej informacji, zobacz [Nieobsłużone wyjątki języka C++](../../cpp/unhandled-cpp-exceptions.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**kończyć**|\<> EH. h|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
[Anuluj](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[oczekiwan](unexpected-crt.md)<br/>
