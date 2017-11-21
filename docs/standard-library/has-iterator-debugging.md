---
title: _HAS_ITERATOR_DEBUGGING | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _HAS_ITERATOR_DEBUGGING
dev_langs: C++
helpviewer_keywords: _HAS_ITERATOR_DEBUGGING
ms.assetid: 90077dbb-8a76-4963-83a6-29f4854007a8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 77690e373363aebec8876bc20fe88e3f09f8d79b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="hasiteratordebugging"></a>_HAS_ITERATOR_DEBUGGING  
  
Zastąpiony przez [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), to makro definiuje, czy iteratora funkcję debugowania jest włączony w kompilacji debugowania. Domyślnie debugowania iteratora jest włączona w kompilacjach debugowania i wyłączone w sprzedaży detalicznej kompilacji. Aby uzyskać więcej informacji, zobacz [Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md).  
  
> [!IMPORTANT]
> Bezpośrednie użycie `_HAS_ITERATOR_DEBUGGING` makro jest przestarzały. Zamiast tego należy użyć `_ITERATOR_DEBUG_LEVEL` kontrolować ustawienia debugowania iteratora. Aby uzyskać więcej informacji, zobacz [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).  
  
## <a name="remarks"></a>Uwagi  
Aby włączyć debugowanie w kompilacjach debugowania iteratora, ustaw `_ITERATOR_DEBUG_LEVEL` 2. Jest to równoważne `_HAS_ITERATOR_DEBUGGING` ustawienie 1 lub włączone:  
  
```  
#define _ITERATOR_DEBUG_LEVEL 2  
```  
  
`_ITERATOR_DEBUG_LEVEL`Nie można ustawić 2 (i `_HAS_ITERATOR_DEBUGGING` nie może być ustawiona na 1) w sprzedaży detalicznej kompilacji.  
  
Aby wyłączyć Iteratory debugowania w kompilacjach debugowania, ustaw `_ITERATOR_DEBUG_LEVEL` 0 lub 1. Jest to równoważne `_HAS_ITERATOR_DEBUGGING` ustawienie 0 lub wyłączone:  
  
```  
#define _ITERATOR_DEBUG_LEVEL 0  
```  
  
## <a name="see-also"></a>Zobacz też  
 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)   
 [Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md)   
 [Zaznaczone Iteratory](../standard-library/checked-iterators.md)   
 [Bezpieczne biblioteki: Standardowa biblioteka C++](../standard-library/safe-libraries-cpp-standard-library.md)

