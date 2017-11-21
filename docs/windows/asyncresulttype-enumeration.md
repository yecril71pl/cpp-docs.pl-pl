---
title: "Asyncresulttype — wyliczenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncResultType
dev_langs: C++
helpviewer_keywords: AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 32cb9a76a9415fc051faf11ecd3268d461297450
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType — Wyliczenie
Określa typ wyniku zwracany przez metodę GetResults().  
  
## <a name="syntax"></a>Składnia  
  
```  
enum AsyncResultType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`MultipleResults`|Zestaw wielu wyników, które są prezentowane stopniowo między stan początkowy i przed wywołaniem Close().|  
|`SingleResult`|Jeden wynik, który zobaczy po wystąpieniu zdarzenie ukończenia.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)