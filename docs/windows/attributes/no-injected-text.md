---
title: no_injected_text (C++ atrybutów COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 354643020e704a87daa2e56e923b6a0a704bf0b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409294"
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

Najbardziej powszechnym zastosowaniem programu **no_injected_text** C++ polega na atrybut [/Fx](../../build/reference/fx-merge-injected-code.md) opcji kompilatora, która wstawia **no_injected_text** atrybutu do pliku .mrg.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Dowolne miejsce|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz także

[Atrybuty kompilatora](compiler-attributes.md)