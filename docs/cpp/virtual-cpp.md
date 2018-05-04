---
title: wirtualne (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- virtual_cpp
- virtual
dev_langs:
- C++
helpviewer_keywords:
- virtual base classes [C++], declaring
- base classes [C++], virtual
- virtual functions [C++], declaring
- virtual keyword [C++]
ms.assetid: c2eb987d-6cf3-43b6-aa0c-29a6f561b1ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 909fd3fde92479b2e5407608026cb01ec17fced2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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