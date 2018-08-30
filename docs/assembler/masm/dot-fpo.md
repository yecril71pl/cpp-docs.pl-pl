---
title: . FPO | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .FPO
dev_langs:
- C++
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 234ec5bd703a390d1e2ee60e48d99d346d4aad95
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203116"
---
# <a name="fpo"></a>.FPO
. Dyrektywa FPO steruje emisji rekordów debugowania do sekcji lub .debug$ F segmentu.  
  
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
 Liczba zmiennych lokalnych, wartością bez znaku 32-bitowych.  
  
 `cdwParams`  
 Rozmiar parametrów w dane DWORD, wartością bez znaku 16-bitowych.  
  
 *cbProlog*  
 Liczba bajtów w kodzie prologu funkcji wartością bez znaku 8-bitową.  
  
 `cbRegs`  
 Liczba rejestrów zapisane.  
  
 `fUseBP`  
 Wskazuje, czy został przydzielony do rejestru EBP. 0 lub 1.  
  
 *cbFrame*  
 Wskazuje typ ramki.  Zobacz [FPO_DATA](/windows/desktop/api/winnt/ns-winnt-_fpo_data) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)