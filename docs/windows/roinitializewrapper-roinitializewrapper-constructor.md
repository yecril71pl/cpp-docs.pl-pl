---
title: "Roinitializewrapper::roinitializewrapper — Konstruktor | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper::RoInitializeWrapper
dev_langs: C++
ms.assetid: c6f7fb07-14af-4574-9135-cea164607f30
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 88ef0885c49ba7ba28afe40aea25a74eb55d46e9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="roinitializewrapperroinitializewrapper-constructor"></a>RoInitializeWrapper::RoInitializeWrapper — Konstruktor
Inicjuje nowe wystąpienie klasy RoInitializeWrapper.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
RoInitializeWrapper(   RO_INIT_TYPE flags)  
```  
  
#### <a name="parameters"></a>Parametry  
 `flags`  
 Jedno z wyliczeń RO_INIT_TYPE, które określa wsparcie ze środowiska uruchomieniowego systemu Windows.  
  
## <a name="remarks"></a>Uwagi  
 Roinitializewrapper — klasa wywołuje Windows::Foundation::Initialize (*flagi*).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Handlet — klasa](../windows/handlet-class.md)