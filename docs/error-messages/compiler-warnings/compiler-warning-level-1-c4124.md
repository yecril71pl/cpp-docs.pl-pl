---
title: Kompilator ostrzeżenie (poziom 1) C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 04732619571420e777244b81bf4b93b775477a20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310984"
---
# <a name="compiler-warning-level-1-c4124"></a>Kompilator ostrzeżenie (poziom 1) C4124

__fastcall ze sprawdzeniem stosu jest nieefektywne

`__fastcall` Użyto słowa kluczowego ze sprawdzeniem stosu włączone.

`__fastcall` Konwencji generuje kod szybszy, ale sprawdzeniem stosu powoduje, że kod wolniej. Korzystając z `__fastcall`, wyłącz sprawdzeniem stosu z **check_stack** pragma lub/GS.

To ostrzeżenie zostanie wyświetlone tylko w przypadku pierwsza funkcja zadeklarowana w tych warunkach.