---
title: "Terminatemap — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Details::TerminateMap
dev_langs: C++
helpviewer_keywords: TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: efe6b143c2fe9a48a008f9005244178b436d170e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="terminatemap-function"></a>TerminateMap — Funkcja
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
inline bool TerminateMap(  
   _In_ ModuleBase *module,   
   _In_opt_z_ const wchar_t *serverName,   
    bool forceTerminate) throw()  
```  
  
## <a name="parameters"></a>Parametry  
 `module`  
 A [modułu](../windows/module-class.md).  
  
 `serverName`  
 Nazwa podzbiór fabryki klas w moduł określony przez parametr `module`.  
  
 `forceTerminate`  
 `true`Aby zakończyć klasy fabryki niezależnie od ich są aktywne; `false` nie zakończyć fabryki klas, jeśli wszystkie fabryki jest aktywny.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli wszystkie fabryki klas zostały przerwane; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Zamyka fabryki klas w określonym module.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)