---
title: "Roinitializewrapper — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::RoInitializeWrapper
dev_langs: C++
ms.assetid: 4055fbe0-63a7-4c06-b5a0-414fda5640e5
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8b94db5e54089fa91c3b79c185df8b366de07c38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[Roinitializewrapper::roinitializewrapper — Konstruktor](../windows/roinitializewrapper-roinitializewrapper-constructor.md)|Inicjuje nowe wystąpienie klasy RoInitializeWrapper.|  
|[RoInitializeWrapper:: ~ RoInitializeWrapper — destruktor](../windows/roinitializewrapper-tilde-roinitializewrapper-destructor.md)|Niszczy bieżące wystąpienie klasy RoInitializeWrapper.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[RoInitializeWrapper::HRESULT() Operator](../windows/roinitializewrapper-hresult-parens-operator.md)|Pobiera HRESULT utworzonego przez konstruktora RoInitializeWrapper.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `RoInitializeWrapper`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: wrappers — Namespace](../windows/microsoft-wrl-wrappers-namespace.md)