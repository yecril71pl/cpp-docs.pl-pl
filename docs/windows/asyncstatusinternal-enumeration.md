---
title: "Asyncstatusinternal — wyliczenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::Details::AsyncStatusInternal
dev_langs: C++
helpviewer_keywords: AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1f014cb2bdf1fa6077dd6922e40e0253b5297c29
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal — Wyliczenie
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
enum AsyncStatusInternal;  
```  
  
## <a name="remarks"></a>Uwagi  
 Określa mapowanie między wewnętrzny wyliczenia stanu operacji asynchronicznych i **Windows::Foundation::AsyncStatus** wyliczenia.  
  
## <a name="members"></a>Elementy członkowskie  
 `_Created`  
 Odpowiednikiem:: Windows::Foundation::AsyncStatus:: utworzone  
  
 `_Started`  
 Odpowiednikiem:: Windows::Foundation::AsyncStatus:: rozpoczęto  
  
 `_Completed`  
 Odpowiednikiem:: Windows::Foundation::AsyncStatus:: ukończone  
  
 `_Cancelled`  
 Odpowiednikiem:: Windows::Foundation::AsyncStatus:: anulowane  
  
 `_Error`  
 Odpowiednikiem:: Windows::Foundation::AsyncStatus::Error  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)