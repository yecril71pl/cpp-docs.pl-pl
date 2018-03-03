---
title: "Handlet — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT
dev_langs:
- C++
helpviewer_keywords:
- HandleT class
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0ff7261735149abb8db607c5fc0cd4aa837fdfd7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="handlet-class"></a>HandleT — Klasa
Reprezentuje uchwyt do obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename HandleTraits  
>  
class HandleT;  
```  
  
#### <a name="parameters"></a>Parametry  
 `HandleTraits`  
 Wystąpienie [handletraits —](../windows/handletraits-structure.md) stucture, który definiuje wspólne cechy dojścia.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`Traits`|Jest to synonim `HandleTraits`.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HandleT::HandleT, konstruktor](../windows/handlet-handlet-constructor.md)|Inicjuje nowe wystąpienie klasy handlet —.|  
|[HandleT::~HandleT, destruktor](../windows/handlet-tilde-handlet-destructor.md)|Deinitializes wystąpienia klasy handlet —.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HandleT::Attach, metoda](../windows/handlet-attach-method.md)|Kojarzy określone dojście z bieżącym obiektem handlet —.|  
|[HandleT::Close, metoda](../windows/handlet-close-method.md)|Zamyka bieżący obiekt handlet —.|  
|[HandleT::Detach, metoda](../windows/handlet-detach-method.md)|Usuwa skojarzenia bieżącego obiektu handlet — z uchwytu podstawowej.|  
|[HandleT::Get, metoda](../windows/handlet-get-method.md)|Pobiera wartość podstawowej dojścia.|  
|[HandleT::IsValid, metoda](../windows/handlet-isvalid-method.md)|Wskazuje, czy bieżący obiekt handlet — reprezentuje dojścia.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HandleT::InternalClose, metoda](../windows/handlet-internalclose-method.md)|Zamyka bieżący obiekt handlet —.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator HandleT::operator=](../windows/handlet-operator-assign-operator.md)|Przenosi bieżący obiekt handlet — wartość określonego obiektu handlet —.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HandleT::handle_, składowa danych](../windows/handlet-handle-data-member.md)|Zawiera dojście reprezentowanego przez obiekt handlet —.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `HandleT`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)