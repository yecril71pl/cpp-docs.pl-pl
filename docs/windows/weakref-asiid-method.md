---
title: WeakRef::AsIID, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: 94e87309-32da-4dbb-8233-e77313a1f448
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 60d2900876d7a9fbee7a193d0575bf3afdf4335b
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012183"
---
# <a name="weakrefasiid-method"></a>WeakRef::AsIID — Metoda
Ustawia określony `ComPtr` parametru wskaźnika do reprezentowania identyfikatora określonego interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT AsIID(  
   REFIID riid,  
   _Out_ ComPtr<IInspectable>* ptr  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *Parametr riid*  
 Identyfikator interfejsu.  
  
 *ptr*  
 Po zakończeniu tej operacji, obiekt, który reprezentuje parametr *riid*.  
  
## <a name="return-value"></a>Wartość zwracana  
  
-   S_OK, jeśli operacja się powiedzie; w przeciwnym razie wartość HRESULT, która wskazuje przyczynę operacja nie powiodła się, a *ptr* ustawiono **nullptr**.  
  
-   S_OK, jeśli operacja zakończy się powodzeniem, ale bieżący **WeakRef** obiekt został zwolniony. Parametr *ptr* ustawiono **nullptr**.  
  
-   S_OK, jeśli operacja zakończy się powodzeniem, ale bieżący **WeakRef** obiektu nie jest tworzony na podstawie parametru *riid*. Parametr *ptr* ustawiono **nullptr**. (Aby uzyskać więcej informacji, zobacz Uwagi).  
  
## <a name="remarks"></a>Uwagi  
 Błąd jest emitowane, jeśli parametr *riid* nie pochodzi od `IInspectable`. Ten błąd zastępuje wartość zwracaną.  
  
 Pierwszy szablon jest formularz, który należy używać w kodzie. Drugi (nie pokazane tutaj, ale zadeklarowana w pliku nagłówkowym) jest wewnętrznych specjalizacji pomocnika, która obsługuje funkcje języka C++, takie jak [automatycznie](../cpp/auto-cpp.md) słowem kluczowym dedukcji typu.  
  
 Począwszy od zestawu Windows 10 SDK, ta metoda nie ustawia **WeakRef** wystąpienia do **nullptr** Jeśli nie można uzyskać słabe odwołanie, więc należy unikać sprawdzanie błędów kodu, który sprawdza **WeakRef** dla **nullptr**. Zamiast tego należy sprawdzić *ptr* dla **nullptr**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [WeakRef, klasa](../windows/weakref-class.md)