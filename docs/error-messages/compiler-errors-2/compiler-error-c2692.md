---
title: Błąd kompilatora C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: c469f4944417c9116c7316b01642dd4b370b8c4b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257819"
---
# <a name="compiler-error-c2692"></a>Błąd kompilatora C2692

"nazwa_funkcji": wymagano w pełni prototypowanych funkcji w kompilatorze języka C z "/ clr" opcja

W przypadku kodu zarządzanego kompilowania dla platformy .NET, kompilator języka C wymaga deklaracji funkcji ANSI. Ponadto, jeśli funkcja nie przyjmuje żadnych parametrów, go jawnie zadeklarować `void` jako typ parametru.