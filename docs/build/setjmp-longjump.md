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
ms.openlocfilehash: 55cf6a2503367777464f09f92e3e3614c3d9f11b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="setjmplongjump"></a>setjmp/longjump
Po dołączeniu setjmpex.h lub setjmp.h wszystkich wywołań [setjmp](../c-runtime-library/reference/setjmp.md) lub [longjmp](../c-runtime-library/reference/longjmp.md) spowoduje unwind wywołuje destruktory, który wywołuje finally.  To różni się od x86, gdzie tym setjmp.h wyniki w klauzulach finally i destruktory nie wywołana.  
  
 Wywołanie `setjmp` zachowuje bieżący wskaźnik stosu, trwałej rejestrów i MxCsr rejestrów.  Wywołań `longjmp` powrót do ostatniego `setjmp` wywoływać lokacji i resetuje wskaźnik stosu, trwałej rejestrów i MxCsr rejestruje, do stanu zachowanego przez najnowszej `setjmp` wywołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencja wywoływania](../build/calling-convention.md)