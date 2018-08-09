---
title: Createactivationfactory — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- CreateActivationFactory function
ms.assetid: a1a53e04-6757-4faf-a4c8-ecf06e43b959
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 780fd8b6866af05007d9c99e3165b149eab956bd
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642906"
---
# <a name="createactivationfactory-function"></a>CreateActivationFactory — Funkcja
Tworzy fabrykę, która tworzy wystąpienia określonej klasy, które można uaktywnić przez środowisko wykonawcze Windows.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Factory>  
   inline HRESULT STDMETHODCALLTYPE CreateActivationFactory(  
      _In_ unsigned int *flags,        _In_ const CreatorMap* entry,   
      REFIID riid,   
     _Outptr_ IUnknown **ppFactory) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *flagi*  
 Kombinacji jednego lub więcej [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) wartości wyliczenia.  
  
 *entry*  
 Wskaźnik do [creatormap —](../windows/creatormap-structure.md) zawierający informacje o parametrze inicjowania i rejestracji *riid*.  
  
 *Parametr riid*  
 Odwołanie do identyfikatora interfejsu.  
  
 *ppFactory*  
 Jeśli operacja zakończy się pomyślnie, wskaźnik do aktywacji fabryki.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.  
  
## <a name="remarks"></a>Uwagi  
 Błąd potwierdzenia jest emitowane, jeśli parametr szablonu *fabryki* nie pochodzi z interfejsu `IActivationFactory`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers::Details, przestrzeń nazw](../windows/microsoft-wrl-wrappers-details-namespace.md)