---
title: Kompilator ostrzeżenie (poziom 1) C4049 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4049
dev_langs:
- C++
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68a89d02129e5e8fbedb0649fff0cfe3813304c5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053521"
---
# <a name="compiler-warning-level-1-c4049"></a>Kompilator ostrzeżenie (poziom 1) C4049

ograniczenie kompilatora: Kończenie emisji numeru wiersza

Ten plik zawiera więcej niż 16 777 215 (2<sup>24</sup>-1) źródła wierszy. Kompilator zatrzymuje numerowanie od 16 777 215.

Dla kodu po wierszu 16 777 215:

- Obraz, który będzie zawierać informacji debugowania dla numerów wierszy.

- Niektóre funkcje diagnostyczne mogą być zgłaszane z numerami wierszy niepoprawne.

- oferty .asm (/ FAs) mogą mieć nieprawidłowe numery.