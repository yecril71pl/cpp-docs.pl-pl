---
title: _bstr_t::GetBSTR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetBSTR
dev_langs:
- C++
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3041e8a4ece0ddff813b7ef9cd2ccb258e520a82
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940485"
---
# <a name="bstrtgetbstr"></a>_bstr_t::GetBSTR
**Microsoft Specific**  
  
 Wskazuje początek `BSTR` opakowane przez `_bstr_t`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
BSTR& GetBSTR( );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Na początek `BSTR` opakowane przez `_bstr_t`.  
  
## <a name="remarks"></a>Uwagi  
 `GetBSTR` ma wpływ na wszystkie `_bstr_t` obiekty udziału `BSTR`. Więcej niż jeden `_bstr_t` mogą udostępniać `BSTR` za pomocą konstruktora kopiującego i i **operator =**.  
  
## <a name="example"></a>Przykład  
 Zobacz [_bstr_t::przypisanie](../cpp/bstr-t-assign.md) dla przykłady dotyczące używania `GetBSTR`.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_bstr_t, klasa](../cpp/bstr-t-class.md)