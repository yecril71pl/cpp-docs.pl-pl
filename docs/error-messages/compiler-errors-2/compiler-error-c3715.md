---
title: Błąd kompilatora C3715
ms.date: 11/04/2016
f1_keywords:
- C3715
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
ms.openlocfilehash: 94a451bbe936507ac3b33747065a9b6aac9edd02
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328331"
---
# <a name="compiler-error-c3715"></a>Błąd kompilatora C3715

"wskaźnik": musi być wskaźnikiem do "class"

Określony wskaźnik w [__hook](../../cpp/hook.md) lub [__unhook](../../cpp/unhook.md) nie wskazujące na prawidłową klasę. Aby naprawić ten błąd, upewnij się, że Twoje `__hook` i `__unhook` wywołania określają wskaźniki do prawidłowych klas.