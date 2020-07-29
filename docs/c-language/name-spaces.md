---
title: Przestrzenie nazw
ms.date: 11/04/2016
helpviewer_keywords:
- union keyword [C], tags
- enumeration tags
- structure tags
- names [C++], declared elements
- name spaces [C++]
- tags, structure tags
- union keyword [C]
ms.assetid: b4bda1d1-cb5e-4f60-ac2b-29af93d8a9a2
ms.openlocfilehash: 28036219464e96ae20733473dedb4fab63f6de38
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218822"
---
# <a name="name-spaces"></a>Przestrzenie nazw

Kompilator konfiguruje „przestrzenie nazw”, aby rozróżniać identyfikatory używane dla różnych rodzajów elementów. Nazwy w obrębie każdego przestrzeni nazw muszą być unikatowe, aby uniknąć konfliktu, ale identyczne nazwy mogą pojawiać się w więcej niż jednej przestrzeni nazw. Oznacza to, że można użyć tego samego identyfikatora dla dwóch lub więcej różnych elementów, pod warunkiem że elementy znajdują się w różnych obszarach nazw. Kompilator może rozpoznać odwołania na podstawie kontekstu składni identyfikatora w programie.

> [!NOTE]
> Nie należy mylić ograniczonego pojęcia obszar nazw C z cechą „przestrzeń nazw” języka C++. Aby uzyskać więcej informacji, zobacz [przestrzenie nazw](../cpp/namespaces-cpp.md) w dokumentacji języka C++.

Poniższa lista opisuje przestrzenie nazw używane w C.

Etykiety instrukcji o nazwanych etykietach instrukcji są częścią instrukcji. Po definicjach etykiet instrukcji zawsze następuje dwukropek, ale nie są one częścią **`case`** etykiet. Użycie etykiet instrukcji zawsze następuje bezpośrednio po słowie kluczowym **`goto`** . Etykiety instrukcji nie muszą być różne od innych nazw lub nazw etykiet w innych funkcjach.

Tagi struktury, Unii i wyliczenia te Tagi są częścią specyfikatorów typu struktury, Unii i wyliczenia oraz, jeśli są obecne, zawsze bezpośrednio przestrzegać słów zarezerwowanych **`struct`** , **`union`** lub **`enum`** . Nazwy tagów muszą być różne od innych tagów struktur, wyliczeń lub unii o tej samej widoczności.

Elementy członkowskie struktur lub składowych Unii są przydzieleni do przestrzeni nazw skojarzonych z każdą strukturą i typem Unii. Oznacza to, że ten sam identyfikator może być nazwą składnika w dowolnej liczbie struktur lub unii w tym samym czasie. Definicje nazw składników zawsze występują w ramach specyfikatora typu struktury lub unii. Użycia nazw składników zawsze są bezpośrednio zgodne z operatorami wyboru elementu członkowskiego ( **->** i **.**). Nazwa składnika musi być unikatowa w obrębie struktury lub unii, ale nie musi być odmienna od innych nazw w programie, łącznie z nazwami elementów członkowskich różnych struktur i unii, lub nazw w samej strukturze.

Zwykłe identyfikatory wszystkie inne nazwy mieszczą się w przestrzeni nazw, która zawiera zmienne, funkcje (w tym parametry formalne i zmienne lokalne) oraz stałe wyliczenia. Nazwy identyfikatorów mają zagnieżdżoną widoczność, więc można je zmienić w ramach bloku.

Nazwy typedef nazw typedef nie mogą być używane jako identyfikatory w tym samym zakresie.

Na przykład, ponieważ znaczniki struktury, elementy struktury i nazwy zmiennych są w trzech różnych obszarach nazw, trzy elementy o nazwie `student` w tym przykładzie nie będą w konflikcie. Kontekst każdego elementu pozwala na poprawną interpretację poszczególnych wystąpień `student` w programie. (Aby uzyskać informacje na temat struktur, zobacz [deklaracje struktury](../c-language/structure-declarations.md)).

```C
struct student {
   char student[20];
   int class;
   int id;
   } student;
```

Gdy `student` pojawia się po **`struct`** słowie kluczowym, kompilator rozpoznaje go jako tag struktury. Gdy `student` pojawia się po operatorze wyboru elementu członkowskiego ( **->** lub **.**), nazwa odwołuje się do elementu członkowskiego struktury. W innych kontekstach `student` odwołuje się do zmiennej struktury. Jednakże przeładowanie tagu przestrzeni nazw nie jest zalecane, ponieważ następuje ukrycie znaczenia.

## <a name="see-also"></a>Zobacz także

[Struktura programu](../c-language/program-structure.md)
