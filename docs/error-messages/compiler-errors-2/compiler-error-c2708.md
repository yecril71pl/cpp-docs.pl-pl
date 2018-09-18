---
title: Błąd kompilatora C2708 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2708
dev_langs:
- C++
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0accd68881cccad5e34530a6c157a4e8179b283
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111098"
---
# <a name="compiler-error-c2708"></a>Błąd kompilatora C2708

'Identyfikator': rzeczywiste parametry długości w bajtach różni się od poprzedniego wywołania lub odwołania

A [__stdcall](../../cpp/stdcall.md) funkcji muszą być poprzedzone prototypu. W przeciwnym razie kompilator interpretuje pierwsze wywołanie do funkcji jako prototyp i ten błąd występuje, gdy kompilator napotyka wywołanie, który nie jest zgodny.

Aby naprawić ten błąd, Dodaj prototyp funkcji.