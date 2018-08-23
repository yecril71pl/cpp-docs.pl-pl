---
title: to_vector, funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::to_vector
dev_langs:
- C++
helpviewer_keywords:
- to_vector Function
ms.assetid: 9cdd5123-7243-4def-a1d3-162e0bf6219e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00ecb00a890629c69994019c9232ff559ea93c96
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609741"
---
# <a name="tovector-function"></a>to_vector, funkcja
Zwraca `std::vector` którego wartość jest taka sama jak kolekcja podstawowy określony parametr IVector lub IVectorView.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <typename T>  
inline ::std::vector<T> to_vector(IVector<T>^ v); 
 
template <typename T>  
inline ::std::vector<T> to_vector(IVectorView<T>^ v);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Parametrowi typu szablonu.  
  
 `v`  
 Interfejs IVector lub IVectorView, która zapewnia dostęp do bazowego obiektu wektora lub VectorView.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** collection.h  
  
 **Namespace:** Windows::Foundation:: Collections  
  
## <a name="see-also"></a>Zobacz też  
 [Windows::Foundation:: Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)