---
title: no_injected_text | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.no_injected_text
dev_langs:
- C++
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e63b0b47dcc3f53ecd5af2d51505df844f66437a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599389"
---
# <a name="noinjectedtext"></a>no_injected_text

Zabezpiecza kompilator przed wprowadzanie kodu w wyniku użycia atrybutu.

## <a name="syntax"></a>Składnia

```cpp
[ no_injected_text(
   boolean
) ];
```

### <a name="parameters"></a>Parametry

*wartość logiczna* (opcjonalnie)  
**wartość true,** Jeśli chcesz, aby bez kodu, które są wstrzykiwane, **false** do kodu, ich wstrzyknięcie. **wartość true,** jest ustawieniem domyślnym.

## <a name="remarks"></a>Uwagi

Najbardziej powszechnym zastosowaniem programu **no_injected_text** polega na atrybut C++ [/Fx](../build/reference/fx-merge-injected-code.md) opcji kompilatora, która wstawia **no_injected_text** atrybutu do pliku .mrg.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Dowolne miejsce|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="see-also"></a>Zobacz też

[Atrybuty kompilatora](../windows/compiler-attributes.md)  