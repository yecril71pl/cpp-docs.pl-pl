---
title: Ostrzeżenie kompilatora (poziom 4) C4510
description: Ostrzeżenie kompilatora C4510 opis i rozwiązanie.
ms.date: 09/22/2019
f1_keywords:
- C4510
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
ms.openlocfilehash: e4bb688266d9fe638978d2d3fa2666b83b3e6cc9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225257"
---
# <a name="compiler-warning-level-4-c4510"></a>Ostrzeżenie kompilatora (poziom 4) C4510

> "*Class*": nie można wygenerować konstruktora domyślnego

Kompilator nie może wygenerować domyślnego konstruktora dla określonej klasy, która nie ma konstruktorów zdefiniowanych przez użytkownika. Nie można utworzyć obiektów tego typu.

Istnieje kilka sytuacji, które uniemożliwiają kompilatorowi generowanie domyślnego konstruktora, w tym:

- **`const`** Element członkowski danych.

- Element członkowski danych, który jest odwołaniem.

Aby rozwiązać ten problem, należy utworzyć zdefiniowany przez użytkownika Konstruktor domyślny dla klasy inicjującej tych członków.
