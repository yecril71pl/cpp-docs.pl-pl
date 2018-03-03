---
title: "Createclassfactory — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
dev_langs:
- C++
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0ac522c2997f6c170e76c462626bb98a290a7dc4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="createclassfactory-function"></a>CreateClassFactory — Funkcja
Tworzy fabrykę tworzy wystąpienia określonej klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template<typename Factory>  
inline HRESULT STDMETHODCALLTYPE CreateClassFactory(  
   _In_ unsigned int *flags,   
   _In_ const CreatorMap* entry,   
   REFIID riid,   
   _Outptr_ IUnknown **ppFactory  
) throw();  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `flags`  
 Kombinacja jednego lub więcej [runtimeclasstype —](../windows/runtimeclasstype-enumeration.md) wartości wyliczenia.  
  
 `entry`  
 Wskaźnik do [creatormap —](../windows/creatormap-structure.md) zawierający inicjowania i rejestracji informacje dotyczące parametru `riid`.  
  
 `riid`  
 Odwołanie do identyfikatora interfejsu.  
  
 `ppFactory`  
 Jeśli ta operacja zakończy się pomyślnie, wskaźnik do fabryki klasy.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.  
  
## <a name="remarks"></a>Uwagi  
 Błąd potwierdzenia jest emitowany, jeśli parametr szablonu `Factory` nie pochodzi z interfejsu IClassFactory.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers::Details, przestrzeń nazw](../windows/microsoft-wrl-wrappers-details-namespace.md)