---
title: Createclassfactory — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
dev_langs:
- C++
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 95d08573515bee89fd86d6b37e3982dde2b29978
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33870476"
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