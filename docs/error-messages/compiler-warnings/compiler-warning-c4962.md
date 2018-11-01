---
title: Ostrzeżenie kompilatora C4962
ms.date: 11/04/2016
f1_keywords:
- C4962
helpviewer_keywords:
- C4962
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
ms.openlocfilehash: e3f7b715da3774d8289fdd526cf1fa0b5bdddba6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585319"
---
# <a name="compiler-warning-c4962"></a>Ostrzeżenie kompilatora C4962

"Funkcja': optymalizacje profilowane wyłączone, ponieważ optymalizacje spowodowały niespójność danych profilu"

Funkcja nie został skompilowany przy użyciu /LTCG:PGO, ponieważ wiarygodne dane dotyczące liczby (profil) dla funkcji. Wykonaj ponownie profilowania, aby ponownie wygenerować pliku .pgc, który zawiera dane profilu zawodnych dla tej funkcji.

To ostrzeżenie jest domyślnie wyłączona. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).