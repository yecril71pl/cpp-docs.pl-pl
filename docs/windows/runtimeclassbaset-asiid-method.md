---
title: RuntimeClassBaseT::AsIID, metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 1174db6702fc68b01f60491ef203265bbd6f4c14
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607430"
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
  
### <a name="parameters"></a>Parametry  
 *T*  
 Typ, który implementuje Identyfikatorem określony przez parametr *riid*.  
  
 *Implementuje*  
 Zmiennej o typie określonym przez parametr szablonu *T*.  
  
 *Parametr riid*  
 Identyfikator interfejsu do pobrania.  
  
 *ppvObject*  
 Jeśli operacja się powiedzie, wskaźnik do a wskaźnik do interfejsu określony przez parametr *riid*.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd.  
  
## <a name="remarks"></a>Uwagi  
 Pobiera wskaźnik do określonego interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [RuntimeClassBaseT, struktura](../windows/runtimeclassbaset-structure.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)