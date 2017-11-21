---
title: "DeferrableEventArgs::GetDeferral — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: ef6dc7c5-b0be-4b85-8507-d3fd97f2185d
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4d43aa6d82f44965e8defda2af3e6455e86cba38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="deferrableeventargsgetdeferral-method"></a>DeferrableEventArgs::GetDeferral — metoda
Pobiera odwołanie do [odroczenia](http://go.microsoft.com/fwlink/?LinkId=526520) obiekt, który reprezentuje odroczonego zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```  
  
#### <a name="parameters"></a>Parametry  
 `result`  
 Wskaźnik, który będzie odwoływać się do [odroczenia](http://go.microsoft.com/fwlink/?LinkId=526520) obiekt po zakończeniu wywołania.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.  
  
## <a name="remarks"></a>Uwagi  
 Na przykład kod, zobacz [deferrableeventargs — klasa](../windows/deferrableeventargs-class.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Deferrableeventargs — klasa](../windows/deferrableeventargs-class.md)