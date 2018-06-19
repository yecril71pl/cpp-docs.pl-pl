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
ms.openlocfilehash: e842a13461757e26dd1aed663c590df4c1ba6c74
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883433"
---
# <a name="createactivationfactory-function"></a>CreateActivationFactory — Funkcja
Tworzy fabrykę tworzy wystąpienia określonej klasy, które można aktywować przez środowisko wykonawcze systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Factory>  
   inline HRESULT STDMETHODCALLTYPE CreateActivationFactory(  
      _In_ unsigned int *flags,        _In_ const CreatorMap* entry,   
      REFIID riid,   
     _Outptr_ IUnknown **ppFactory) throw();  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `flags`  
 Kombinacja jednego lub więcej [runtimeclasstype —](../windows/runtimeclasstype-enumeration.md) wartości wyliczenia.  
  
 `entry`  
 Wskaźnik do [creatormap —](../windows/creatormap-structure.md) zawierający inicjowania i rejestracji informacje dotyczące parametru `riid`.  
  
 `riid`  
 Odwołanie do identyfikatora interfejsu.  
  
 `ppFactory`  
 Jeśli ta operacja zakończy się pomyślnie, wskaźnik do aktywacji fabryki.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.  
  
## <a name="remarks"></a>Uwagi  
 Błąd potwierdzenia jest emitowany, jeśli parametr szablonu `Factory` nie pochodzi z interfejsu IActivationFactory.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers::Details, przestrzeń nazw](../windows/microsoft-wrl-wrappers-details-namespace.md)