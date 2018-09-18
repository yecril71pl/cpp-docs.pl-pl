---
title: Kompilator ostrzeżenie (poziom 4) C4710 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4710
dev_langs:
- C++
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1f6de17f7005db3834bfcfc93aff03f12f0293ce
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046098"
---
# <a name="compiler-warning-level-4-c4710"></a>Kompilator ostrzeżenie (poziom 4) C4710

'Funkcja': funkcja niewbudowana

Daną funkcję został wybrany dla wbudowane rozwijanie, ale kompilator nie wykonał wbudowanie.

Wbudowanie odbywa się według uznania kompilatora. **Wbudowane** — słowo kluczowe, takiej jak **zarejestrować** słowo kluczowe jest używane jako wskazówka dla kompilatora. Kompilator używa Algorytm heurystyczny, aby ustalić, czy powinien wbudowane konkretną funkcję w celu przyspieszenia kodu podczas kompilowania dla danej szybkości, czy powinien wbudowane konkretną funkcję, aby zmniejszyć rozmiar kodu podczas kompilowania dla miejsca. Kompilator będzie tylko wbudowanego bardzo małych funkcji podczas kompilowania dla miejsca.

W niektórych przypadkach kompilator będzie niewyrównane określonej funkcji mechanicznych powodów. Zobacz [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) listę przyczyn, kompilator może wbudowanych funkcji.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.