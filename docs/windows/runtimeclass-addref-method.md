---
title: "RuntimeClass::AddRef — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::RuntimeClass::AddRef
dev_langs: C++
helpviewer_keywords: AddRef method
ms.assetid: 9c705749-680b-4308-bbec-5b601e8e7dbd
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d99623b75aabf17a0f23090889077db5196924ac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="runtimeclassaddref-method"></a>RuntimeClass::AddRef — Metoda
Zwiększa liczbę odwołania dla bieżącego obiektu runtimeclass —.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHOD_(  
   ULONG,  
   AddRef  
)();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Runtimeclass — klasa](../windows/runtimeclass-class.md)