---
title: "nonextensible — atrybut | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: nonextensible
dev_langs: C++
helpviewer_keywords:
- nonextensible attribute
- dual interfaces, nonextensible attribute
ms.assetid: 02a4a18b-ffd3-4d53-8fd1-feb1c05ad5ac
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 54c76d640171a6068421ff4199b6e77480db28d7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="nonextensible-attribute"></a>nonextensible — atrybut
Jeśli w czasie wykonywania nie zostanie rozszerzony podwójną interfejsu (oznacza to, że nie będzie zapewniać metody lub właściwości za pośrednictwem **IDispatch::Invoke** które nie są dostępne za pośrednictwem vtable), należy zastosować **nonextensible —** atrybut do definicji interfejsu. Ten atrybut informuje języków klienta (na przykład w języku Visual Basic), których można użyć, aby włączyć weryfikację pełnego kodu w czasie kompilacji. Jeśli ten atrybut nie zostanie podany, usterki mogą pozostać ukryte w kodzie klienta do czasu wykonywania.  
  
 Aby uzyskać więcej informacji na temat **nonextensible —** atrybut i przykładem, zobacz [nonextensible —](../windows/nonextensible.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Podwójne interfejsy i ATL](../atl/dual-interfaces-and-atl.md)

