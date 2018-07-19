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
ms.openlocfilehash: 810a5c16df1027aba976bea3c165b19f765d15a6
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941843"
---
# <a name="comerrorwcode"></a>_com_error::WCode
**Microsoft Specific**  
  
 Pobiera kod błędu 16-bitowych zmapowany do zhermetyzowanego HRESULT.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
WORD WCode ( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli wynik HRESULT znajduje się w zakresie 0x80040200 do 0x8004FFFF `WCode` metoda zwróci wartość HRESULT minus 0x80040200; w przeciwnym razie zwraca wartość zero.  
  
## <a name="remarks"></a>Uwagi  
 `WCode` Metoda służy do cofania mapowanie odbywa się w modelu COM kod pomocy technicznej. Otoka dla `dispinterface` właściwość lub metoda wywołuje procedurę obsługi, która pakietów wywołań i argumenty `IDispatch::Invoke`. Po powrocie, jeśli błąd HRESULT DISP_E_EXCEPTION jest zwracana, informacje o błędzie jest pobierana z `EXCEPINFO` struktury przekazany do `IDispatch::Invoke`. Kod błędu mogą być 16-bitową wartość przechowywana w `wCode` członkiem `EXCEPINFO` struktury lub pełnej 32-bitową wartość w `scode` członkiem `EXCEPINFO` struktury. Jeśli 16-bitowych `wCode` ma zostać zwrócona, najpierw musi być zamapowany na 32-bitowych błąd HRESULT.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [_com_error, klasa](../cpp/com-error-class.md)