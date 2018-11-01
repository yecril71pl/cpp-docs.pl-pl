---
title: Kompilator ostrzeżenie (poziomy 1 i 4) C4115
ms.date: 11/04/2016
f1_keywords:
- C4115
helpviewer_keywords:
- C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
ms.openlocfilehash: 20e44eba3b6f6079e6f37b7cf33fa530a996e829
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462962"
---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>Kompilator ostrzeżenie (poziomy 1 i 4) C4115

"type": nazwana definicja typu w nawiasach

Dany symbol jest używany do definiowania struktury, Unii lub Typ wyliczany wewnątrz wyrażenia w nawiasach. Zakres definicja może być nieoczekiwany.

W wywołaniu funkcji C definicja ma zakres globalny. W wywołaniu C++ definicja ma taki sam zakres jak wywoływanej funkcji.

To ostrzeżenie może również wpływać deklaratory wewnątrz nawiasów (na przykład prototypy), które nie są wyrażenia w nawiasach.

Jest to ostrzeżenia poziomu 1 z programy C++ i C opracowane w ramach zgodności z ANSI (/Za). W przeciwnym razie jest poziom 3.