---
title: "Runtimeclass — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::RuntimeClass
dev_langs: C++
helpviewer_keywords: RuntimeClass class
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e757712b360ff3ed4de12d8236c75a691a1f0c7c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="runtimeclass-class"></a>RuntimeClass — Klasa
Reprezentuje wystąpień klasy, która dziedziczy określona liczba interfejsów i zapewnia określonego środowiska wykonawczego systemu Windows, klasycznego modelu COM i obsługa słabe odwołanie.  
  
 Zwykle pochodzi z typów WRL z `RuntimeClass` ponieważ ta klasa implementuje `AddRef`, `Release`, i `QueryInterface`, i umożliwia zarządzanie ogólnej liczby odwołanie do modułu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <  
   typename I0,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil,  
   typename I3 = Details::Nil,  
   typename I4 = Details::Nil,  
   typename I5 = Details::Nil,  
   typename I6 = Details::Nil,  
   typename I7 = Details::Nil,  
   typename I8 = Details::Nil,  
   typename I9 = Details::Nil  
>  
class RuntimeClass : public Details::RuntimeClass<typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8, I9>::TypeT, RuntimeClassFlags<WinRt>>;  
  
template <  
   unsigned int classFlags,  
   typename I0,  
   typename I1,  
   typename I2,  
   typename I3,  
   typename I4,  
   typename I5,  
   typename I6,  
   typename I7,  
   typename I8  
>  
class RuntimeClass<RuntimeClassFlags<classFlags>, I0, I1, I2, I3, I4, I5, I6, I7, I8> : public Details::RuntimeClass<typename Details::InterfaceListHelper<I0, I1, I2, I3, I4, I5, I6, I7, I8>::TypeT, RuntimeClassFlags<classFlags> >;  
```  
  
#### <a name="parameters"></a>Parametry  
 `I0`  
 Identyfikator zeroth interfejsu. (Wymagane)  
  
 `I1`  
 Pierwszy identyfikator interfejsu. (opcjonalnie)  
  
 `I2`  
 Drugi identyfikatora interfejsu. (opcjonalnie)  
  
 `I3`  
 Trzeci identyfikatora interfejsu. (opcjonalnie)  
  
 `I4`  
 Czwarty identyfikatora interfejsu. (opcjonalnie)  
  
 `I5`  
 Piąty identyfikatora interfejsu. (opcjonalnie)  
  
 `I6`  
 Szóstym identyfikatora interfejsu. (opcjonalnie)  
  
 `I7`  
 Siódmego identyfikatora interfejsu. (opcjonalnie)  
  
 `I8`  
 Identyfikator osiem interfejsu. (opcjonalnie)  
  
 `I9`  
 Dziewiąty identyfikatora interfejsu. (opcjonalnie)  
  
 `classFlags`  
 Kombinacja jednego lub więcej [runtimeclasstype —](../windows/runtimeclasstype-enumeration.md) wartości wyliczenia.  `__WRL_CONFIGURATION_LEGACY__` Makro można definiować w celu zmienić domyślną wartość classFlags dla wszystkich klas środowiska uruchomieniowego w projekcie. Jeśli określone, wystąpień runtimeclass — są domyślne dy-agile. Jeśli nie jest zdefiniowana, runtimeclass — wystąpienia są elastyczne domyślnie. Aby uniknąć niejednoznaczności zawsze podać RuntimeClassType::FtmBase lub RuntimeClassType::InhibitFtmBase.
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Runtimeclass::runtimeclass — Konstruktor](../windows/runtimeclass-runtimeclass-constructor.md)|Inicjuje bieżące wystąpienie klasy runtimeclass — klasa.|  
|[Runtimeclass —:: ~ RuntimeClass — destruktor](../windows/runtimeclass-tilde-runtimeclass-destructor.md)|Deinitializes bieżące wystąpienie klasy runtimeclass — klasa.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `RuntimeClassBase`  
  
 `ImplementsHelper`  
  
 `DontUseNewUseMake`  
  
 `RuntimeClassFlags`  
  
 `RuntimeClassBaseT`  
  
 `RuntimeClass`  
  
 `RuntimeClass`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)
