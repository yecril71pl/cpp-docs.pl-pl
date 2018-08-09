---
title: Getactivationfactory — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::GetActivationFactory
- client/ABI::Windows::Foundation::GetActivationFactory
- client/Windows::Foundation::GetActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- GetActivationFactory function
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3fe0d03ead29362ea2926f6326557df2ba6a2cd9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649250"
---
# <a name="getactivationfactory-function"></a>GetActivationFactory — Funkcja
Pobiera fabrykę aktywacji dla typu określonego przez parametr szablonu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template<typename T>  
inline HRESULT GetActivationFactory(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *T*  
 Parametr szablonu, który określa typ fabryką aktywacji.  
  
 *activatableClassId*  
 Nazwa klasy, która może spowodować fabryką aktywacji.  
  
 *Fabryka*  
 Po zakończeniu tej operacji, odwołanie do aktywacji fabryki dla typu *T*.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie błąd HRESULT, która wskazuje, dlaczego ta operacja nie powiodła się.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Windows::Foundation  
  
## <a name="see-also"></a>Zobacz też  
 [Windows::Foundation, przestrzeń nazw](../windows/windows-foundation-namespace.md)