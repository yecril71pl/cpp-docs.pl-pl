---
title: "AsyncBase::FireProgress — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::FireProgress
dev_langs: C++
helpviewer_keywords: FireProgress method
ms.assetid: 4512bef6-0ebc-4465-9b8a-4c9dfa82084c
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dd7aa1d66697058d711edd38b3c2eb0679b73c07
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="asyncbasefireprogress-method"></a>AsyncBase::FireProgress — Metoda
Wywołuje Bieżący postęp obsługi zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
void FireProgress(  
   const typename ProgressTraits::Arg2Type arg  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `arg`  
 Metoda obsługi zdarzeń do wywołania.  
  
## <a name="remarks"></a>Uwagi  
 `ProgressTraits`jest pochodną [argtraitshelper — struktura](../windows/argtraitshelper-structure.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Asyncbase — klasa](../windows/asyncbase-class.md)