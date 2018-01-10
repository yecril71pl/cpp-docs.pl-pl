---
title: "ImplementsHelper::CastToUnknown — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::ImplementsHelper::CastToUnknown
dev_langs: C++
helpviewer_keywords: CastToUnknown method
ms.assetid: 5bcfcbaf-c75f-4d43-87b3-0d6838c838d9
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d07e716e085b7f10220f3ed3db4956ae7b1b3cf9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="implementshelpercasttounknown-method"></a>ImplementsHelper::CastToUnknown — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
IUnknown* CastToUnknown();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do powiązanego interfejsu IUnknown.  
  
## <a name="remarks"></a>Uwagi  
 Pobiera wskaźnik do podstawowego interfejsu IUnknown dla bieżącej struktury Implements.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Implementshelper — struktura](../windows/implementshelper-structure.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)