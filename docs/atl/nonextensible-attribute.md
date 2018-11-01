---
title: nonextensible — atrybut
ms.date: 11/04/2016
f1_keywords:
- nonextensible
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
ms.openlocfilehash: 04cbc042d56902e2390e0f0f4a03a0797287397d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563764"
---
# <a name="nonextensible-attribute"></a>nonextensible — atrybut

Jeśli w czasie wykonywania nie zostanie rozszerzony podwójnego interfejsu (oznacza to, że nie będzie zapewniać metody lub właściwości, za pośrednictwem `IDispatch::Invoke` które nie są dostępne za pośrednictwem vtable), należy zastosować **nonextensible** atrybutu do interfejsu Definicja. Ten atrybut zawiera informacje dla języków klienta (np. Visual Basic), których można użyć, aby włączyć weryfikację pełnego kodu w czasie kompilacji. Jeśli ten atrybut nie zostanie podany, błędy mogą pozostać ukryte w kodzie klienta do czasu wykonywania.

Aby uzyskać więcej informacji na temat **nonextensible** atrybutu i przykłady, zobacz [nonextensible](../windows/nonextensible.md).

## <a name="see-also"></a>Zobacz też

[Podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md)

