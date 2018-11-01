---
title: _bstr_t::GetAddress
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetAddress
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
ms.openlocfilehash: 4d51539d2afbb2fbcc860b6c4d821df119aca418
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601464"
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

**Getaddress —** ma wpływ na wszystkie `_bstr_t` obiekty udziału `BSTR`. Więcej niż jeden `_bstr_t` mogą udostępniać `BSTR` za pomocą konstruktora kopiującego i **operator =**.

## <a name="example"></a>Przykład

Zobacz [_bstr_t::przypisanie](../cpp/bstr-t-assign.md) na przykład użycie **getaddress —**.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[_bstr_t, klasa](../cpp/bstr-t-class.md)