---
title: Atrybut nierozszerzalny
ms.date: 11/04/2016
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
ms.openlocfilehash: fda2a0d43144b6e9832e061e7198b3f3e65f8b86
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500115"
---
# <a name="nonextensible-attribute"></a>Atrybut nierozszerzalny

Jeśli podwójny interfejs nie zostanie rozszerzony w czasie wykonywania (oznacza to, że nie będą udostępniane metody lub właściwości za pośrednictwem `IDispatch::Invoke` tablic wirtualnych), należy zastosować atrybut **nierozszerzalny** do definicji interfejsu. Ten atrybut zawiera informacje dotyczące języków klienta (takich jak Visual Basic), które mogą być używane do włączania pełnej weryfikacji kodu w czasie kompilacji. Jeśli ten atrybut nie jest podany, usterki mogą pozostać ukryte w kodzie klienta do czasu uruchomienia.

Aby uzyskać więcej informacji na temat atrybutu **nierozszerzalny** i przykładu, zobacz [nierozszerzalny](../windows/attributes/nonextensible.md).

## <a name="see-also"></a>Zobacz też

[Podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md)
