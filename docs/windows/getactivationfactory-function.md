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
ms.openlocfilehash: 2cbb5be3603f79a7df1cb330ca06775357666854
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570314"
---
# <a name="getactivationfactory-function"></a>GetActivationFactory — Funkcja
Pobiera fabrykę aktywacji dla typu określonego przez parametr szablonu.  
  
## <a name="syntax"></a>Składnia  
  
```  
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