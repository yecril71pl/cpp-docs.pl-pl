---
title: HStringReference::CopyTo, metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: bb3a23f53dee82dd83f7b1b096702788d69d1f8e
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015891"
---
# <a name="hstringreferencecopyto-method"></a>HStringReference::CopyTo — Metoda
Kopiuje bieżący **HStringReference** obiektu do obiektu HSTRING.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CopyTo(  
   _Out_ HSTRING *str  
   ) const throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *str*  
 HSTRING, który otrzymuje kopię.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje [WindowsDuplicateString](http://msdn.microsoft.com/library/br224634.aspx) funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [HStringReference, klasa](../windows/hstringreference-class.md)