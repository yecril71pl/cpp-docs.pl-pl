---
title: _bstr_t::GetAddress | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetAddress
dev_langs:
- C++
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4895153abe248265e0aacfbe636b9a4bd46ed205
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941200"
---
# <a name="bstrtgetaddress"></a>_bstr_t::GetAddress
**Microsoft Specific**  
  
 Zwalnia wszelkie istniejących parametrów i zwraca adres nowo przydzielonego ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
BSTR* GetAddress( );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `BSTR` opakowane przez `_bstr_t`.  
  
## <a name="remarks"></a>Uwagi  
 `GetAddress` ma wpływ na wszystkie `_bstr_t` obiekty udziału `BSTR`. Więcej niż jeden `_bstr_t` mogą udostępniać `BSTR` za pomocą konstruktora kopiującego i i **operator =**.  
  
## <a name="example"></a>Przykład  
 Zobacz [_bstr_t::przypisanie](../cpp/bstr-t-assign.md) na przykład użycie `GetAddress`.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_bstr_t, klasa](../cpp/bstr-t-class.md)