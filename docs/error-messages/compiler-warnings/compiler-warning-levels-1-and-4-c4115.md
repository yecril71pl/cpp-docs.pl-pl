---
title: Kompilator ostrzeżenie (poziomy 1 i 4) C4115 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4115
dev_langs:
- C++
helpviewer_keywords:
- C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c22e3c33f9ef2409c02f0e651473d566b4d2a74
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022529"
---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>Kompilator ostrzeżenie (poziomy 1 i 4) C4115

"type": nazwana definicja typu w nawiasach

Dany symbol jest używany do definiowania struktury, Unii lub Typ wyliczany wewnątrz wyrażenia w nawiasach. Zakres definicja może być nieoczekiwany.

W wywołaniu funkcji C definicja ma zakres globalny. W wywołaniu C++ definicja ma taki sam zakres jak wywoływanej funkcji.

To ostrzeżenie może również wpływać deklaratory wewnątrz nawiasów (na przykład prototypy), które nie są wyrażenia w nawiasach.

Jest to ostrzeżenia poziomu 1 z programy C++ i C opracowane w ramach zgodności z ANSI (/Za). W przeciwnym razie jest poziom 3.