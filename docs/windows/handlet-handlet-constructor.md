---
title: "Handlet::handlet — Konstruktor | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleT::HandleT
dev_langs: C++
helpviewer_keywords: HandleT, constructor
ms.assetid: 4def6891-7e53-46f1-a197-a80e10744dd5
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8cca827bb8ba7fa43619a6e61e2c16ffba5e4563
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="handlethandlet-constructor"></a>HandleT::HandleT — Konstruktor
Inicjuje nowe wystąpienie klasy handlet —.  
  
## <a name="syntax"></a>Składnia  
  
```  
explicit HandleT(  
   typename HandleTraits::Type h =   
      HandleTraits::GetInvalidValue()  
);  
  
HandleT(  
   _Inout_ HandleT&& h  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `h`  
 Uchwyt.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor inicjuje obiekt handlet —, który nie jest prawidłowym dojściem do obiektu. Drugi Konstruktor tworzy nowy obiekt handlet — z parametru `h`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Handlet — klasa](../windows/handlet-class.md)