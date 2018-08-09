---
title: Runtimeclass — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClass class
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7f76695cfe3dcad0f5c835577aa4cc9b7cd3ec62
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017646"
---
# <a name="runtimeclass-class"></a>RuntimeClass — Klasa
Reprezentuje klasę WinRT lub COM, który dziedziczy określonych interfejsów i zapewnia określonego środowiska wykonawczego Windows, Klasyczny model COM i odwołanie tymczasowe wsparcia.  
  
Ta klasa dostarcza implementację standardowy klasy WinRT i COM, zapewniając wykonania `QueryInterface`, `AddRef`, `Release` itp., zarządza licznika odwołań modułu i obsługuje dostarczanie fabryki klas dla obiekty, którą można aktywować.
  
## <a name="syntax"></a>Składnia  
  
```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```
  
### <a name="parameters"></a>Parametry  
 *classFlags*  
Opcjonalny parametr. Kombinacji jednego lub więcej [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) wartości wyliczenia. `__WRL_CONFIGURATION_LEGACY__` Makr można zdefiniować, aby zmienić domyślną wartość classFlags dla wszystkich klas środowiska uruchomieniowego w projekcie. Jeśli zdefiniowane, RuntimeClass wystąpienia są inne niż agile domyślnie. Jeśli nie zostanie zdefiniowana, RuntimeClass wystąpienia są elastyczne domyślnie. Aby uniknąć niejednoznaczności należy zawsze określić `Microsoft::WRL::FtmBase` w `TInterfaces` lub `RuntimeClassType::InhibitFtmBase`. Uwaga: Jeżeli InhibitFtmBase i FtmBase jest używany zarówno obiekt będzie agile.
 
 *TInterfaces*  
Na liście interfejsów obiekt implementuje poza `IUnknown`, `IInspectable` lub innych interfejsów w wartości clientauthtrustmode [RuntimeClassType](../windows/runtimeclasstype-enumeration.md). Również może go wyświetlać innych klas pochodzących z, szczególnie `Microsoft::WRL::FtmBase` na obiekt agile i spowodować, tak aby implementował `IMarshal`.
  
## <a name="members"></a>Elementy członkowskie  
`RuntimeClassInitialize` Funkcja, która inicjuje obiekt, jeśli `MakeAndInitialize` funkcji szablonu jest używana do konstruowania obiektu. Zwraca S_OK, jeśli obiekt został pomyślnie zainicjowany lub kod błędu modelu COM, jeśli inicjowanie nie powiodło się. Kod błędu modelu COM są propagowane jako wartość zwracaną `MakeAndInitialize`. Należy pamiętać, że `RuntimeClassInitialize` metoda nie jest wywoływana, jeśli `Make` funkcji szablonu jest używana do konstruowania obiektu.

### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[RuntimeClass::RuntimeClass, konstruktor](../windows/runtimeclass-runtimeclass-constructor.md)|Inicjuje bieżące wystąpienie klasy RuntimeClass.|  
|[RuntimeClass::~RuntimeClass, destruktor](../windows/runtimeclass-tilde-runtimeclass-destructor.md)|Deinicjuje bieżące wystąpienie klasy RuntimeClass.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
Jest to szczegół implementacji.
  
## <a name="requirements"></a>Wymagania  
**Nagłówek:** implements.h  
  
**Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)