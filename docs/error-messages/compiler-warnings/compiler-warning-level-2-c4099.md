---
title: Ostrzeżenie kompilatora (poziom 2) C4099 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4099
dev_langs:
- C++
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d7ffee02e8e5414a0e06cc4ba0da77a50c75f53
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110175"
---
# <a name="compiler-warning-level-2-c4099"></a>Ostrzeżenie kompilatora (poziom 2) C4099

'Identyfikator': Nazwa typu najpierw widoczna przy użyciu "objecttype1" teraz widoczna przy użyciu "objecttype2"

Obiekt, który został zadeklarowany jako struktura jest zdefiniowana jako klasa lub obiekt, który został zadeklarowany jako klasa jest zdefiniowana jako struktury. Kompilator używa typu podanego w definicji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4099.

```
// C4099.cpp
// compile with: /W2 /c
struct A;
class A {};   // C4099, use different identifer or use same object type
```