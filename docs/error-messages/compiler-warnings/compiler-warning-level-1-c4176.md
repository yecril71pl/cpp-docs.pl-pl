---
title: Kompilator ostrzeżenie (poziom 1) C4176 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4176
dev_langs:
- C++
helpviewer_keywords:
- C4176
ms.assetid: cfffb934-219a-4a63-9df6-ba54405bf766
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f173e132a2bd0d54c32fb0c2f7ae3b13dff1657d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085709"
---
# <a name="compiler-warning-level-1-c4176"></a>Kompilator ostrzeżenie (poziom 1) C4176

"podskładnika": nieznany podskładnik dla składnika przeglądarki #pragma

**Składnika** pragma zawiera nieprawidłowy podskładnika. Aby wykluczyć odwołania do konkretnej nazwy, należy użyć **odwołania** opcja przed nazwą.

## <a name="example"></a>Przykład

```
// C4176.cpp
// compile with: /W1 /LD
#pragma component(browser, off, i)  // C4176
#pragma component(browser, off, references, i) // ok
```