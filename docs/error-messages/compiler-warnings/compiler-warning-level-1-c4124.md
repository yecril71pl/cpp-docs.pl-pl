---
title: Kompilator ostrzeżenie (poziom 1) C4124 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4124
dev_langs:
- C++
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a69190487c22987ead2d00ec102785ed42ea93c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090935"
---
# <a name="compiler-warning-level-1-c4124"></a>Kompilator ostrzeżenie (poziom 1) C4124

__fastcall ze sprawdzeniem stosu jest nieefektywne

`__fastcall` Użyto słowa kluczowego ze sprawdzeniem stosu włączone.

`__fastcall` Konwencji generuje kod szybszy, ale sprawdzeniem stosu powoduje, że kod wolniej. Korzystając z `__fastcall`, wyłącz sprawdzeniem stosu z **check_stack** pragma lub/GS.

To ostrzeżenie zostanie wyświetlone tylko w przypadku pierwsza funkcja zadeklarowana w tych warunkach.