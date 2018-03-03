---
title: ComPtr::operator&amp; Operator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 2d77fda6-f4b2-45c1-8a0e-fbc355013531
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cc5234f10a16141fd91193d634f0d306886aff71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="comptroperatoramp-operator"></a>ComPtr::operator&amp; — Operator
Zwalnia skojarzony z tym interfejs `ComPtr` obiekt, a następnie pobiera adres `ComPtr` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&()  
  
const Details::ComPtrRef<const WeakRef> operator&() const  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Słabe odwołanie do bieżącego `ComPtr`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda różni się od [ComPtr::GetAddressOf](../windows/comptr-getaddressof-method.md) , ta metoda zwalnia odwołanie do wskaźnika interfejsu. Użyj `ComPtr::GetAddressOf` Jeżeli adresu wskaźnika interfejsu, ale nie mają być wersji interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [ComPtr, klasa](../windows/comptr-class.md)