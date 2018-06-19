---
title: RuntimeClass::DecrementReference — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::DecrementReference
dev_langs:
- C++
ms.assetid: f5ecfeaa-2865-455b-9208-94a0685fd2c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 660c78ba8a6b3000facc43541249fb6f9856a813
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892686"
---
# <a name="runtimeclassdecrementreference-method"></a>RuntimeClass::DecrementReference — Metoda
Liczba odwołania dla bieżącego obiektu runtimeclass — zmniejsza.  
  
## <a name="syntax"></a>Składnia  
  
```  
ULONG DecrementReference();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [RuntimeClass, klasa](../windows/runtimeclass-class.md)