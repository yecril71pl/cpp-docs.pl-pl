---
title: Ostrzeżenie kompilatora (poziom 4) C4718
ms.date: 11/04/2016
f1_keywords:
- C4718
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
ms.openlocfilehash: 48452ed53b93d7cd89daadd3f7ab3a69b453e1a1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198162"
---
# <a name="compiler-warning-level-4-c4718"></a>Ostrzeżenie kompilatora (poziom 4) C4718

"wywołanie funkcji": wywołanie cykliczne nie ma żadnych efektów ubocznych, usuwanie

Funkcja zawiera wywołanie cykliczne, ale w przeciwnym razie nie ma żadnych efektów ubocznych. Trwa usuwanie wywołania tej funkcji. Nie dotyczy to poprawnego programu, ale zachowanie to. Pozostawienie wywołania w może spowodować wyjątek przepełnienia stosu środowiska uruchomieniowego, usunięcie tego wywołania spowoduje usunięcie takiej możliwości.
