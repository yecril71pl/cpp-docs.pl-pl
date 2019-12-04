---
title: Błąd krytyczny C1103
ms.date: 11/04/2016
f1_keywords:
- C1103
helpviewer_keywords:
- C1103
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
ms.openlocfilehash: f037d1acb281b5997e3486a542784abc4b4b7542
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747387"
---
# <a name="fatal-error-c1103"></a>Błąd krytyczny C1103

Błąd krytyczny podczas importowania identyfikatora ProgID: "Message"

Kompilator wykrył problem podczas importowania biblioteki typów.  Na przykład nie można określić biblioteki typów z identyfikatorem ProgID, a także określić `no_registry`.

Aby uzyskać więcej informacji, zobacz [#import dyrektywie](../../preprocessor/hash-import-directive-cpp.md).

Poniższy przykład generuje C1103:

```cpp
// C1103.cpp
#import "progid:a.b.id.1.5" no_registry auto_search   // C1103
```
