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
ms.openlocfilehash: ebf1961d83d14bf95633d4248c2f970c54923274
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51325994"
---
# <a name="name-spaces"></a>Przestrzenie nazw

Kompilator konfiguruje „przestrzenie nazw”, aby rozróżniać identyfikatory używane dla różnych rodzajów elementów. Nazwy w obrębie każdego przestrzeni nazw muszą być unikatowe, aby uniknąć konfliktu, ale identyczne nazwy mogą pojawiać się w więcej niż jednej przestrzeni nazw. Oznacza to, że można użyć tego samego identyfikatora dla dwóch lub więcej różnych elementów, pod warunkiem że elementy znajdują się w różnych obszarach nazw. Kompilator może rozpoznać odwołania na podstawie kontekstu składni identyfikatora w programie.

> [!NOTE]
> Nie należy mylić ograniczonego pojęcia obszar nazw C z cechą „przestrzeń nazw” języka C++. Zobacz [przestrzenie nazw](../cpp/namespaces-cpp.md) w dokumentacji języka C++, aby uzyskać więcej informacji.

Poniższa lista opisuje przestrzenie nazw używane w C.

Etykiety instrukcji nazwane etykiety instrukcji są częścią instrukcji. Definicjach etykiet instrukcji zawsze następuje dwukropek, ale nie są częścią **przypadek** etykiety. Użycia etykiet instrukcji zawsze od razu po słowie kluczowym **goto**. Etykiety instrukcji nie muszą być różne od innych nazw lub nazw etykiet w innych funkcjach.

Znaczniki struktury, Unii i wyliczenia te znaczniki należą do struktury, Unii i wyliczenia specyfikatory typu i, jeśli jest obecne, zawsze od razu postępuj zgodnie z słów zastrzeżonych **struktury**, **Unii**, lub **wyliczenia**. Nazwy tagów muszą być różne od innych tagów struktur, wyliczeń lub unii o tej samej widoczności.

Elementy członkowskie struktur lub Unii nazwy elementów członkowskich są przydzielane w przestrzeniach nazw skojarzonych z każdym typem struktury i Unii. Oznacza to, że ten sam identyfikator może być nazwą składnika w dowolnej liczbie struktur lub unii w tym samym czasie. Definicje nazw składników zawsze występują w ramach specyfikatora typu struktury lub unii. Użycia nazw składników zawsze znajdują się bezpośrednio po operatory wyboru elementu członkowskiego (**->** i **.**). Nazwa składnika musi być unikatowa w obrębie struktury lub unii, ale nie musi być odmienna od innych nazw w programie, łącznie z nazwami elementów członkowskich różnych struktur i unii, lub nazw w samej strukturze.

Zwykłe identyfikatory inne nazwy dzielą się na przestrzeń nazw, który zawiera zmienne, funkcje (w tym parametry formalne i zmienne lokalne) oraz stałe wyliczeń. Nazwy identyfikatorów mają zagnieżdżoną widoczność, więc można je zmienić w ramach bloku.

Nazwy elementów TypeDef nazwy elementów Typedef nie może służyć jako identyfikatory w tym samym zakresie.

Na przykład, ponieważ znaczniki struktury, elementy struktury i nazwy zmiennych są w trzech różnych obszarach nazw, trzy elementy o nazwie `student` w tym przykładzie nie będą w konflikcie. Kontekst każdego elementu pozwala na poprawną interpretację poszczególnych wystąpień `student` w programie. (Aby uzyskać informacje dotyczące struktur, zobacz [deklaracje struktur](../c-language/structure-declarations.md).)

```C
struct student {
   char student[20];
   int class;
   int id;
   } student;
```

Gdy `student` pojawia się po **struktury** — słowo kluczowe, kompilator rozpoznaje je jako tag struktury. Gdy `student` pojawia się po operatorze wyboru składowej (**->** lub **.**), nazwa odnosi się do elementu członkowskiego struktury. W innych kontekstach `student` odwołuje się do zmiennej struktury. Jednakże przeładowanie tagu przestrzeni nazw nie jest zalecane, ponieważ następuje ukrycie znaczenia.

## <a name="see-also"></a>Zobacz też

[Struktura programu](../c-language/program-structure.md)