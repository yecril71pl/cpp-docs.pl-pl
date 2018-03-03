---
title: "Roinitializewrapper — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5f6330c78a6bbac5f14e94c253f05515e3d29575
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper — Klasa
Inicjuje środowiska uruchomieniowego systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
class RoInitializeWrapper  
```  
  
## <a name="remarks"></a>Uwagi  
 RoInitializeWrapper jest wygodne, która inicjuje środowiska uruchomieniowego systemu Windows i zwraca HRESULT, która wskazuje, czy operacja powiodła się.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[RoInitializeWrapper::RoInitializeWrapper, konstruktor](../windows/roinitializewrapper-roinitializewrapper-constructor.md)|Inicjuje nowe wystąpienie klasy RoInitializeWrapper.|  
|[RoInitializeWrapper::~RoInitializeWrapper, destruktor](../windows/roinitializewrapper-tilde-roinitializewrapper-destructor.md)|Niszczy bieżące wystąpienie klasy RoInitializeWrapper.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator RoInitializeWrapper::HRESULT()](../windows/roinitializewrapper-hresult-parens-operator.md)|Pobiera HRESULT utworzonego przez konstruktora RoInitializeWrapper.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `RoInitializeWrapper`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)