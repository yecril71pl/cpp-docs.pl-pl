---
title: Błąd kompilatora C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: a82ee0bead9e4e7a92c16df89eee86288f562de9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216105"
---
# <a name="compiler-error-c2692"></a>Błąd kompilatora C2692

"function_name": funkcje w pełni prototypowe wymagane w kompilatorze języka C z opcją "/CLR"

Podczas kompilowania kodu zarządzanego .NET kompilator języka C wymaga deklaracji funkcji ANSI. Ponadto, jeśli funkcja nie przyjmuje żadnych parametrów, musi jawnie zadeklarować **`void`** jako typ parametru.
