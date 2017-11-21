---
title: "ComPtr::AsWeak — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::AsWeak
dev_langs: C++
helpviewer_keywords: AsWeak method
ms.assetid: 23e29dcd-39cb-423f-abe6-6df4428213bf
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d4bdf9e6f2e3a484af825cea7facc78830b0cc48
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comptrasweak-method"></a>ComPtr::AsWeak — Metoda
Pobiera słabe odwołanie do bieżącego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AsWeak(  
   _Out_ WeakRef* pWeakRef  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pWeakRef`  
 Po tej operacji zakończeniu wskaźnik do obiektu słabe odwołanie.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Comptr — klasa](../windows/comptr-class.md)