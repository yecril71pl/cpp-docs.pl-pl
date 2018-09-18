---
title: Kompilator ostrzeżenie (poziom 1) C4010 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4010
dev_langs:
- C++
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52449689d329cee45cc69b63c315ce9335befbe0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073106"
---
# <a name="compiler-warning-level-1-c4010"></a>Kompilator ostrzeżenie (poziom 1) C4010

komentarz jednowierszowy zawiera znak kontynuacji wiersza

Komentarz jednowierszowy, który został wprowadzony przez / / zawiera ukośnik odwrotny (\\) który służy jako znak kontynuacji wiersza. Kompilator traktuje następny wiersz jako kontynuację i traktuje je jako komentarz.

Niektóre składni skierowane edytory nie wskazują wiersza po znaku kontynuacji jako komentarz. Ignoruj kolorowania na wszystkie wiersze, które powodują to ostrzeżenie.

Poniższy przykład spowoduje wygenerowanie C4010:

```
// C4010.cpp
// compile with: /WX
int main() {
   // the next line is also a comment because of the backslash \
   int a = 3; // C4010
   a++;
}
```