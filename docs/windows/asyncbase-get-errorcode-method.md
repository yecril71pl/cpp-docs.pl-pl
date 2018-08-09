---
title: AsyncBase::get_ErrorCode, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_ErrorCode
dev_langs:
- C++
helpviewer_keywords:
- get_ErrorCode method
ms.assetid: 50b4f8a2-9a21-4ea0-bb5d-7ff524d62aea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dc9ec0c0c68c2941991d0820265b9ee1499bf7cb
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39650836"
---
# <a name="asyncbasegeterrorcode-method"></a>AsyncBase::get_ErrorCode — Metoda
Pobiera kod błędu dla bieżącej operacji asynchronicznej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDMETHOD(  
   get_ErrorCode  
)(HRESULT* errorCode) override;  
```  
  
### <a name="parameters"></a>Parametry  
 *Kod błędu*  
 Lokalizacja przechowywania bieżący kod błędu.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie E_ILLEGAL_METHOD_CALL, jeśli bieżąca operacja asynchroniczna jest zamknięty.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)