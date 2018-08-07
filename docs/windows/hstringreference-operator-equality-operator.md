---
title: HStringReference::Operator == — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
dev_langs:
- C++
ms.assetid: cad3d52d-cd67-4194-a270-5239b1121a09
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7620cee350ab69f55737e6336b275218a70b6891
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607716"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator== Operator
Wskazuje, czy dwa parametry są równe.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
inline bool operator==(  
               const HStringReference& lhs,   
               const HStringReference& rhs) throw()  
  
inline bool operator==(  
               const HSTRING& lhs,   
               const HStringReference& rhs) throw()  
  
inline bool operator==(  
               const HStringReference& lhs,   
               const HSTRING& rhs) throw()  
```  
  
### <a name="parameters"></a>Parametry  
 *Lewa strona reguły przepisywania*  
 Pierwszy parametr do porównania. *Lewa strona reguły przepisywania* może być **HStringReference** obiektu lub dojścia HSTRING.  
  
 *RHS*  
 Drugi parametr do porównania.  *RHS* może być **HStringReference** obiektu lub dojścia HSTRING.  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli *lhs* i *rhs* parametry są równe; w przeciwnym razie **false**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [HStringReference, klasa](../windows/hstringreference-class.md)