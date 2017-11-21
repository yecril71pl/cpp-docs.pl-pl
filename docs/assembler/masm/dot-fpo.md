---
title: . FPO | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .FPO
dev_langs: C++
helpviewer_keywords: .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fc26358e1da11ada6b23364576bfedb379bc4030
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fpo"></a>.FPO
. Dyrektywa FPO steruje emisji .debug$ F segmentu lub części rekordów debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
FPO (  
cdwLocals  
,   
cdwParams  
,   
cbProlog  
,   
cbRegs  
,   
fUseBP  
,   
cbFrame  
)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `cdwLocals`  
 Liczba zmiennych lokalnych, wartość bez znaku 32-bitowych.  
  
 `cdwParams`  
 Rozmiar parametrów w dane DWORD, wartość bez znaku 16-bitowych.  
  
 *cbProlog*  
 Liczba bajtów w kod prologu funkcji wartości bez znaku 8-bitowej.  
  
 `cbRegs`  
 Rejestruje numer zapisany.  
  
 `fUseBP`  
 Wskazuje, czy została przydzielona do rejestru EBP. 0 lub 1.  
  
 *cbFrame*  
 Wskazuje typ ramki.  Zobacz [FPO_DATA](http://msdn.microsoft.com/library/windows/desktop/ms679352) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania do dyrektyw](../../assembler/masm/directives-reference.md)