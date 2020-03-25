---
title: Ostrzeżenie kompilatora (poziom 4) C4513
ms.date: 11/04/2016
f1_keywords:
- C4513
helpviewer_keywords:
- C4513
ms.assetid: 6877334a-f30a-4184-9483-dac3348737a4
ms.openlocfilehash: f5f25465beb04c6f91d290d4c119d07d75dd8f54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185220"
---
# <a name="compiler-warning-level-4-c4513"></a>Ostrzeżenie kompilatora (poziom 4) C4513

"Class": nie można wygenerować destruktora

Kompilator nie może wygenerować domyślnego destruktora dla danej klasy; nie utworzono destruktora. Destruktor znajduje się w klasie bazowej, która nie jest dostępna dla klasy pochodnej. Jeśli klasa bazowa ma destruktor prywatny, ustaw go jako publiczną lub chronioną.
