---
title: Ostrzeżenie kompilatora C4962 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4962
dev_langs:
- C++
helpviewer_keywords:
- C4962
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: caff08744497936839e1021cef8fc86e0e8aa7e5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066261"
---
# <a name="compiler-warning-c4962"></a>Ostrzeżenie kompilatora C4962

"Funkcja': optymalizacje profilowane wyłączone, ponieważ optymalizacje spowodowały niespójność danych profilu"

Funkcja nie został skompilowany przy użyciu /LTCG:PGO, ponieważ wiarygodne dane dotyczące liczby (profil) dla funkcji. Wykonaj ponownie profilowania, aby ponownie wygenerować pliku .pgc, który zawiera dane profilu zawodnych dla tej funkcji.

To ostrzeżenie jest domyślnie wyłączona. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).