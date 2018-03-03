---
title: "WeakRef::AsIID — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: 94e87309-32da-4dbb-8233-e77313a1f448
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8fdefa73ac14e807c5e4100fd81e1d931f4bf6e6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="weakrefasiid-method"></a>WeakRef::AsIID — Metoda
Ustawia określony parametr wskaźnika comptr — do reprezentowania identyfikator określonego interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AsIID(  
   REFIID riid,  
   _Out_ ComPtr<IInspectable>* ptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 Identyfikatora interfejsu.  
  
 `ptr`  
 Po zakończeniu tej operacji, obiekt, który reprezentuje parametr `riid`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
-   Wartość S_OK, jeśli operacja zakończy się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje przyczynę działanie nie powiodło się, i `ptr` ma ustawioną wartość `nullptr`.  
  
-   Wartość S_OK, jeśli operacja zakończy się pomyślnie, ale bieżący obiekt weakref — zostało już zwolnione. Parametr `ptr` ma ustawioną wartość `nullptr`.  
  
-   Wartość S_OK, jeśli operacja zakończy się pomyślnie, ale bieżący obiekt weakref — nie pochodzi od parametru `riid`. Parametr `ptr` ma ustawioną wartość `nullptr`. (Aby uzyskać więcej informacji, zobacz Uwagi).  
  
## <a name="remarks"></a>Uwagi  
 Błąd jest emitowany, jeśli parametr `riid` nie pochodzi od IInspectable. Ten błąd zastępuje wartość zwracaną.  
  
 Pierwszy szablon jest formularz, która powinna być używana w kodzie. Drugi szablon (nie pokazane, ale zadeklarowana w pliku nagłówka) jest wewnętrznych specjalizacji pomocnika, który obsługuje funkcje języka C++, takie jak [automatycznie](../cpp/auto-cpp.md) wpisz wnioskowanie — słowo kluczowe.  
  
 Począwszy od zestawu SDK systemu Windows 10, ta metoda nie ustawiono wystąpienie weakref — `nullptr` , jeśli nie można uzyskać słabe odwołanie, dlatego należy unikać sprawdzanie błędów kodu, który sprawdza zgodność weakref — dla `nullptr`. Zamiast tego należy sprawdzić `ptr` dla `nullptr`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [WeakRef, klasa](../windows/weakref-class.md)