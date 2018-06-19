---
title: Połączenie zewnętrzne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43301686d5bdb964cf08e8123ff4c55475228567
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383205"
---
# <a name="external-linkage"></a>Połączenie zewnętrzne
Jeśli nie wykorzystuje pierwszej deklaracji na poziomie zakresu pliku dla identyfikatora **statycznych** Specyfikator klasy magazynowania, obiekt ma połączenie zewnętrzne.  
  
 Jeśli nie ma deklarację identyfikatora dla funkcji *Specyfikator klasy magazynu*, jego powiązanie jest określane dokładnie tak, jakby zostały zgłoszone z *Specyfikator klasy magazynu* `extern`. Czy deklaracja identyfikator obiektu zawiera zakres pliku i nie *Specyfikator klasy magazynu*, jego powiązanie jest zewnętrzny.  
  
 Nazwa identyfikatora z zewnętrznym powiązaniem wyznacza tej samej funkcji lub obiektu danych jako nie żadnej innej deklaracji dla tej samej nazwie z zewnętrznym powiązaniem. Deklaracje dwóch może być w tej samej jednostce tłumaczenia lub w innej tłumaczenia jednostki. Jeśli obiekt lub funkcji również ma globalny okres istnienia, obiekt lub funkcja jest współużytkowana przez całego programu.  
  
## <a name="see-also"></a>Zobacz też  
 [Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)