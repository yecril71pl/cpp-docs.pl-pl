---
title: setjmp longjump
ms.date: 11/04/2016
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
ms.openlocfilehash: 765cef3f02bed09bed0278aaeecdcdbd55d86b67
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50427901"
---
# <a name="setjmplongjump"></a>setjmp/longjump

Po włączeniu setjmpex.h lub setjmp.h wszystkie wywołania [setjmp](../c-runtime-library/reference/setjmp.md) lub [longjmp](../c-runtime-library/reference/longjmp.md) spowoduje rozwinięcie, który wywołuje destruktory i na koniec wywołania.  To różni się od x86, w przypadku, gdy tym setjmp.h wyniki w klauzulach finally i destruktory nie są wywoływane.

Wywołanie `setjmp` zachowuje bieżący wskaźnik stosu, rejestrów trwała i MxCsr rejestrów.  Wywołania `longjmp` wróć do najnowszych, ostatnio `setjmp` wywołań lokacji i resetuje wskaźnik stosu, rejestrów trwała i MxCsr rejestruje, do stanu zachowanego przez najnowszych, ostatnio `setjmp` wywołania.

## <a name="see-also"></a>Zobacz też

[Konwencja wywoływania](../build/calling-convention.md)