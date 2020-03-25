---
title: _bstr_t::GetBSTR
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetBSTR
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
ms.openlocfilehash: da438c65256d9a7e5bf5b02e108fee1385171d2d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181216"
---
# <a name="_bstr_tgetbstr"></a>_bstr_t::GetBSTR

**Specyficzne dla firmy Microsoft**

Wskazuje początek `BSTR` opakowany przez `_bstr_t`.

## <a name="syntax"></a>Składnia

```
BSTR& GetBSTR( );
```

## <a name="return-value"></a>Wartość zwracana

Początek `BSTR` opakowany przez `_bstr_t`.

## <a name="remarks"></a>Uwagi

**GetBSTR** ma wpływ na wszystkie obiekty `_bstr_t`, które współużytkują `BSTR`. Więcej niż jeden `_bstr_t` może współdzielić `BSTR` za pomocą konstruktora kopiującego i **operatora =** .

## <a name="example"></a>Przykład

Zobacz [_bstr_t:: Assign](../cpp/bstr-t-assign.md) dla przykładu przy użyciu elementu **GetBSTR**.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_bstr_t, klasa](../cpp/bstr-t-class.md)
