---
title: setjmp longjump | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f53160a5deeb3ea0db111fc0aae7429b19b7cc86
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703277"
---
# <a name="setjmplongjump"></a>setjmp/longjump

Po włączeniu setjmpex.h lub setjmp.h wszystkie wywołania [setjmp](../c-runtime-library/reference/setjmp.md) lub [longjmp](../c-runtime-library/reference/longjmp.md) spowoduje rozwinięcie, który wywołuje destruktory i na koniec wywołania.  To różni się od x86, w przypadku, gdy tym setjmp.h wyniki w klauzulach finally i destruktory nie są wywoływane.

Wywołanie `setjmp` zachowuje bieżący wskaźnik stosu, rejestrów trwała i MxCsr rejestrów.  Wywołania `longjmp` wróć do najnowszych, ostatnio `setjmp` wywołań lokacji i resetuje wskaźnik stosu, rejestrów trwała i MxCsr rejestruje, do stanu zachowanego przez najnowszych, ostatnio `setjmp` wywołania.

## <a name="see-also"></a>Zobacz też

[Konwencja wywoływania](../build/calling-convention.md)