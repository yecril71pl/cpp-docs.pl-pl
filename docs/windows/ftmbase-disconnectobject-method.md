---
title: FtmBase::DisconnectObject — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::DisconnectObject
dev_langs:
- C++
helpviewer_keywords:
- DisconnectObject method
ms.assetid: 33253eec-3a65-4e72-8525-0249245a4790
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2501413196e1fd6b8b7a1a4f9985304863e02549
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873004"
---
# <a name="ftmbasedisconnectobject-method"></a>FtmBase::DisconnectObject — Metoda
Wymuszanie zwalnia wszystkie połączenia zewnętrzne do obiektu. Serwer obiektu wywołuje obiektu implementacja tej metody przed zamykanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHODIMP DisconnectObject(  
   __in DWORD dwReserved  
) override;  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwReserved`  
 Zarezerwowane do użytku w przyszłości; musi być równy zero.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ftm.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [FtmBase, klasa](../windows/ftmbase-class.md)