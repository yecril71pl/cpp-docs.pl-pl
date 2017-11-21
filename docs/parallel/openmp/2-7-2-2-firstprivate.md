---
title: 2.7.2.2 firstprivate | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: ece6ff12-2be1-4e4f-866c-d39345fd87b5
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ac868b33e8a53778faa3fba9724974e4af6ffb90
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="2722-firstprivate"></a>2.7.2.2 — firstprivate
**Firstprivate** klauzuli stanowi nadzbiór funkcje udostępniane przez **prywatnej** klauzuli. Składnia **firstprivate** klauzuli wygląda następująco:  
  
```  
firstprivate(variable-list)  
```  
  
 Zmienne określone w *zmiennej listy* ma **prywatnej** semantyki klauzuli, zgodnie z opisem w [sekcji 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) na stronie 25. Inicjowanie lub konstrukcji odbywa się tak, jakby były wykonywane raz na wątek, przed wykonaniem wątku konstrukcji. Aby uzyskać **firstprivate** klauzuli na konstrukcję równoległe, wartość początkowa nowego obiektu prywatnego to wartość oryginalny obiekt, który istnieje bezpośrednio przed równoległych konstrukcja dla wątku, który wykryje on. Aby uzyskać **firstprivate** klauzula w konstrukcji podziału pracy, wartość początkowa nowego obiektu prywatny dla każdego wątku, który wykonuje konstrukcji podziału pracy jest wartością oryginalny obiekt, który istnieje przed punktu w czasie który tym samym wątku napotka konstrukcji podziału pracy. Ponadto dla obiektów C++ nowy obiekt prywatny dla każdego wątku jest kopiowania utworzone na podstawie obiektu oryginalnego.  
  
 Ograniczenia do **firstprivate** klauzuli są następujące:  
  
-   Określona w zmiennej **firstprivate** niekompletnego typu lub typ referencyjny nie może mieć klauzuli.  
  
-   Zmienna typu klasy jest określony jako **firstprivate** musi mieć Konstruktor kopiujący dostępny, jednoznaczne.  
  
-   Zmienne, które są prywatne w ramach równoległego regionu lub które są widoczne w **redukcji** klauzuli **równoległych** dyrektywy nie można określić w **firstprivate** klauzula w dyrektywa podziału pracy, która jest powiązana z konstrukcji równoległych.