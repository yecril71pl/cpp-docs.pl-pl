---
title: Błąd kompilatora C2129
ms.date: 11/04/2016
f1_keywords:
- C2129
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
ms.openlocfilehash: e55107419235420d272c738e9d8ef7cf277c11c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397630"
---
# <a name="compiler-error-c2129"></a>Błąd kompilatora C2129

Funkcja statyczna "function" zadeklarowana ale niezdefiniowana

Prześlij dalej odniesienia do `static` funkcja, która nigdy nie jest zdefiniowana.

A `static` funkcja musi być zdefiniowany w zakresie pliku. Jeśli funkcja jest zdefiniowana w innym pliku, musi być zadeklarowany `extern`.