---
title: Błąd kompilatora C2129 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2129
dev_langs:
- C++
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e86515a7d7c8954271578291c4ebcb1a52fc9863
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054288"
---
# <a name="compiler-error-c2129"></a>Błąd kompilatora C2129

Funkcja statyczna "function" zadeklarowana ale niezdefiniowana

Prześlij dalej odniesienia do `static` funkcja, która nigdy nie jest zdefiniowana.

A `static` funkcja musi być zdefiniowany w zakresie pliku. Jeśli funkcja jest zdefiniowana w innym pliku, musi być zadeklarowany `extern`.