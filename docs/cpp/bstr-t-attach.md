---
title: _bstr_t::Attach
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::Attach
helpviewer_keywords:
- Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
ms.openlocfilehash: 3b52661097ca1feab4c8045be240e4138a0c0f21
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190667"
---
# <a name="_bstr_tattach"></a>_bstr_t::Attach

**Specyficzne dla firmy Microsoft**

Łączy otokę `_bstr_t` z `BSTR`.

## <a name="syntax"></a>Składnia

```
void Attach(
   BSTR s
);
```

#### <a name="parameters"></a>Parametry

*wolumin*<br/>
`BSTR`, która ma być skojarzona z lub przypisana do zmiennej `_bstr_t`.

## <a name="remarks"></a>Uwagi

Jeśli `_bstr_t` była wcześniej dołączona do innego `BSTR`, `_bstr_t` czyści zasób `BSTR`, jeśli żadna inna zmienna `_bstr_t` nie używa `BSTR`.

## <a name="example"></a>Przykład

Zobacz [_bstr_t:: Assign](../cpp/bstr-t-assign.md) dla przykładu przy użyciu **dołączania**.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[_bstr_t, klasa](../cpp/bstr-t-class.md)
