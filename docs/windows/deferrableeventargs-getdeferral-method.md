---
title: DeferrableEventArgs::GetDeferral — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: ef6dc7c5-b0be-4b85-8507-d3fd97f2185d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2442894c5f7bd85eb94262e776294c1e52a19e01
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883544"
---
# <a name="deferrableeventargsgetdeferral-method"></a>DeferrableEventArgs::GetDeferral — metoda
Pobiera odwołanie do [odroczenia](http://go.microsoft.com/fwlink/p/?linkid=526520) obiekt, który reprezentuje odroczonego zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```  
  
#### <a name="parameters"></a>Parametry  
 `result`  
 Wskaźnik, który będzie odwoływać się do [odroczenia](http://go.microsoft.com/fwlink/p/?linkid=526520) obiekt po zakończeniu wywołania.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.  
  
## <a name="remarks"></a>Uwagi  
 Na przykład kod, zobacz [deferrableeventargs — klasa](../windows/deferrableeventargs-class.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [DeferrableEventArgs, klasa](../windows/deferrableeventargs-class.md)