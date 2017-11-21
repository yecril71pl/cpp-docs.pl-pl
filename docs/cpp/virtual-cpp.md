---
title: wirtualne (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- virtual_cpp
- virtual
dev_langs: C++
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f8d029ce5a75da7c3c5642912c3d2a418183eee0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="virtual-c"></a>wirtualne (C++)
`virtual` — Słowo kluczowe deklaruje funkcję wirtualną lub wirtualnej klasy podstawowej.  
  
## <a name="syntax"></a>Składnia  
  
```  
virtual [type-specifiers] member-function-declarator  
virtual [access-specifier] base-class-name  
```  
  
#### <a name="parameters"></a>Parametry  
 `type-specifiers`  
 Określa typ zwracany funkcji wirtualnego elementu członkowskiego.  
  
 `member-function-declarator`  
 Deklaruje funkcję elementu członkowskiego.  
  
 `access-specifier`  
 Określa poziom dostępu do klasy podstawowej `public`, `protected` lub `private`. Może występować przed lub po `virtual` — słowo kluczowe.  
  
 `base-class-name`  
 Określa typ klasy poprzednio zadeklarowana.  
  
## <a name="remarks"></a>Uwagi  
 Zobacz [funkcji wirtualnych](../cpp/virtual-functions.md) Aby uzyskać więcej informacji.  
  
 Zobacz też Poniższe słowa kluczowe: [klasy](../cpp/class-cpp.md), [prywatnej](../cpp/private-cpp.md), [publicznego](../cpp/public-cpp.md), i [chronione](../cpp/protected-cpp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)