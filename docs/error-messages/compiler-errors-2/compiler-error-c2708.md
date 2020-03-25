---
title: Błąd kompilatora C2708
ms.date: 11/04/2016
f1_keywords:
- C2708
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
ms.openlocfilehash: a1d3379a0da42c5aabd38cffbf6f6a3f340ef3b9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202374"
---
# <a name="compiler-error-c2708"></a>Błąd kompilatora C2708

"Identyfikator": rzeczywiste parametry długości w bajtach różnią się od poprzedniego wywołania lub odwołania

Funkcja [__stdcall](../../cpp/stdcall.md) musi być poprzedzona prototypem. W przeciwnym razie kompilator interpretuje pierwsze wywołanie funkcji jako prototyp i ten błąd występuje, gdy kompilator napotyka wywołanie, które nie jest zgodne.

Aby naprawić ten błąd, Dodaj prototyp funkcji.
