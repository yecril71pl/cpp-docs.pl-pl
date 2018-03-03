---
title: "Runtimeclass — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClass class
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d5c75492b55cd1c238798d3500e2157738c3c58f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="runtimeclass-class"></a>RuntimeClass — Klasa
Reprezentuje klasę WinRT lub COM, która dziedziczy określonych interfejsów i zapewnia określonego środowiska wykonawczego systemu Windows, klasycznego modelu COM i obsługa słabe odwołanie.  
  
Ta klasa udostępnia implementacji standardowego klas WinRT i modelu COM, dostarcza implementację elementu `QueryInterface`, `AddRef`, `Release` itp., zarządza liczebności referencyjnej modułu i obsługuje zapewniające fabryki klasy dla aktywowalnej obiektów.
  
## <a name="syntax"></a>Składnia  
  
```
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```
  
#### <a name="parameters"></a>Parametry  
 `classFlags`  
Parametr opcjonalny. Kombinacja jednego lub więcej [runtimeclasstype —](../windows/runtimeclasstype-enumeration.md) wartości wyliczenia. `__WRL_CONFIGURATION_LEGACY__` Makro można definiować w celu zmienić domyślną wartość classFlags dla wszystkich klas środowiska uruchomieniowego w projekcie. Jeśli określone, runtimeclass — wystąpienia są z systemem innym niż agile domyślnie. Jeśli nie jest zdefiniowana, runtimeclass — wystąpienia są elastyczne domyślnie. Aby uniknąć niejednoznaczności należy zawsze określić Microsoft::WRL::FtmBase w `TInterfaces` lub RuntimeClassType::InhibitFtmBase. Uwaga: Jeśli InhibitFtmBase i ftmbase — są używane obiektu będzie elastyczne.
 
 `TInterfaces`  
Lista interfejsów obiekt implementuje poza IUnknown, IInspectable lub inne interfejsy kontrolowane przez [runtimeclasstype —](../windows/runtimeclasstype-enumeration.md). On również może zawierać listę innych klas pochodzących z szczególnie Microsoft::WRL::FtmBase powoduje, że obiekt elastyczne i spowodować, że plik implementacji interfejsu IMarshal.
  
## <a name="members"></a>Elementy członkowskie  
`RuntimeClassInitialize`Funkcja, która inicjuje obiekt, jeśli makeandinitialize — funkcja szablonu jest używana do konstruowania obiektu. Zwraca wartość S_OK, jeśli obiekt został pomyślnie zainicjowany lub kod błędu modelu COM. Jeśli inicjowanie nie powiodło się. Kod błędu modelu COM są propagowane jako wartość zwracaną makeandinitialize —. Należy pamiętać, że metoda RuntimeClassInitialize nie jest wywoływana, gdy funkcja szablonu upewnij jest używana do konstruowania obiektu.

### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[RuntimeClass::RuntimeClass, konstruktor](../windows/runtimeclass-runtimeclass-constructor.md)|Inicjuje bieżące wystąpienie klasy runtimeclass — klasa.|  
|[RuntimeClass::~RuntimeClass, destruktor](../windows/runtimeclass-tilde-runtimeclass-destructor.md)|Deinitializes bieżące wystąpienie klasy runtimeclass — klasa.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
Jest to szczegóły implementacji.
  
## <a name="requirements"></a>Wymagania  
**Nagłówek:** implements.h  
  
**Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)
