---
title: "ActivationFactory::AddRef — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ActivationFactory::AddRef
dev_langs: C++
helpviewer_keywords: AddRef method
ms.assetid: dfe96189-ddbe-410a-9f8d-5d8ecc8cc7e6
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 681c473c53fff5637d07f990df3f7eee78f65ec7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="activationfactoryaddref-method"></a>ActivationFactory::AddRef — Metoda
Zwiększa liczbę odwołanie do bieżącego obiektu activationfactory —.  
  
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
 [Activationfactory — klasa](../windows/activationfactory-class.md)