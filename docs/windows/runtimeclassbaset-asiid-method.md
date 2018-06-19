---
title: RuntimeClassBaseT::AsIID — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: 90d7df8a-cf9e-4eef-8837-bc1a25f3fa1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 35d218666f785685e95d737574ff44e276ce84b3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892133"
---
# <a name="runtimeclassbasetasiid-method"></a>RuntimeClassBaseT::AsIID — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename T>  
__forceinline static HRESULT AsIID(  
   _In_ T* implements,  
   REFIID riid,  
   _Deref_out_ void **ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ, który implementuje interfejs identyfikator określony przez parametr `riid`.  
  
 `implements`  
 Zmienna typu określony przez parametr szablonu `T`.  
  
 `riid`  
 Identyfikator interfejsu do pobrania.  
  
 `ppvObject`  
 Jeśli ta operacja zakończy się pomyślnie, wskaźnik do a wskaźnik do interfejsu określonej przez parametr `riid`.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT opisującego błąd.  
  
## <a name="remarks"></a>Uwagi  
 Pobiera wskaźnik identyfikator określonego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Runtimeclassbaset — struktura](../windows/runtimeclassbaset-structure.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)