---
title: WYWOŁANIE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Invoke
dev_langs:
- C++
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27c18c83b623ce1a22ffcb5e1a9f1ce98ee6eb20
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32055173"
---
# <a name="invoke"></a>INVOKE
Wywołuje procedurę na adres podany przez *wyrażenie*, przekazywanie argumentów na stosie lub w rejestrach zgodnie ze standardowej konwencji wywoływania typu języka.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
INVOKE   
expression [[, arguments]]  
```  
  
## <a name="remarks"></a>Uwagi  
 Każdy argument przekazany do procedury może być wyrażenie, parę rejestru lub wyrażenie adresu (wyrażenie poprzedzone `ADDR`).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)