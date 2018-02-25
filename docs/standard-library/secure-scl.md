---
title: _SECURE_SCL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _SECURE_SCL
dev_langs:
- C++
helpviewer_keywords:
- _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b49e101e944d4309a1d05e605a49452d9e17083c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="securescl"></a>_SECURE_SCL
  
Zastąpiony przez [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md), definiuje to makro czy [zaznaczone Iteratory](../standard-library/checked-iterators.md) są włączone. Domyślnie zaznaczone Iteratory są włączone w kompilacjach debugowania i wyłączone w sprzedaży detalicznej kompilacji.  
  
> [!IMPORTANT]
> Bezpośrednie użycie `_SECURE_SCL` makro jest przestarzały. Zamiast tego należy użyć `_ITERATOR_DEBUG_LEVEL` do kontrolowania ustawień zaznaczone iteratora. Aby uzyskać więcej informacji, zobacz [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md).  
  
## <a name="remarks"></a>Uwagi  
  
Zaznaczone Iteratory są włączone, niebezpieczne użycie iteratora powoduje błąd w czasie wykonywania, a program zostanie zakończony. Aby włączyć zaznaczone Iteratory, ustaw `_ITERATOR_DEBUG_LEVEL` 1 lub 2. Jest to równoważne `_SECURE_SCL` ustawienie 1 lub włączone:  
  
```  
#define _ITERATOR_DEBUG_LEVEL 1  
```  
  
Aby wyłączyć zaznaczone Iteratory, ustaw `_ITERATOR_DEBUG_LEVEL` na 0. Jest to równoważne `_SECURE_SCL` ustawienie 0 lub wyłączone:  
  
```  
#define _ITERATOR_DEBUG_LEVEL 0  
```  
  
Aby uzyskać informacje na temat sposobu Wyłącz ostrzeżenia o zaznaczone Iteratory, zobacz [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md).  
  
## <a name="see-also"></a>Zobacz też  
[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)   
[Zaznaczone Iteratory](../standard-library/checked-iterators.md)   
[Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md)   
[Bezpieczne biblioteki: Standardowa biblioteka C++](../standard-library/safe-libraries-cpp-standard-library.md)

