---
title: "ComPtr::Attach — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::Attach
dev_langs: C++
helpviewer_keywords: Attach method
ms.assetid: 5b911f2d-9830-4dc7-b9e3-527abd55d2c8
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c000fe3bd00b0b16143f538720cc022df3654efe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comptrattach-method"></a>ComPtr::Attach — Metoda
Kojarzy tego comptr — z typu interfejsu, określony przez parametr typu bieżącego szablonu.  
  
## <a name="syntax"></a>Składnia  
  
```  
void Attach(  
   _In_opt_ InterfaceType* other  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `other`  
 Typ interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Comptr — klasa](../windows/comptr-class.md)