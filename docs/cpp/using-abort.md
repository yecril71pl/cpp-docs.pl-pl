---
title: Użycie przerywania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Abort
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7231339ba4884445d7ad6b0161c6cff793c6db8a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32421851"
---
# <a name="using-abort"></a>Użycie przerywania
Wywoływanie [przerwać](../c-runtime-library/reference/abort.md) funkcja powoduje natychmiastowe przerwanie działania. Pomija się proces normalne zniszczenie zainicjowane statycznych obiektów globalnych. Również pomija specjalnego przetwarzania, która została określona za pomocą `atexit` funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodatkowe zagadnienia dotyczące kończenia](../cpp/additional-termination-considerations.md)