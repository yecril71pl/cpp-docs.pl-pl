---
title: "Zakres i widoczność | Dokumentacja firmy Microsoft"
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
- scope, levels
- visibility
- file scope [C++]
ms.assetid: a019eb7c-66ed-46a7-bc9f-89a963930a56
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c61d9c6f38851e48335f83cccfeb5a8bf4aba448
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="scope-and-visibility"></a>Zakres i widoczność
„Widoczność” identyfikatora określa części programu, w których można się do niego odwoływać (jego „zakres”). Identyfikator jest widoczny (tzn. może zostać użyty) tylko w częściach programu wchodzących w skład jego „zakresu”, który może być ograniczony (w celu zwiększenia restrykcyjności) do pliku, funkcji, bloku lub prototypu funkcji, w którym występuje. Zakres identyfikatora jest częścią programu, w której może być używana nazwa. Jest to czasami nazywane „zakresem słownikowym”. Istnieją cztery rodzaje zakresów: funkcji, pliku, bloku i prototypu funkcji.  
  
 Wszystkie identyfikatory z wyjątkiem etykiet mają zakres uzależniony od poziomu, na którym występuje deklaracja. Dla każdego rodzaju zakresu, widocznością identyfikatorów w programie rządzą następujące zasady:  
  
 Zakres pliku  
 Deklarator lub specyfikator typu dla identyfikatora z zakresem pliku pojawia się poza każdym blokiem lub listą parametrów i jest dostępny z dowolnego miejsca w jednostce translacji po jej deklaracji. Nazwy identyfikatorów z zakresem pliku są często nazywane „global” lub „external”. Zakres globalnego identyfikatora rozpoczyna się w miejscu jego definicji lub deklaracji i kończy się na końcu jednostki translacji.  
  
 Zakres funkcji  
 Etykieta jest jedynym rodzajem identyfikatora, który ma zakres funkcji. Etykieta jest niejawnie zadeklarowana przez jej użycie w instrukcji. Nazwy etykiet muszą być unikatowe w obrębie danej funkcji. (Aby uzyskać więcej informacji na temat etykiety i nazwy etykiet, zobacz [goto i Labeled — instrukcje](../c-language/goto-and-labeled-statements-c.md).)  
  
 Zakres bloku  
 Deklarator lub specyfikator typu dla identyfikatora z zakresem bloku pojawia się wewnątrz bloku lub listy deklaracji parametrów formalnych w definicji funkcji. Jest widoczny tylko od punktu jego deklaracji lub definicji do końca bloku, zawierającego jego deklarację lub definicję. Jej zakres jest ograniczony do tego bloku i wszelkich bloków zagnieżdżonych w tym bloku i kończy się nawiasem klamrowym, który zamyka skojarzony blok. Takie identyfikatory są czasami nazywane „zmiennymi lokalnymi”.  
  
 Zakres prototypu funkcji  
 Deklarator lub specyfikator typu dla identyfikatora z zakresem prototypu funkcji pojawia się w obrębie listy deklaracji parametrów prototypu funkcji (nie jest częścią deklaracji funkcji). Jej zakres kończy się z końcem deklaratora funkcji.  
  
 Deklaracje odpowiednie do tworzenia zmiennych widoczne w innych plikach źródłowych są opisane w [klasy magazynu](../c-language/c-storage-classes.md). Jednak funkcje i zmienne zadeklarowane na zewnętrznej poziomu z **statycznych** Specyfikator klasy magazynowania są widoczne tylko w obrębie pliku źródłowego, w którym jest zdefiniowany. Wszystkie pozostałe funkcje są widoczne globalnie.  
  
## <a name="see-also"></a>Zobacz też  
 [Okres istnienia, zakres, widoczność i połączenie](../c-language/lifetime-scope-visibility-and-linkage.md)