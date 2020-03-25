---
title: Ostrzeżenie kompilatora (poziom 1) C4103
ms.date: 11/04/2016
f1_keywords:
- C4103
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
ms.openlocfilehash: dfc3a91b2dcb3ed1e8f4f4993edd67219a6bf1d8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163848"
---
# <a name="compiler-warning-level-1-c4103"></a>Ostrzeżenie kompilatora (poziom 1) C4103

"filename": wyrównanie zmieniono po dołączeniu nagłówka, może to być spowodowane brakiem #pragma Pack (pop)

Pakowanie ma wpływ na układ klas, a często w przypadku zmiany pakowania w plikach nagłówkowych mogą wystąpić problemy.

Użyj #pragma [Pack](../../preprocessor/pack.md)(pop) przed opuszczeniem pliku nagłówkowego, aby usunąć to ostrzeżenie.

Poniższy przykład generuje C4103:

```cpp
// C4103.h
#pragma pack(push, 4)

// defintions and declarations

// uncomment the following line to resolve
// #pragma pack(pop)
```

a następnie

```cpp
// C4103.cpp
// compile with: /LD /W1
#include "c4103.h"   // C4103
```
