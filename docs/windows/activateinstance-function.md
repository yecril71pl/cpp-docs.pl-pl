---
title: "Activateinstance — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
dev_langs: C++
helpviewer_keywords: ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1fbf79a38dedf2a7978bdaf1be4bea084283efe9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="activateinstance-function"></a>ActivateInstance — Funkcja
Rejestruje i pobiera wystąpienia określonego typu zdefiniowane w identyfikatora dla określonej klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<  
   typename T  
>  
inline HRESULT ActivateInstance(  
   _In_ HSTRING activatableClassId,  
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ do aktywacji.  
  
 `activatableClassId`  
 Nazwa Identyfikatora klasy, który definiuje parametru `T`.  
  
 `instance`  
 Po zakończeniu tej operacji, odwołania do wystąpienia `T`.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie błąd HRESULT, która wskazuje przyczynę błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Windows::Foundation —  
  
## <a name="see-also"></a>Zobacz też  
 [Windows::Foundation — Namespace](../windows/windows-foundation-namespace.md)