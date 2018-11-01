---
title: Kompilator ostrzeżenie (poziom 1) C4651
ms.date: 11/04/2016
f1_keywords:
- C4651
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
ms.openlocfilehash: 01e2472a547e73eda5fcc56952949a0d9611029f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434778"
---
# <a name="compiler-warning-level-1-c4651"></a>Kompilator ostrzeżenie (poziom 1) C4651

"definition" określony dla prekompilowanego nagłówka, ale nie dla bieżącej kompilacji

Definicja została określona podczas generowania prekompilowanego nagłówka, ale nie znajduje się w tej kompilacji.

Definicja będzie obowiązywać wewnątrz prekompilowanego nagłówka, ale nie znajduje się w dalszej części kodu.

Jeśli prekompilowanego nagłówka został utworzony za pomocą /DSYMBOL, kompilator generuje to ostrzeżenie, jeśli kompilacji /Yu nie ma /DSYMBOL.  Dodawanie /DSYMBOL do wiersza polecenia /Yu rozwiązuje to ostrzeżenie.