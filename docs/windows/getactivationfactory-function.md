---
title: "Getactivationfactory — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::GetActivationFactory
- client/ABI::Windows::Foundation::GetActivationFactory
- client/Windows::Foundation::GetActivationFactory
dev_langs: C++
helpviewer_keywords: GetActivationFactory function
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6419ef4d48c3f151f8acfb49d40e10853f5d17f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="getactivationfactory-function"></a>GetActivationFactory — Funkcja
Pobiera fabryki aktywacji dla typu określonego przez parametr szablonu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<  
   typename T  
>  
inline HRESULT GetActivationFactory(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Parametr szablonu, który określa typ fabryki aktywacji.  
  
 `activatableClassId`  
 Nazwa klasy, która może tworzyć fabryki aktywacji.  
  
 `factory`  
 Po zakończeniu tej operacji, odwołanie z fabryką aktywacji dla typu `T`.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie błąd HRESULT, która wskazuje, dlaczego ta operacja nie powiodła się.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Windows::Foundation —  
  
## <a name="see-also"></a>Zobacz też  
 [Windows::Foundation, przestrzeń nazw](../windows/windows-foundation-namespace.md)