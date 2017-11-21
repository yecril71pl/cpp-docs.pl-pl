---
title: "Połączenie zewnętrzne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c4a1981d2dd22f9ed8928b1d1daf71612b057e71
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="external-linkage"></a>Połączenie zewnętrzne
Jeśli nie wykorzystuje pierwszej deklaracji na poziomie zakresu pliku dla identyfikatora **statycznych** Specyfikator klasy magazynowania, obiekt ma połączenie zewnętrzne.  
  
 Jeśli nie ma deklarację identyfikatora dla funkcji *Specyfikator klasy magazynu*, jego powiązanie jest określane dokładnie tak, jakby zostały zgłoszone z *Specyfikator klasy magazynu* `extern`. Czy deklaracja identyfikator obiektu zawiera zakres pliku i nie *Specyfikator klasy magazynu*, jego powiązanie jest zewnętrzny.  
  
 Nazwa identyfikatora z zewnętrznym powiązaniem wyznacza tej samej funkcji lub obiektu danych jako nie żadnej innej deklaracji dla tej samej nazwie z zewnętrznym powiązaniem. Deklaracje dwóch może być w tej samej jednostce tłumaczenia lub w innej tłumaczenia jednostki. Jeśli obiekt lub funkcji również ma globalny okres istnienia, obiekt lub funkcja jest współużytkowana przez całego programu.  
  
## <a name="see-also"></a>Zobacz też  
 [Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)