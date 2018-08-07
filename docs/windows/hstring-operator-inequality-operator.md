---
title: HString::Operator! = — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
dev_langs:
- C++
ms.assetid: dcdd2aca-e7d6-4bf1-b2de-03efbb430a93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e35c0b9c448ce9b7aeb6e5f14627e82274a72a41
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604476"
---
# <a name="hstringoperator-operator"></a>HString::Operator!= Operator
Wskazuje, czy dwa parametry nie są równe.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
inline bool operator!=( const HString& lhs,   
                        const HString& rhs) throw()  
  
inline bool operator!=( const HStringReference& lhs,   
                        const HString& rhs) throw()  
  
inline bool operator!=( const HString& lhs,   
                        const HStringReference& rhs) throw()  
  
inline bool operator!=( const HSTRING& lhs,   
                        const HString& rhs) throw()  
  
inline bool operator!=( const HString& lhs,   
                        const HSTRING& rhs) throw()  
```  
  
#### <a name="parameters"></a>Parametry  
 *Lewa strona reguły przepisywania*  
 Pierwszy parametr do porównania. *Lewa strona reguły przepisywania* może być **HString** lub `HStringReference` obiektu lub dojścia HSTRING.  
  
 *RHS*  
 Drugi parametr do porównania. *rhs* może być **HString** lub `HStringReference` obiektu lub dojścia HSTRING.  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli *lhs* i *rhs* parametry nie są równe; w przeciwnym razie **false**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [HString, klasa](../windows/hstring-class.md)