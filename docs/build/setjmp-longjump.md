---
title: setjmp longjump | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a3617f70e7c62e1845d8d24e11cebdd7738c507f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="setjmplongjump"></a>setjmp/longjump
Po dołączeniu setjmpex.h lub setjmp.h wszystkich wywołań [setjmp](../c-runtime-library/reference/setjmp.md) lub [longjmp](../c-runtime-library/reference/longjmp.md) spowoduje unwind wywołuje destruktory, który wywołuje finally.  To różni się od x86, gdzie tym setjmp.h wyniki w klauzulach finally i destruktory nie wywołana.  
  
 Wywołanie `setjmp` zachowuje bieżący wskaźnik stosu, trwałej rejestrów i MxCsr rejestrów.  Wywołań `longjmp` powrót do ostatniego `setjmp` wywoływać lokacji i resetuje wskaźnik stosu, trwałej rejestrów i MxCsr rejestruje, do stanu zachowanego przez najnowszej `setjmp` wywołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencja wywoływania](../build/calling-convention.md)