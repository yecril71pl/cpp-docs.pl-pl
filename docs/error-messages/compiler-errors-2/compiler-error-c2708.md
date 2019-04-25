---
title: Błąd kompilatora C2708
ms.date: 11/04/2016
f1_keywords:
- C2708
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
ms.openlocfilehash: a128613cabb201142c29b833959924dbf8a6e0ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160961"
---
# <a name="compiler-error-c2708"></a>Błąd kompilatora C2708

'Identyfikator': rzeczywiste parametry długości w bajtach różni się od poprzedniego wywołania lub odwołania

A [__stdcall](../../cpp/stdcall.md) funkcji muszą być poprzedzone prototypu. W przeciwnym razie kompilator interpretuje pierwsze wywołanie do funkcji jako prototyp i ten błąd występuje, gdy kompilator napotyka wywołanie, który nie jest zgodny.

Aby naprawić ten błąd, Dodaj prototyp funkcji.