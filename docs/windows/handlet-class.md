---
title: "Handlet — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HandleT
dev_langs: C++
helpviewer_keywords: HandleT class
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 293be59e15ca91254cad520a6d7fbf84410ed8e1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[Handlet::handlet — Konstruktor](../windows/handlet-handlet-constructor.md)|Inicjuje nowe wystąpienie klasy handlet —.|  
|[Handlet —:: ~ HandleT — destruktor](../windows/handlet-tilde-handlet-destructor.md)|Deinitializes wystąpienia klasy handlet —.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HandleT::Attach — metoda](../windows/handlet-attach-method.md)|Kojarzy określone dojście z bieżącym obiektem handlet —.|  
|[HandleT::Close — metoda](../windows/handlet-close-method.md)|Zamyka bieżący obiekt handlet —.|  
|[HandleT::Detach — metoda](../windows/handlet-detach-method.md)|Usuwa skojarzenia bieżącego obiektu handlet — z uchwytu podstawowej.|  
|[HandleT::Get — metoda](../windows/handlet-get-method.md)|Pobiera wartość podstawowej dojścia.|  
|[HandleT::IsValid — metoda](../windows/handlet-isvalid-method.md)|Wskazuje, czy bieżący obiekt handlet — reprezentuje dojścia.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HandleT::InternalClose — metoda](../windows/handlet-internalclose-method.md)|Zamyka bieżący obiekt handlet —.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HandleT::operator = — Operator](../windows/handlet-operator-assign-operator.md)|Przenosi bieżący obiekt handlet — wartość określonego obiektu handlet —.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Handlet::handle_ — członek danych](../windows/handlet-handle-data-member.md)|Zawiera dojście reprezentowanego przez obiekt handlet —.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `HandleT`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: wrappers — Namespace](../windows/microsoft-wrl-wrappers-namespace.md)