---
title: nonextensible — atrybut
ms.date: 11/04/2016
f1_keywords:
- nonextensible
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
ms.openlocfilehash: 5aa5b8514435e9876500daa4d92504d75eb6dc23
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257634"
---
# <a name="nonextensible-attribute"></a>nonextensible — atrybut

Jeśli w czasie wykonywania nie zostanie rozszerzony podwójnego interfejsu (oznacza to, że nie będzie zapewniać metody lub właściwości, za pośrednictwem `IDispatch::Invoke` które nie są dostępne za pośrednictwem vtable), należy zastosować **nonextensible** atrybutu do interfejsu Definicja. Ten atrybut zawiera informacje dla języków klienta (np. Visual Basic), których można użyć, aby włączyć weryfikację pełnego kodu w czasie kompilacji. Jeśli ten atrybut nie zostanie podany, błędy mogą pozostać ukryte w kodzie klienta do czasu wykonywania.

Aby uzyskać więcej informacji na temat **nonextensible** atrybutu i przykłady, zobacz [nonextensible](../windows/nonextensible.md).

## <a name="see-also"></a>Zobacz także

[Podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md)
