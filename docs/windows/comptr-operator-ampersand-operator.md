---
title: ComPtr::operator&amp; Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 2d77fda6-f4b2-45c1-8a0e-fbc355013531
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0afff1699a4c7a3a14f07967cfb5ba5727ba0320
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461565"
---
# <a name="comptroperatoramp-operator"></a>ComPtr::operator&amp; — Operator
Zwalnia interfejs skojarzony z tym **ComPtr** obiektu, a następnie pobiera adres **ComPtr** obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&()  
  
const Details::ComPtrRef<const WeakRef> operator&() const  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Słabe odwołanie do bieżącego **ComPtr**.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda różni się od [ComPtr::GetAddressOf](../windows/comptr-getaddressof-method.md) w tym, że ta metoda wydaje odniesienie do wskaźnika interfejsu. Użyj `ComPtr::GetAddressOf` po adresu wskaźnik interfejsu, ale nie chcesz zwolnić interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [ComPtr, klasa](../windows/comptr-class.md)