---
title: Ostrzeżenie kompilatora (poziom 1) C4049
ms.date: 11/04/2016
f1_keywords:
- C4049
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
ms.openlocfilehash: 214ccae5d9835bc4a3b66bbbe1cd5ded4bc651cb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164147"
---
# <a name="compiler-warning-level-1-c4049"></a>Ostrzeżenie kompilatora (poziom 1) C4049

ograniczenie kompilatora: Trwa kończenie emisji numeru wiersza

Plik zawiera więcej niż 16 777 215<sup>(2)</sup>wierszy źródłowych. Kompilator przerywa numerowanie o 16 777 215.

Dla kodu po wierszu 16 777 215:

- Obraz nie będzie zawierał żadnych informacji debugowania dla numerów wierszy.

- Niektóre funkcje diagnostyczne mogą być zgłaszane z nieprawidłowymi numerami wierszy.

- listy. asm (/FAs) mogą mieć niepoprawne numery wierszy.
