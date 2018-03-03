---
title: _com_error::WCode | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error::WCode
dev_langs:
- C++
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 74f79491b9d4f88e19bcd0f7a20c94b26d0f7909
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="comerrorwcode"></a>_com_error::WCode
**Dotyczące firmy Microsoft**  
  
 Pobiera kod błędu 16-bitowych przypisywane do hermetyzowany `HRESULT`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
WORD WCode ( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli `HRESULT` znajduje się w zakresie 0x80040200 do 0x8004FFFF **Kodostrzeżenia** metoda zwraca `HRESULT` minus 0x80040200; w przeciwnym razie zwraca wartość zero.  
  
## <a name="remarks"></a>Uwagi  
 **Kodostrzeżenia** metoda jest używana do cofnąć mapowanie, które odbywa się w modelu COM kod obsługi. Otoka dla **dispinterface** właściwości lub metody wywołuje procedura obsługi pakietów argumentów i wywołania **IDispatch::Invoke**. Po powrocie, jeśli błąd `HRESULT` z `DISP_E_EXCEPTION` jest zwracany, informacje o błędzie jest pobierana z **EXCEPINFO** struktury przekazany do **IDispatch::Invoke**. Kod błędu może być wartością 16-bitowych przechowywane w `wCode` członkiem **EXCEPINFO** struktury lub pełnej 32-bitową wartość w **scode** członkiem **EXCEPINFO**struktury. Jeśli 16-bitowych `wCode` jest zwracany, najpierw musi zostać zmapowana na awarie 32-bitowych `HRESULT`.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error, klasa](../cpp/com-error-class.md)