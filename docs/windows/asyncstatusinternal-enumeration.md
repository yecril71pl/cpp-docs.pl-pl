---
title: Asyncstatusinternal — wyliczenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::AsyncStatusInternal
dev_langs:
- C++
helpviewer_keywords:
- AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a68189c461453dc72585ff4034df5ba69bb41bd5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464879"
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal — Wyliczenie
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
enum AsyncStatusInternal;  
```  
  
## <a name="remarks"></a>Uwagi  
 Określa mapowanie między wewnętrznego wyliczenia stanu operacji asynchronicznych i `Windows::Foundation::AsyncStatus` wyliczenia.  
  
## <a name="members"></a>Elementy członkowskie  
 *_Created*  
 Odpowiednikiem:: Windows::Foundation::AsyncStatus:: utworzone  
  
 *_Started*  
 Odpowiednikiem:: Windows::Foundation::AsyncStatus:: pracę  
  
 *_Completed*  
 Odpowiednikiem:: Windows::Foundation::AsyncStatus:: ukończone  
  
 *_Cancelled*  
 Odpowiednikiem:: Windows::Foundation::AsyncStatus:: anulowane  
  
 *_Błąd*  
 Odpowiednikiem:: Windows::Foundation::AsyncStatus::Error  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)