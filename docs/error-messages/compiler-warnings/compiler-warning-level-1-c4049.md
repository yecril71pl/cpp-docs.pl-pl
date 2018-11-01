---
title: Kompilator ostrzeżenie (poziom 1) C4049
ms.date: 11/04/2016
f1_keywords:
- C4049
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
ms.openlocfilehash: a4958bb446b5f7e80ef2eef92b52a0f86cf6a134
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479407"
---
# <a name="compiler-warning-level-1-c4049"></a>Kompilator ostrzeżenie (poziom 1) C4049

ograniczenie kompilatora: Kończenie emisji numeru wiersza

Ten plik zawiera więcej niż 16 777 215 (2<sup>24</sup>-1) źródła wierszy. Kompilator zatrzymuje numerowanie od 16 777 215.

Dla kodu po wierszu 16 777 215:

- Obraz, który będzie zawierać informacji debugowania dla numerów wierszy.

- Niektóre funkcje diagnostyczne mogą być zgłaszane z numerami wierszy niepoprawne.

- oferty .asm (/ FAs) mogą mieć nieprawidłowe numery.