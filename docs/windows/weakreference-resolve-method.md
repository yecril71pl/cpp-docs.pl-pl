---
title: "WeakReference::Resolve — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::WeakReference::Resolve
dev_langs: C++
helpviewer_keywords: Resolve method
ms.assetid: fc65a4b7-48a0-4d64-a793-37f566fdd8e7
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9dc2eef072e64d38b96afd045bae6a9b23d59d94
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="weakreferenceresolve-method"></a>WeakReference::Resolve — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
STDMETHOD(Resolve)  
   (REFIID riid,   
   _Deref_out_opt_ IInspectable **ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 Identyfikatora interfejsu.  
  
 `ppvObject`  
 Po tej operacji zakończeniu kopię bieżącego silne odwołanie, jeśli liczba silne odwołanie jest różna od zera.  
  
## <a name="return-value"></a>Wartość zwracana  
  
-   Wartość S_OK, jeśli operacja zakończy się pomyślnie, a liczba silne odwołanie wynosi zero. `ppvObject` Ustawiono parametr `nullptr`.  
  
-   Wartość S_OK, jeśli operacja zakończy się pomyślnie, a liczba silne odwołanie jest różna od zera. `ppvObject` Parametr ma wartość silne odwołanie.  
  
-   W przeciwnym razie wartość HRESULT, która wskazuje przyczynę ta operacja nie powiodła się.  
  
## <a name="remarks"></a>Uwagi  
 Ustawia określony wskaźnik do bieżącej wartości silne odwołanie, jeśli liczba silne odwołanie jest różna od zera.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Weakreference — Class1](../windows/weakreference-class1.md)   
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)