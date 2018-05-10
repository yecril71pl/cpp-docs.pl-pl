---
title: HStringReference::CopyTo — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 179d9b14-1ced-4b16-b297-19ca1e92a462
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f65c08cad438328eb1a0e15495774dbde6845f4d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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
 [HStringReference, klasa](../windows/hstringreference-class.md)