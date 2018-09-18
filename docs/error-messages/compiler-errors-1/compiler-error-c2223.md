---
title: Błąd kompilatora C2223 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2223
dev_langs:
- C++
helpviewer_keywords:
- C2223
ms.assetid: e4506f0f-0317-4a96-8a90-877a156d7939
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0ca3cd091b349536046b0ead8e52805db3dff9b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067665"
---
# <a name="compiler-error-c2223"></a>Błąd kompilatora C2223

po lewej "-> Identyfikator" musi wskazywać na struct/union

Argument operacji po lewej stronie `->` nie jest wskaźnik do klasy, struktury lub Unii.

Ten błąd może być spowodowany przez lewy operand, który jest niezdefiniowaną zmienną (w związku z tym wpisz `int`).