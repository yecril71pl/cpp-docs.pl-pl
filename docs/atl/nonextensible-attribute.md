---
title: Atrybut nonextensible | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- nonextensible
dev_langs:
- C++
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1112f533e2e38dd90b1693e8bd31e5896ebca5e7
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848440"
---
# <a name="nonextensible-attribute"></a>nonextensible — atrybut
Jeśli w czasie wykonywania nie zostanie rozszerzony podwójnego interfejsu (oznacza to, że nie będzie zapewniać metody lub właściwości, za pośrednictwem `IDispatch::Invoke` które nie są dostępne za pośrednictwem vtable), należy zastosować **nonextensible** atrybutu do interfejsu Definicja. Ten atrybut zawiera informacje dla języków klienta (np. Visual Basic), których można użyć, aby włączyć weryfikację pełnego kodu w czasie kompilacji. Jeśli ten atrybut nie zostanie podany, błędy mogą pozostać ukryte w kodzie klienta do czasu wykonywania.  
  
 Aby uzyskać więcej informacji na temat **nonextensible** atrybutu i przykłady, zobacz [nonextensible](../windows/nonextensible.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md)

