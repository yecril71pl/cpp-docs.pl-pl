---
title: "HStringReference::CopyTo — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 179d9b14-1ced-4b16-b297-19ca1e92a462
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f93dd138490834451a665761f4c575a751bfe7ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="hstringreferencecopyto-method"></a>HStringReference::CopyTo — Metoda
Kopie bieżącego hstringreference — obiektu do obiektu HSTRING.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
HRESULT CopyTo(  
   _Out_ HSTRING *str  
   ) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 HSTRING, który odbiera kopii.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje [WindowsDuplicateString](http://msdn.microsoft.com/library/br224634.aspx) funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Hstringreference — klasa](../windows/hstringreference-class.md)