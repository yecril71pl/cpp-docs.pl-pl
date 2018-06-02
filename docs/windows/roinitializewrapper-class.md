---
title: Roinitializewrapper — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/20/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
dev_langs:
- C++
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cac71857e6b472f11d1c9eaba48d181ea78fb456
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705595"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper — Klasa
Inicjuje środowiska uruchomieniowego systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
class RoInitializeWrapper  
```  
  
## <a name="remarks"></a>Uwagi  
 RoInitializeWrapper jest wygodne, która inicjuje środowiska uruchomieniowego systemu Windows i zwraca HRESULT, która wskazuje, czy operacja powiodła się. Ponieważ klasa destruktor wywoła `::Windows::Foundation::Uninitialize`, wystąpień `RoInitializeWrapper` musi być zadeklarowana w zakresie globalnym, ani najwyższego poziomu.  
  
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