---
title: _com_error::WCode | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::WCode
dev_langs:
- C++
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1354d490446795e55b41fa0c548e8dd8aa38c71b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32411539"
---
# <a name="comerrorwcode"></a>_com_error::WCode
**Microsoft Specific**  
  
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