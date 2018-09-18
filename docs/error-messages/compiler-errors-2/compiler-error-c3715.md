---
title: Błąd kompilatora C3715 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3715
dev_langs:
- C++
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63ae3486b4db21a3aa241d5ebdbbfa0cdc6806f2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026559"
---
# <a name="compiler-error-c3715"></a>Błąd kompilatora C3715

"wskaźnik": musi być wskaźnikiem do "class"

Określony wskaźnik w [__hook](../../cpp/hook.md) lub [__unhook](../../cpp/unhook.md) nie wskazujące na prawidłową klasę. Aby naprawić ten błąd, upewnij się, że Twoje `__hook` i `__unhook` wywołania określają wskaźniki do prawidłowych klas.