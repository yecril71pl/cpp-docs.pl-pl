---
title: Klasa magazynu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- linkage [C++], external
- function storage class
- function specifiers, storage class
- storage classes
- Microsoft-specific storage classes
- external linkage, storage-class specifiers
- static storage class specifiers
ms.assetid: 39a79ba6-edf5-42b6-8e45-f94227603dd6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ecd50ddf72fbafb23571e2b2709418e4eb89093e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="storage-class"></a>Klasa magazynu
Specyfikator klasy magazynu w definicji funkcji zapewnia funkcję albo `extern` lub **statycznej** klasy magazynu.  
  
## <a name="syntax"></a>Składnia  
 *Definicja funkcji*:  
 *Specyfikatory deklaracji* opt*seq atrybutu* opt*lista deklaracji deklarator* opt*złożonej instrukcji*  
  
 /\* *Atrybut seq* jest Specific Microsoft * /  
  
 *Specyfikatory deklaracji*:  
 *Specyfikatory deklaracji Specyfikator klasy magazynu* opcjonalnych  
  
 *Specyfikatory deklaracji specyfikatora typu* opcjonalnych  
  
 *Specyfikatory deklaracji kwalifikator typu* opcjonalnych  
  
 *Specyfikator klasy magazynu*: /\* definicje funkcji \*/  
 **extern**  
  
 **static**  
  
 Jeśli nie ma definicji funkcji *Specyfikator klasy magazynu*, wartością domyślną klasę magazynu `extern`. Można jawnie zadeklarować funkcję jako `extern`, ale nie jest to wymagane.  
  
 Jeśli w deklaracji funkcji zawiera *Specyfikator klasy magazynu* `extern`, identyfikator ma tego samego powiązania jako żadnych zgłoszenia widocznych identyfikatora z zakresem pliku. Jeśli nie ma żadnej widocznej deklaracji z zakresem pliku, identyfikator ma powiązania zewnętrzne. Jeśli identyfikator ma zakres pliku i nie *Specyfikator klasy magazynu*, identyfikator ma połączenie zewnętrzne. Powiązania zewnętrzne oznaczają, że każde wystąpienie identyfikatora oznacza ten sam obiekt lub funkcję. Zobacz [okres istnienia, zakres, widoczność i połączenie](../c-language/lifetime-scope-visibility-and-linkage.md) uzyskać więcej informacji dotyczących zakresu połączenie i plik.  
  
 Deklaracje funkcji o zakresie bloku ze specyfikatorem klasy magazynu innym niż `extern`.  
  
 Funkcja z **statycznych** Klasa magazynu jest widoczna tylko w pliku źródłowym, w którym jest zdefiniowany. Wszystkie inne funkcje, niezależnie od tego, czy posiadają klasę magazynu `extern` jawnie lub niejawnie, są widoczne we wszystkich plikach z kodem źródłowym w programie. Jeśli **statycznych** Klasa magazynu jest pożądane, może być deklarowana na pierwsze wystąpienie deklaracji funkcji (jeśli istnieje), a w definicji funkcji.  
  
 **Microsoft Specific**  
  
 Po włączeniu rozszerzenia Microsoft funkcji pierwotnie zadeklarowana bez klasy magazynu (lub `extern` klasy magazynu) podano **statycznych** klasy magazynu, jeśli z definicji funkcji znajduje się w tym samym pliku źródłowego i Definicja jawnie określa **statycznej** klasy magazynu.  
  
 Podczas kompilacji z opcją kompilatora /Ze, funkcje zadeklarowane wewnątrz bloku za pomocą słowa kluczowego `extern` mają globalną widoczność. Nie ma to zastosowania podczas kompilowania z opcją /Za. Na tej funkcji nie można polegać, jeżeli trzeba uwzględnić przenośność kodu źródłowego.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Definicje funkcji języka C](../c-language/c-function-definitions.md)