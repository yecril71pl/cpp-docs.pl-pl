---
title: HString::Set, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::Set
dev_langs:
- C++
ms.assetid: c9b3d613-95c4-48b0-999d-f5baf0804faf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aecdafe81dcebc7867d30c46be1fee271e60154c
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606400"
---
# <a name="hstringset-method"></a>HString::Set — Metoda
Ustawia wartość bieżącego **HString** obiekt określony ciąg znaków dwubajtowych lub **HString** parametru.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Set(  
          const wchar_t* str) throw();  
HRESULT Set(   
          const wchar_t* str,   
          unsigned int len  
           ) throw();  
HRESULT Set(  
          const HSTRING& hstr  
           ) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *str*  
 Ciąg znaków dwubajtowych.  
  
 *Len*  
 Maksymalna długość *str* parametr, który jest przypisany do bieżącego **HString** obiektu.  
  
 *HSTR*  
 Istniejące **HString** obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [HString, klasa](../windows/hstring-class.md)