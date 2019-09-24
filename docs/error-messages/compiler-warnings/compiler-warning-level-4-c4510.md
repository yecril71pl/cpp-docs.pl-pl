---
title: Ostrzeżenie kompilatora (poziom 4) C4510
description: Ostrzeżenie kompilatora C4510 opis i rozwiązanie.
ms.date: 09/22/2019
f1_keywords:
- C4510
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
ms.openlocfilehash: 05a6d0fe42d8247d3328506d8772b2fa77b5703c
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230387"
---
# <a name="compiler-warning-level-4-c4510"></a>Ostrzeżenie kompilatora (poziom 4) C4510

> "*Class*": nie można wygenerować konstruktora domyślnego

Kompilator nie może wygenerować domyślnego konstruktora dla określonej klasy, która nie ma konstruktorów zdefiniowanych przez użytkownika. Nie można utworzyć obiektów tego typu.

Istnieje kilka sytuacji, które uniemożliwiają kompilatorowi generowanie domyślnego konstruktora, w tym:

- Element członkowski danych **const** .

- Element członkowski danych, który jest odwołaniem.

Aby rozwiązać ten problem, należy utworzyć zdefiniowany przez użytkownika Konstruktor domyślny dla klasy inicjującej tych członków.
