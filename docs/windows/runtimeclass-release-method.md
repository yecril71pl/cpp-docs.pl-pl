---
title: "RuntimeClass::Release — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::RuntimeClass::Release
dev_langs: C++
helpviewer_keywords: Release method
ms.assetid: 0bd6f9e2-ad90-4de6-adef-a6286f458cb6
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b989b32add712a9f9c97385104ed65a5cc704c9c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="runtimeclassrelease-method"></a>RuntimeClass::Release — Metoda
Wykonuje operację wydania COM w bieżącym obiekcie runtimeclass —.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHOD_(  
   ULONG,  
   Release  
)();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli liczba odwołań wynosi zero, obiekt runtimeclass — zostaje usunięty.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Runtimeclass — klasa](../windows/runtimeclass-class.md)