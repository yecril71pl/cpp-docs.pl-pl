---
title: Kompilator ostrzeżenie (poziom 4) C4718
ms.date: 11/04/2016
f1_keywords:
- C4718
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
ms.openlocfilehash: c313e26af5f5b17db9c7d001a705ff7211461c2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395173"
---
# <a name="compiler-warning-level-4-c4718"></a>Kompilator ostrzeżenie (poziom 4) C4718

"wywołanie funkcji": wywołanie cykliczne nie ma żadnych efektów ubocznych, usuwanie

Funkcja zawiera wywołanie cykliczne, a w przeciwnym razie ma żadnych efektów ubocznych. Wywołanie tej funkcji jest usuwana. Poprawność program nie ma wpływu, ale jest to zachowanie. Natomiast opuszczania wywołanie może spowodować wyjątek przepełnienia stosu środowiska uruchomieniowego, usuwając wywołanie usuwa tę możliwość.