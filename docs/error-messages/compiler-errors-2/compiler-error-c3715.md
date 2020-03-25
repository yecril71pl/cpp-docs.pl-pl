---
title: Błąd kompilatora C3715
ms.date: 11/04/2016
f1_keywords:
- C3715
helpviewer_keywords:
- C3715
ms.assetid: ee5dce88-ddc4-4bdb-9464-47467ce1674f
ms.openlocfilehash: 13befc17b94fdf2c22cb84bc64ed55b9375b3473
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165915"
---
# <a name="compiler-error-c3715"></a>Błąd kompilatora C3715

"wskaźnik": musi być wskaźnikiem do "Class"

Określono wskaźnik w [__hook](../../cpp/hook.md) lub [__unhook](../../cpp/unhook.md) , który nie wskazuje prawidłowej klasy. Aby naprawić ten błąd, upewnij się, że wywołania `__hook` i `__unhook` określają wskaźniki do prawidłowych klas.
