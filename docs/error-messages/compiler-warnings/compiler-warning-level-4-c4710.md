---
title: "Kompilatora (poziom 4) ostrzeżenie C4710 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4710
dev_langs:
- C++
helpviewer_keywords:
- C4710
ms.assetid: 76381ec7-3fc1-4bee-9a0a-c2c8307b92e2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0464d924c21a029a97a8f03d30f88127f3aea6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4710"></a>Kompilator C4710 ostrzegawcze (poziom 4)
"Funkcja": funkcja nie została wbudowana  
  
 Dana funkcja zostały wybrane do rozszerzenie funkcji wbudowanej, ale nie wykonał kompilator ze śródwierszowaniem.  
  
 Ze Śródwierszowaniem jest wykonywane według uznania kompilatora. **Wbudowanego** — słowo kluczowe, takiej jak **zarejestrować** — słowo kluczowe, stanowi wskazówkę dla kompilatora. Kompilator używa Algorytm heurystyczny w celu określenia, czy powinno wbudowanego konkretną funkcję w celu przyspieszenia kodu podczas kompilowania dla danej szybkości, czy powinno wbudowanego określonej funkcji, aby zmniejszyć rozmiar kodu podczas kompilowania dla miejsca do. Kompilator będzie tylko wbudowanego bardzo małe funkcje w przypadku kompilowania kodu dla miejsca.  
  
 W niektórych przypadkach kompilator będzie niewyrównane konkretną funkcję mechaniczne ze względu na. Zobacz [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) listę przyczyn kompilator może wbudowanej funkcji.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.