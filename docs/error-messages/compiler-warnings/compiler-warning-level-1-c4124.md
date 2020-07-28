---
title: Ostrzeżenie kompilatora (poziom 1) C4124
ms.date: 11/04/2016
f1_keywords:
- C4124
helpviewer_keywords:
- C4124
ms.assetid: c08c3a65-9584-47a1-a147-44f00c4b230e
ms.openlocfilehash: 59860bef108a3cd3e8bbbc6ff0790e17dbdaa0d4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214493"
---
# <a name="compiler-warning-level-1-c4124"></a>Ostrzeżenie kompilatora (poziom 1) C4124

__fastcall ze sprawdzaniem stosu jest niewydajne

**`__fastcall`** Słowo kluczowe zostało użyte z włączonym sprawdzaniem stosu.

**`__fastcall`** Konwencja generuje szybszy kod, ale sprawdzanie stosu powoduje wolniejszy kod. W przypadku korzystania z programu Wyłącz **`__fastcall`** Sprawdzanie stosu przy użyciu **check_stack** pragma lub/GS.

To ostrzeżenie jest wydawane tylko dla pierwszej funkcji zadeklarowanej w tych warunkach.
