---
title: Błąd kompilatora C2919
ms.date: 11/04/2016
f1_keywords:
- C2919
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
ms.openlocfilehash: 624b3ab47ccb1c934b612ec8648b5eee0d233690
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176978"
---
# <a name="compiler-error-c2919"></a>Błąd kompilatora C2919

"Type": nie można używać operatorów na publikowanej powierzchni typu WinRT

System typu środowisko wykonawcze systemu Windows nie obsługuje funkcji składowych operatorów na publikowanej powierzchni typu. Wynika to z faktu, że nie wszystkie języki mogą korzystać z funkcji Członkowskich operatora. Można tworzyć funkcje składowe operatora prywatnego lub wewnętrznego, które mogą być wywoływane C++ z kodu w tej samej klasie lub jednostce kompilacji.

Aby rozwiązać ten problem, Usuń funkcję członkowską operatora z interfejsu publicznego lub Zmień ją na nazwę funkcji członkowskiej. Na przykład zamiast `operator==`Nadaj nazwę funkcji członkowskiej `Equals`.
