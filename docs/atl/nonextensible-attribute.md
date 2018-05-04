---
title: nonextensible — atrybut | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 40b4b79701862ca07e704aca098419479923ef1a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="nonextensible-attribute"></a>nonextensible — atrybut
Jeśli w czasie wykonywania nie zostanie rozszerzony podwójną interfejsu (oznacza to, że nie będzie zapewniać metody lub właściwości za pośrednictwem **IDispatch::Invoke** które nie są dostępne za pośrednictwem vtable), należy zastosować **nonextensible —** atrybut do definicji interfejsu. Ten atrybut informuje języków klienta (na przykład w języku Visual Basic), których można użyć, aby włączyć weryfikację pełnego kodu w czasie kompilacji. Jeśli ten atrybut nie zostanie podany, usterki mogą pozostać ukryte w kodzie klienta do czasu wykonywania.  
  
 Aby uzyskać więcej informacji na temat **nonextensible —** atrybut i przykładem, zobacz [nonextensible —](../windows/nonextensible.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md)

