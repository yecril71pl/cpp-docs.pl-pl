---
title: HString::Operator = — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
dev_langs:
- C++
ms.assetid: 8e68c1ff-bc57-4526-810e-af3c284b4e30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9cc496f4f1c23508b2ebba2788910ff9c9ca2066
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608602"
---
# <a name="hstringoperator-operator"></a>HString::Operator= Operator
Przenosi wartość innego **HString** obiekt do bieżącego **HString** obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HString& operator=(HString&& other) throw()  
```  
  
### <a name="parameters"></a>Parametry  
 *other*  
 Istniejące **HString** obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Wartość istniejącego *innych* obiekt jest kopiowany do bieżącego **HString** obiektu, a następnie *innych* niszczony jest obiekt.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [HString, klasa](../windows/hstring-class.md)