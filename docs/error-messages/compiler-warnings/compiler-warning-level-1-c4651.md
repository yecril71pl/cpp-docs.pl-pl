---
title: Kompilator ostrzeżenie (poziom 1) C4651 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4651
dev_langs:
- C++
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b516ef86372901d00dd20d94ed10d5e361bbab8d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099475"
---
# <a name="compiler-warning-level-1-c4651"></a>Kompilator ostrzeżenie (poziom 1) C4651

"definition" określony dla prekompilowanego nagłówka, ale nie dla bieżącej kompilacji

Definicja została określona podczas generowania prekompilowanego nagłówka, ale nie znajduje się w tej kompilacji.

Definicja będzie obowiązywać wewnątrz prekompilowanego nagłówka, ale nie znajduje się w dalszej części kodu.

Jeśli prekompilowanego nagłówka został utworzony za pomocą /DSYMBOL, kompilator generuje to ostrzeżenie, jeśli kompilacji /Yu nie ma /DSYMBOL.  Dodawanie /DSYMBOL do wiersza polecenia /Yu rozwiązuje to ostrzeżenie.