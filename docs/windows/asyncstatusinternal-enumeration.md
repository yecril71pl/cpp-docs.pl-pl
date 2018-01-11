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
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bd277fecb0bc63d5ee823af98df8aa298b285964
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)