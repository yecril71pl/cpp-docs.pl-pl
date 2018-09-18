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
ms.openlocfilehash: 3a62cd1c08409fb5915ebf42fa118c1e6124e29f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071864"
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