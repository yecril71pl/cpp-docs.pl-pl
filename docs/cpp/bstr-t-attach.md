---
title: _bstr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
ms.openlocfilehash: 718efb9e3dac0d776678fe9efd912a602e041659
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749705"
---
# <a name="_bstr_tattach"></a>_bstr_t::Attach

**Specyficzne dla firmy Microsoft**

Łączy `_bstr_t` otokę z `BSTR`.

## <a name="syntax"></a>Składnia

```cpp
void Attach(
   BSTR s
);
```

#### <a name="parameters"></a>Parametry

*S*<br/>
A `BSTR` do skojarzenia ze zmienną lub `_bstr_t` przypisanej do niej.

## <a name="remarks"></a>Uwagi

Jeśli `_bstr_t` wcześniej został dołączony do `BSTR`innego `_bstr_t` , będzie `BSTR` oczyścić zasób, jeśli żadne inne `_bstr_t` zmienne nie używają `BSTR`.

## <a name="example"></a>Przykład

Zobacz [_bstr_t::Przypisywanie](../cpp/bstr-t-assign.md) przykładu za pomocą **dołączania**.

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[_bstr_t, klasa](../cpp/bstr-t-class.md)
