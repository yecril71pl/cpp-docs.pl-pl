---
title: nonextensible — atrybut
ms.date: 11/04/2016
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
ms.openlocfilehash: cc57acb8bd7bc3e32c764606da651f57316ceabf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250107"
---
# <a name="nonextensible-attribute"></a>nonextensible — atrybut

Jeśli w czasie wykonywania nie zostanie rozszerzony podwójnego interfejsu (oznacza to, że nie będzie zapewniać metody lub właściwości, za pośrednictwem `IDispatch::Invoke` które nie są dostępne za pośrednictwem vtable), należy zastosować **nonextensible** atrybutu do interfejsu Definicja. Ten atrybut zawiera informacje dla języków klienta (np. Visual Basic), których można użyć, aby włączyć weryfikację pełnego kodu w czasie kompilacji. Jeśli ten atrybut nie zostanie podany, błędy mogą pozostać ukryte w kodzie klienta do czasu wykonywania.

Aby uzyskać więcej informacji na temat **nonextensible** atrybutu i przykłady, zobacz [nonextensible](../windows/nonextensible.md).

## <a name="see-also"></a>Zobacz także

[Podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md)
