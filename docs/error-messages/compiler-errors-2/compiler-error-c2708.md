---
title: Błąd kompilatora C2708
ms.date: 11/04/2016
f1_keywords:
- C2708
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
ms.openlocfilehash: a128613cabb201142c29b833959924dbf8a6e0ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460076"
---
# <a name="compiler-error-c2708"></a>Błąd kompilatora C2708

'Identyfikator': rzeczywiste parametry długości w bajtach różni się od poprzedniego wywołania lub odwołania

A [__stdcall](../../cpp/stdcall.md) funkcji muszą być poprzedzone prototypu. W przeciwnym razie kompilator interpretuje pierwsze wywołanie do funkcji jako prototyp i ten błąd występuje, gdy kompilator napotyka wywołanie, który nie jest zgodny.

Aby naprawić ten błąd, Dodaj prototyp funkcji.