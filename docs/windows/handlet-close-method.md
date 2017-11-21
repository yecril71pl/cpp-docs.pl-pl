---
title: "HandleT::Close — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
dev_langs: C++
helpviewer_keywords: Close method
ms.assetid: 1b9d597c-abcf-4028-a068-0344560009f6
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 94c246153e5c7e159ccbfe4196ab3692f4138047
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="handletclose-method"></a>HandleT::Close — Metoda
Zamyka bieżący obiekt handlet —.  
  
## <a name="syntax"></a>Składnia  
  
```  
void Close();  
```  
  
## <a name="remarks"></a>Uwagi  
 Dojście źródłową bieżącego handlet — jest zamknięty, a handlet — ustawiono nieprawidłowy stan.  
  
 Jeśli dojście nie zamknięty poprawnie, jest wyjątek w wątku wywołującym.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Handlet — klasa](../windows/handlet-class.md)