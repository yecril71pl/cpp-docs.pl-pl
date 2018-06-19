---
title: Terminatemap — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
dev_langs:
- C++
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b4787fec0a6b4b9f55c500b66786372945d9a523
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890352"
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
 `true` Aby zakończyć klasy fabryki niezależnie od ich są aktywne; `false` nie zakończyć fabryki klas, jeśli wszystkie fabryki jest aktywny.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli wszystkie fabryki klas zostały przerwane; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Zamyka fabryki klas w określonym module.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)