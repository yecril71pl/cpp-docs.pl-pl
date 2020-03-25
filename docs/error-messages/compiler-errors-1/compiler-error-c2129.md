---
title: Błąd kompilatora C2129
ms.date: 11/04/2016
f1_keywords:
- C2129
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
ms.openlocfilehash: a3e2268bfc5597668e8689d093a0c2bb7f18e037
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80207288"
---
# <a name="compiler-error-c2129"></a>Błąd kompilatora C2129

funkcja statyczna "Function" została zadeklarowana, ale nie została zdefiniowana

Odwołanie do przodu jest wykonywane do funkcji `static`, która nigdy nie jest zdefiniowana.

Funkcja `static` musi być zdefiniowana w zakresie pliku. Jeśli funkcja jest zdefiniowana w innym pliku, należy ją zadeklarować `extern`.
