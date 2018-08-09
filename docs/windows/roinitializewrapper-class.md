---
title: RoInitializeWrapper, klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 41eb5e79ca1471fb8c12ffca420a134115fbfcc1
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014042"
---
# <a name="roinitializewrapper-class"></a>RoInitializeWrapper — Klasa
Inicjuje środowisko wykonawcze Windows.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
class RoInitializeWrapper  
```  
  
## <a name="remarks"></a>Uwagi  
 **RoInitializeWrapper** jest wygodne, inicjuje środowiska wykonawczego Windows, która zwraca wartość HRESULT, która wskazuje, czy operacja zakończyła się powodzeniem. Ponieważ wywołuje destruktor klasy `::Windows::Foundation::Uninitialize`, wystąpień **RoInitializeWrapper** musi być zadeklarowana w zakresie globalnym lub najwyższego poziomu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[RoInitializeWrapper::RoInitializeWrapper, konstruktor](../windows/roinitializewrapper-roinitializewrapper-constructor.md)|Inicjuje nowe wystąpienie klasy **RoInitializeWrapper** klasy.|  
|[RoInitializeWrapper::~RoInitializeWrapper, destruktor](../windows/roinitializewrapper-tilde-roinitializewrapper-destructor.md)|Likwiduje bieżące wystąpienie **RoInitializeWrapper** klasy.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator RoInitializeWrapper::HRESULT()](../windows/roinitializewrapper-hresult-parens-operator.md)|Pobiera wartość HRESULT produkowane przez **RoInitializeWrapper** konstruktora.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `RoInitializeWrapper`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)