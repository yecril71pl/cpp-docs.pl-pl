---
title: Ostrzeżenie kompilatora (poziomy 1 i 4) C4115
ms.date: 11/04/2016
f1_keywords:
- C4115
helpviewer_keywords:
- C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
ms.openlocfilehash: 7e39e8c837d94776a804da2bf38643b453edb949
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198045"
---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>Ostrzeżenie kompilatora (poziomy 1 i 4) C4115

"Type": nazwana definicja typu w nawiasach

Dany symbol jest używany do definiowania struktury, Unii lub typu wyliczeniowego wewnątrz wyrażenia ujętego w nawiasy. Zakres definicji może być nieoczekiwany.

W wywołaniu funkcji języka C definicja ma zakres globalny. W C++ wywołaniu definicja ma ten sam zakres, co funkcja, która jest wywoływana.

To ostrzeżenie może być również spowodowane przez Deklaratory w nawiasach (takich jak prototypy), które nie są wyrażeniami w nawiasach.

Jest to ostrzeżenie poziomu-1 z C++ programami i programami C skompilowanymi pod kątem zgodności ze standardem ANSI (/za). W przeciwnym razie jest to poziom 3.
