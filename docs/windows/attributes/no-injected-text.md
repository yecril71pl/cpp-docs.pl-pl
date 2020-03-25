---
title: no_injected_text (C++ atrybut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 5f98be3478b2e1eeb4b464f1784f3f4ece22d8a4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166617"
---
# <a name="no_injected_text"></a>no_injected_text

Uniemożliwia kompilatorowi wstrzyknięcie kodu w wyniku użycia atrybutów.

## <a name="syntax"></a>Składnia

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>Parametry

*typu*<br/>
Obowiązkowe **prawda** , jeśli chcesz, aby żaden kod nie został wstrzyknięty, **wartość false** , aby zezwolić na wstrzyknięcie kodu. **wartość** domyślna to true.

## <a name="remarks"></a>Uwagi

Najbardziej typowym zastosowaniem atrybutu **No_injected_text** C++ jest opcja kompilatora [/FX](../../build/reference/fx-merge-injected-code.md) , która wstawia atrybut **No_injected_text** do pliku. MRG.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|Dowolnym miejscu|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|None|
|**Nieprawidłowe atrybuty**|None|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Zobacz też

[Atrybuty kompilatora](compiler-attributes.md)
