---
title: "Połączenie zewnętrzne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aef61c580306cc40ef1a89c6a389c7fbaf64a5f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="external-linkage"></a>Połączenie zewnętrzne
Jeśli nie wykorzystuje pierwszej deklaracji na poziomie zakresu pliku dla identyfikatora **statycznych** Specyfikator klasy magazynowania, obiekt ma połączenie zewnętrzne.  
  
 Jeśli nie ma deklarację identyfikatora dla funkcji *Specyfikator klasy magazynu*, jego powiązanie jest określane dokładnie tak, jakby zostały zgłoszone z *Specyfikator klasy magazynu* `extern`. Czy deklaracja identyfikator obiektu zawiera zakres pliku i nie *Specyfikator klasy magazynu*, jego powiązanie jest zewnętrzny.  
  
 Nazwa identyfikatora z zewnętrznym powiązaniem wyznacza tej samej funkcji lub obiektu danych jako nie żadnej innej deklaracji dla tej samej nazwie z zewnętrznym powiązaniem. Deklaracje dwóch może być w tej samej jednostce tłumaczenia lub w innej tłumaczenia jednostki. Jeśli obiekt lub funkcji również ma globalny okres istnienia, obiekt lub funkcja jest współużytkowana przez całego programu.  
  
## <a name="see-also"></a>Zobacz też  
 [Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)