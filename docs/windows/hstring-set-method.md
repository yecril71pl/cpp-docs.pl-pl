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
ms.openlocfilehash: 18ea9eafe3786d0a0df543cde654e1f0270dc8c7
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011770"
---
# <a name="hstringset-method"></a>HString::Set — Metoda
Ustawia wartość bieżącego **HString** obiekt określony ciąg znaków dwubajtowych lub **HString** parametru.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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