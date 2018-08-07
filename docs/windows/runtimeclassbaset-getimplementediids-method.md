---
title: RuntimeClassBaseT::GetImplementedIIDS, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
dev_langs:
- C++
helpviewer_keywords:
- GetImplementedIIDS method
ms.assetid: adae54da-521d-4add-87f5-242fbd85f33b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bf29b5db15f88528012914476572cb1ccb21a07c
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39603254"
---
# <a name="runtimeclassbasetgetimplementediids-method"></a>RuntimeClassBaseT::GetImplementedIIDS — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename T>  
__forceinline static HRESULT GetImplementedIIDS(  
   _In_ T* implements,  
   _Out_ ULONG *iidCount,  
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Typ *implementuje* parametru.  
  
 *Implementuje*  
 Wskaźnik do typu określonego przez parametr *T*.  
  
 *iidCount*  
 Maksymalna liczba identyfikatorów interfejsu do pobrania.  
  
 *IID*  
 Jeśli operacja zakończy się pomyślnie, tablicę identyfikatorów implementowana przez typ interfejsu *T*.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd.  
  
## <a name="remarks"></a>Uwagi  
 Pobiera tablicę identyfikatorów, które są implementowane przez określony typ interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [RuntimeClassBaseT, struktura](../windows/runtimeclassbaset-structure.md)