---
title: "Przegląd funkcji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- functions [C++]
- control flow, function calls
ms.assetid: b6f4637f-02b9-49d8-8601-1f886bd2cfb9
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 093400e5d98b0b5e0336c2f640ed0937bdb157b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-functions"></a>Przegląd funkcji
Funkcje musi zawierać definicję i powinien mieć deklaracji, mimo że definicji może służyć jako deklaracji, jeśli deklaracja występuje przed wywołaniem funkcji. Definicja funkcji zawiera treść funkcji — kod, który jest wykonywany, gdy jest wywoływana funkcja.  
  
 Deklaracja funkcji Określa nazwę, zwracany typ i atrybuty funkcję, która jest zdefiniowana w innym miejscu w programie. Deklaracja funkcji musi poprzedzać wywołania funkcji. Jest to, dlaczego plików nagłówka zawierającego deklaracje funkcji środowiska wykonawczego znajdują się w kodzie przed wywołaniem funkcji środowiska wykonawczego. Gdy deklaracja zawiera informacje o typach i liczba parametrów, deklaracja jest prototypu. Zobacz [prototypy funkcji](../c-language/function-prototypes.md) Aby uzyskać więcej informacji.  
  
 Kompilator używa prototyp do porównania z typami argumentów w kolejnych wywołaniach funkcji z parametrów funkcji i konwertowania typy argumentów do typów parametrów zawsze, gdy jest to konieczne.  
  
 Wywołanie funkcji przekazuje Kontrola wykonywania z funkcji wywołującej do wywołanej funkcji. Argumenty, jeśli taki występuje, są przekazywane przez wartość do wywołanej funkcji. Wykonywanie `return` instrukcji w wywołana funkcja zwraca kontroli i prawdopodobnie wartość wywołania funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../c-language/functions-c.md)