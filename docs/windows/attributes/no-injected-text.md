---
title: no_injected_text (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: af4bb4b07439c0a5dacfa0d4956db564d2dccefe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618121"
---
# <a name="noinjectedtext"></a>no_injected_text

Zabezpiecza kompilator przed wprowadzanie kodu w wyniku użycia atrybutu.

## <a name="syntax"></a>Składnia

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>Parametry

*Atrybut typu wartość logiczna*<br/>
(Opcjonalnie) **true** Jeśli chcesz, aby bez kodu, które są wstrzykiwane, **false** do kodu, ich wstrzyknięcie. **wartość true,** jest ustawieniem domyślnym.

## <a name="remarks"></a>Uwagi

Najbardziej powszechnym zastosowaniem programu **no_injected_text** polega na atrybut C++ [/Fx](../../build/reference/fx-merge-injected-code.md) opcji kompilatora, która wstawia **no_injected_text** atrybutu do pliku .mrg.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Dowolne miejsce|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty kompilatora](compiler-attributes.md)