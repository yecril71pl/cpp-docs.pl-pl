---
title: 2.7.2.1 prywatne | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 079b4b84-f2b3-4050-a0ac-289493c36b3d
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a08faf39ab2f82d76a936c216ba6707bee5c240
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="2721-private"></a>2.7.2.1 — prywatny
`private` Klauzuli deklaruje zmienne na liście zmiennych ma charakter prywatny, aby każdy wątek w zespole. Składnia `private` klauzuli wygląda następująco:  
  
```  
private(variable-list)  
```  
  
 Zachowanie określonego w zmiennej `private` klauzuli ma następującą składnię. Nowy obiekt z automatycznym okresem magazynu jest przydzielany dla konstrukcji. Rozmiar i wyrównanie nowego obiektu zależą od typu zmiennej. Ten przydział występuje raz dla każdego wątku w zespole, a domyślny konstruktor jest wywoływany dla obiekt klasy, jeśli jest to konieczne. w przeciwnym razie wartość początkowa jest nieokreślony.  Oryginalny obiekt odwołuje się zmienna ma nieokreśloną wartość po wejściu do konstrukcja, nie muszą zostać zmodyfikowane w ramach zakresu dynamicznego konstrukcji i ma nieokreśloną wartość momencie opuszczenia konstrukcja.  
  
 W zakresie leksykalne dyrektywa konstrukcji zmienna odwołuje się do nowego obiektu prywatnej przydzielonej przez wątek.  
  
 Ograniczenia do `private` klauzuli są następujące:  
  
-   Zmienna typu klasy określonej w `private` klauzuli musi mieć konstruktora domyślnego dostępny, jednoznaczne.  
  
-   Określona w zmiennej `private` nie może mieć klauzuli **const**-kwalifikowanego typu, chyba że jego typ klasy `mutable` elementu członkowskiego.  
  
-   Określona w zmiennej `private` niekompletnego typu lub typ referencyjny nie może mieć klauzuli.  
  
-   Zmienne, które są widoczne w `reduction` klauzuli **równoległych** dyrektywy nie można określić w `private` klauzuli w dyrektywie podziału pracy, która jest powiązana z konstrukcji równoległych.