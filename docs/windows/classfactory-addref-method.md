---
title: "ClassFactory::AddRef — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ClassFactory::AddRef
dev_langs: C++
helpviewer_keywords: AddRef method
ms.assetid: 5b091785-dea4-42b6-a502-0db5fc7a5a2e
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 77f1cfa7cf65c301aa1799701446ea157ab08ab5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="classfactoryaddref-method"></a>ClassFactory::AddRef — Metoda
Zwiększa liczbę odwołania dla bieżącego obiektu ClassFactory —.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHOD_(  
   ULONG,  
   AddRef  
)();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT opisujący błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [ClassFactory — klasa](../windows/classfactory-class.md)