---
title: Ostrzeżenie kompilatora (poziom 1) C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 6408185c99a54d5411fa5b1058cd5ec09d3326d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176315"
---
# <a name="compiler-warning-level-1-c4124"></a>Ostrzeżenie kompilatora (poziom 1) C4124

__fastcall ze sprawdzaniem stosu jest niewydajne

Słowo kluczowe `__fastcall` zostało użyte z włączonym sprawdzaniem stosu.

Konwencja `__fastcall` generuje szybszy kod, ale sprawdzanie stosu powoduje wolniejszy kod. Korzystając z `__fastcall`, Wyłącz sprawdzanie stosu przy użyciu **check_stack** pragma lub/GS.

To ostrzeżenie jest wydawane tylko dla pierwszej funkcji zadeklarowanej w tych warunkach.
