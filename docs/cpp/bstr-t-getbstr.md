---
title: _bstr_t::GetBSTR
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetBSTR
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
ms.openlocfilehash: cea3404e0732cb0e16b3fa9199ce95e3dfcc23f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618052"
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

**Getbstr —** ma wpływ na wszystkie `_bstr_t` obiekty udziału `BSTR`. Więcej niż jeden `_bstr_t` mogą udostępniać `BSTR` za pomocą konstruktora kopiującego i **operator =**.

## <a name="example"></a>Przykład

Zobacz [_bstr_t::przypisanie](../cpp/bstr-t-assign.md) dla przykłady dotyczące używania **getbstr —**.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_bstr_t, klasa](../cpp/bstr-t-class.md)