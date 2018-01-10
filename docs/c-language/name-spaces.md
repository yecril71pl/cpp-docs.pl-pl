---
title: Nazwa spacje | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- union keyword [C], tags
- enumeration tags
- structure tags
- names [C++], declared elements
- name spaces [C++]
- tags, structure tags
- union keyword [C]
ms.assetid: b4bda1d1-cb5e-4f60-ac2b-29af93d8a9a2
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7833c7c1cfd9e7e2b408203f18cf955f6bafedd8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="name-spaces"></a>Przestrzenie nazw
Kompilator konfiguruje „przestrzenie nazw”, aby rozróżniać identyfikatory używane dla różnych rodzajów elementów. Nazwy w obrębie każdego przestrzeni nazw muszą być unikatowe, aby uniknąć konfliktu, ale identyczne nazwy mogą pojawiać się w więcej niż jednej przestrzeni nazw. Oznacza to, że można użyć tego samego identyfikatora dla dwóch lub więcej różnych elementów, pod warunkiem że elementy znajdują się w różnych obszarach nazw. Kompilator może rozpoznać odwołania na podstawie kontekstu składni identyfikatora w programie.  
  
> [!NOTE]
>  Nie należy mylić ograniczonego pojęcia obszar nazw C z cechą „przestrzeń nazw” języka C++. Zobacz [przestrzeni nazw](../cpp/namespaces-cpp.md) w języku C*++ materiały referencyjne dotyczące języka* Aby uzyskać więcej informacji.  
  
 Poniższa lista opisuje przestrzenie nazw używane w C.  
  
 Etykiety instrukcji  
 Nazwane etykiety instrukcji są częścią instrukcji. Definicje etykiety instrukcji są zawsze następuje dwukropek, ale nie jest częścią są **przypadku** etykiety. Użycia etykiet instrukcji zawsze znajdują się bezpośrednio po słowie kluczowym `goto`. Etykiety instrukcji nie muszą być różne od innych nazw lub nazw etykiet w innych funkcjach.  
  
 Znaczniki struktury, unii i wyliczenia  
 Znaczniki są częścią struktury, Unii i wyliczenia specyfikatorze typu i jeśli jest obecny, zawsze występować zaraz po słów zastrzeżonych `struct`, **Unii**, lub `enum`. Nazwy tagów muszą być różne od innych tagów struktur, wyliczeń lub unii o tej samej widoczności.  
  
 Elementy członkowskie struktur lub unii  
 Nazwy elementów członkowskich są przydzielane w przestrzeniach nazw skojarzonych z każdym typem struktury i unii. Oznacza to, że ten sam identyfikator może być nazwą składnika w dowolnej liczbie struktur lub unii w tym samym czasie. Definicje nazw składników zawsze występują w ramach specyfikatora typu struktury lub unii. Używa nazwy składnika zawsze występować zaraz po operatory wyboru elementu członkowskiego ( **->**  i **.**). Nazwa składnika musi być unikatowa w obrębie struktury lub unii, ale nie musi być odmienna od innych nazw w programie, łącznie z nazwami elementów członkowskich różnych struktur i unii, lub nazw w samej strukturze.  
  
 Zwykłe identyfikatory  
 Wszystkie inne nazwy dzielą się na obszar nazw, który zawiera zmienne, funkcje (w tym parametry formalne i zmienne lokalne) oraz stałe wyliczeń. Nazwy identyfikatorów mają zagnieżdżoną widoczność, więc można je zmienić w ramach bloku.  
  
 Nazwy elementów typedef  
 Nazwy elementów typedef nie mogą być używane jako identyfikatory w tym samym zakresie.  
  
 Na przykład, ponieważ znaczniki struktury, elementy struktury i nazwy zmiennych są w trzech różnych obszarach nazw, trzy elementy o nazwie `student` w tym przykładzie nie będą w konflikcie. Kontekst każdego elementu pozwala na poprawną interpretację poszczególnych wystąpień `student` w programie. (Dla informacji na temat struktury, zobacz [deklaracje struktur](../c-language/structure-declarations.md).)  
  
```  
struct student {  
   char student[20];  
   int class;  
   int id;  
   } student;  
```  
  
 Gdy `student` pojawia się po słowie kluczowym `struct`, kompilator rozpoznaje je jako tag struktury. Gdy `student` pojawia się po operatorze wyboru elementu członkowskiego ( **->**  lub **.**), nazwa odwołuje się do elementu członkowskiego struktury. W innych kontekstach `student` odwołuje się do zmiennej struktury. Jednakże przeładowanie tagu przestrzeni nazw nie jest zalecane, ponieważ następuje ukrycie znaczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura programu](../c-language/program-structure.md)