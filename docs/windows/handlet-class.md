---
title: Handlet — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT
dev_langs:
- C++
helpviewer_keywords:
- HandleT class
ms.assetid: 3822b32a-a426-4d94-a54d-919d4df60ee2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 87a8718971a2da008b03dca1e9653d8454115adb
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570600"
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
  
### <a name="parameters"></a>Parametry  
 *Handletraits —*  
 Wystąpienie [handletraits —](../windows/handletraits-structure.md) stucture, który definiuje typowe cechy dojście.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Publiczne definicje typów  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`Traits`|Synonim dla `HandleTraits`.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HandleT::HandleT, konstruktor](../windows/handlet-handlet-constructor.md)|Inicjuje nowe wystąpienie klasy **HandleT** klasy.|  
|[HandleT::~HandleT, destruktor](../windows/handlet-tilde-handlet-destructor.md)|Wyłącza wystąpienie **HandleT** klasy.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HandleT::Attach, metoda](../windows/handlet-attach-method.md)|Kojarzy określone dojście z bieżącego **HandleT** obiektu.|  
|[HandleT::Close, metoda](../windows/handlet-close-method.md)|Zamyka bieżące **HandleT** obiektu.|  
|[HandleT::Detach, metoda](../windows/handlet-detach-method.md)|Powoduje usunięcie bieżącego **HandleT** obiekt z jego podstawowego dojścia.|  
|[HandleT::Get, metoda](../windows/handlet-get-method.md)|Pobiera wartość podstawowego dojścia.|  
|[HandleT::IsValid, metoda](../windows/handlet-isvalid-method.md)|Wskazuje, czy bieżący **HandleT** obiekt reprezentuje dojście.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HandleT::InternalClose, metoda](../windows/handlet-internalclose-method.md)|Zamyka bieżące **HandleT** obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator HandleT::operator=](../windows/handlet-operator-assign-operator.md)|Przenosi wartość określonego **HandleT** obiekt do bieżącego **HandleT** obiektu.|  
  
### <a name="protected-data-members"></a>Chronione elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HandleT::handle_, składowa danych](../windows/handlet-handle-data-member.md)|Zawiera uchwyt, który jest reprezentowany przez **HandleT** obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `HandleT`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)