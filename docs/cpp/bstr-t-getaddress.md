---
title: _bstr_t::GetAddress
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetAddress
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
ms.openlocfilehash: ca78bd1b607ba4a86bbc824887a7ec767cd5476e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181255"
---
# <a name="_bstr_tgetaddress"></a>_bstr_t::GetAddress

**Specyficzne dla firmy Microsoft**

Zwalnia wszystkie istniejące ciągi i zwraca adres nowo przydzielony ciąg.

## <a name="syntax"></a>Składnia

```
BSTR* GetAddress( );
```

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do `BSTR` opakowany przez `_bstr_t`.

## <a name="remarks"></a>Uwagi

**GetAddress** ma wpływ na wszystkie obiekty `_bstr_t`, które współużytkują `BSTR`. Więcej niż jeden `_bstr_t` może współdzielić `BSTR` za pomocą konstruktora kopiującego i **operatora =** .

## <a name="example"></a>Przykład

Zobacz [_bstr_t:: Assign](../cpp/bstr-t-assign.md) dla przykładu przy użyciu **GetAddress**.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_bstr_t, klasa](../cpp/bstr-t-class.md)
