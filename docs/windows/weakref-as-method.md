---
title: WeakRef::As — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::As
dev_langs:
- C++
helpviewer_keywords:
- As method
ms.assetid: 7173da62-b3fe-44d6-aea4-1aa97e69b221
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 034664c91af422aed26f27b924827238b26a9134
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="weakrefas-method"></a>WeakRef::As — Metoda
Ustawia określony parametr wskaźnika comptr — do reprezentowania określonego interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
template<typename U>  
HRESULT As(  
   _Out_ ComPtr<U>* ptr  
);  
  
template<typename U>  
HRESULT As(  
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `U`  
 Identyfikatora interfejsu.  
  
 `ptr`  
 Po zakończeniu tej operacji, obiekt, który reprezentuje parametr `U`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
-   Wartość S_OK, jeśli operacja zakończy się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje przyczynę działanie nie powiodło się, i `ptr` ma ustawioną wartość `nullptr`.  
  
-   Wartość S_OK, jeśli operacja zakończy się pomyślnie, ale bieżący obiekt weakref — zostało już zwolnione. Parametr `ptr` ma ustawioną wartość `nullptr`.  
  
-   Wartość S_OK, jeśli operacja zakończy się pomyślnie, ale bieżący obiekt weakref — nie pochodzi od parametru `U`. Parametr `ptr` ma ustawioną wartość `nullptr`.  
  
## <a name="remarks"></a>Uwagi  
 Błąd jest emitowany, jeśli parametr `U` jest słabe odwołanie, lub nie jest pochodną IInspectable.  
  
 Pierwszy szablon jest formularz, która powinna być używana w kodzie. Drugi szablon jest wewnętrznych specjalizacji pomocnika, który obsługuje funkcje języka C++, takie jak [automatycznie](../cpp/auto-cpp.md) wpisz wnioskowanie — słowo kluczowe.  
  
 Począwszy od zestawu SDK systemu Windows 10, ta metoda nie ustawiono wystąpienie weakref — `nullptr` , jeśli nie można uzyskać słabe odwołanie, dlatego należy unikać sprawdzanie błędów kodu, który sprawdza zgodność weakref — dla `nullptr`. Zamiast tego należy sprawdzić `ptr` dla `nullptr`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [WeakRef, klasa](../windows/weakref-class.md)