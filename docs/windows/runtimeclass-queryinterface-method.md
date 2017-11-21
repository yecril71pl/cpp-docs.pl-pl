---
title: "RuntimeClass::QueryInterface — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::RuntimeClass::QueryInterface
dev_langs: C++
helpviewer_keywords: QueryInterface method
ms.assetid: 8f01f4a1-3fa2-4a8e-88c6-03629236cb9f
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f6d3684c377cc5d56e6e3da78f5b57983f32c2c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="runtimeclassqueryinterface-method"></a>RuntimeClass::QueryInterface — Metoda
Pobiera wskaźnik identyfikator określonego interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
STDMETHOD(  
   QueryInterface  
)  
   (REFIID riid,   
   _Deref_out_ void **ppvObject);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 Identyfikatora interfejsu.  
  
 `ppvObject`  
 Po zakończeniu tego opereation, wskaźnik do interfejsu określonego przez `riid` parametru.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Runtimeclass — klasa](../windows/runtimeclass-class.md)