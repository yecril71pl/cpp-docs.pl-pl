---
title: "Przegląd deklaracji | Dokumentacja firmy Microsoft"
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
- declarations, about declarations
- type qualifiers
ms.assetid: fcd2364c-c2a5-4fbf-9027-19dac4144cb5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aa6285504a194d909dec7a446437ca9f584272a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-declarations"></a>Przegląd deklaracji
"Deklaracji" Określa interpretacji i atrybuty zestaw identyfikatorów. Deklaracja powodujący magazynu, które mają zostać zarezerwowane dla obiekt lub funkcji o nazwie przez identyfikator jest nazywany "definition". Deklaracje C zmienne, funkcje i typy mają następującej składni:  
  
## <a name="syntax"></a>Składnia  
 `declaration`:  
 *Specyfikatory deklaracji* *seq atrybutu*opt*init deklarator listy*opt**;**  
  
 /\**seq atrybutu*opt dotyczy Microsoft * /  
  
 *Specyfikatory deklaracji*:  
 *Specyfikatory deklaracji Specyfikator klasy magazynu*opcjonalnych  
  
 *Specyfikatory deklaracji specyfikatora typu*opcjonalnych  
  
 *Specyfikatory deklaracji kwalifikator typu*opcjonalnych  
  
 *init — deklarator — lista*:  
 *init — deklarator*  
  
 *init — deklarator — lista* , *init deklarator*  
  
 *init — deklarator*:  
 *deklarator*  
  
 *deklarator***=***inicjatora*   
  
> [!NOTE]
>  Ta składnia `declaration` nie jest powtarzany w poniższych sekcjach. Składnia w poniższych sekcjach zazwyczaj rozpoczyna się od `declarator` nonterminal.  
  
 Deklaracje w *init deklarator listy* zawierają identyfikatory o nazwie; *init* jest formą skróconą dla inicjatora. *Init deklarator listy* jest rozdzielaną przecinkami sekwencję deklaratorów, z których każda może mieć typu dodatkowych informacji, i/lub inicjatora. `declarator` Zawiera identyfikatory, jeśli występują został zadeklarowany. *Specyfikatory deklaracji* nonterminal składa się z sekwencji specyfikatory typu i Klasa magazynu, które wskazują połączenie, okresem magazynu i jest częścią typu jednostek, które oznaczają deklaratorów. W związku z tym deklaracje składają się pewnej kombinacji specyfikatory klasy magazynowania, specyfikatorze typu kwalifikatory typu, deklaratorów i inicjatorów.  
  
 Deklaracje może zawierać jeden lub więcej atrybutów opcjonalnych wymienionych w *seq atrybutu*; *seq* stanowi skrót od sekwencji. Te atrybuty specyficzne dla firmy Microsoft wykonywania różnych funkcji, które opisano szczegółowo w niniejszym podręczniku.  
  
 Ogólne postać deklaracji zmiennej *specyfikatora typu* zawiera typ danych zmiennej. *Specyfikatora typu* może być złożone, jako modyfikacji typ przez **const** lub `volatile`. `declarator` Nadaje nazwę zmiennej, prawdopodobnie zmodyfikowane, aby zadeklarować tablicy lub typu wskaźnika. Na przykład  
  
```  
int const *fp;  
```  
  
 deklaruje zmienną o nazwie `fp` jako wskaźnik do niemodyfikowalnymi (**const**) `int` wartość. Można zdefiniować więcej niż jednej zmiennej w deklaracji przy użyciu wiele deklaratorów rozdzielonych przecinkami.  
  
 Deklaracja musi mieć co najmniej jeden deklarator lub jego specyfikatora typu musi zadeklarować tag struktury, złożenia tag lub elementy członkowskie wyliczenia. Deklaratory wprowadź wszelkie pozostałe informacje o identyfikatorze. Deklaratorze jest identyfikatorem, który może być modyfikowany w nawiasy (**[**), gwiazdki (**\***), lub nawiasy ( **()** ) Aby zadeklarować tablicę, wskaźnik, lub Funkcja wpisz odpowiednio. Przy deklarowaniu proste zmienne (takie jak znak, integer i zmiennoprzecinkowych elementy), lub struktur i Unii proste zmiennych `declarator` jest po prostu identyfikatorem. Aby uzyskać więcej informacji o deklaratorów, zobacz [deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md).  
  
 Wszystkie definicje są niejawnie deklaracje, ale nie wszystkie deklaracje definicje. Na przykład deklaracji zmiennych, które zaczynają się od `extern` Specyfikator klasy magazynu "odwołują się do," zamiast deklaracji "Definiowanie". Jeśli zmienna zewnętrzne jest do określonych przed jego zdefiniowaniem lub jest zdefiniowany w innym pliku źródłowego z jednego miejsca jest używany, `extern` deklaracja jest konieczne. Magazynu nie jest przydzielony przez "odwołuje się do" deklaracje nie można zainicjować zmienne w deklaracjach.  
  
 Klasy magazynu lub typu (lub obie) jest wymagany w deklaracji zmiennych. Z wyjątkiem `__declspec`, specyfikator tylko jedną klasę magazynu jest dozwolony w deklaracji i nie wszystkie specyfikatory klasy magazynowania są dozwolone w każdym kontekstu. `__declspec` Klasa magazynu jest dozwolone w przypadku innych specyfikatory klasy magazynowania i jest dozwolony więcej niż raz. Specyfikator klasy składującej deklaracji wpływa na sposób przechowywania i zainicjować element zadeklarowane i części programu, które mogą odwoływać się elementu.  
  
 *Specyfikator klasy magazynu* obejmują terminale zdefiniowany w języku C **automatycznie**, `extern`, **zarejestrować**, **statycznych**i `typedef`. Ponadto zawiera Microsoft C *Specyfikator klasy magazynu* terminali `__declspec`. Wszystkie *Specyfikator klasy magazynu* terminali z wyjątkiem `typedef` i `__declspec` omówiono w [klasy magazynu](../c-language/c-storage-classes.md). Zobacz [deklaracje Typedef](../c-language/typedef-declarations.md) informacji o `typedef`. Zobacz [rozszerzone atrybuty klasy magazynu](../c-language/c-extended-storage-class-attributes.md) informacji o `__declspec`.  
  
 Lokalizacja deklaracji w ramach programu źródłowego i obecności lub braku innych deklaracji zmiennej są ważne czynniki wpływające na okres istnienia zmiennych. Może istnieć wiele redeclarations, ale tylko jedną definicję. Jednak definicji może występować w więcej niż jednej jednostki tłumaczenia. Obiekty z wewnętrznym powiązaniem zastosowana ta reguła osobno do każdej jednostki tłumaczenia, ponieważ wewnętrznie połączone obiekty są unikatowe w jednostce tłumaczenia. W przypadku obiektów z zewnętrznym powiązaniem ta reguła ma zastosowanie do całego programu. Zobacz [okres istnienia, zakres, widoczność i połączenie](../c-language/lifetime-scope-visibility-and-linkage.md) Aby uzyskać więcej informacji na temat widoczności.  
  
 Specyfikatory typów dostarczają niektóre informacje o typach danych identyfikatorów. Domyślne specyfikatora typu `int`. Aby uzyskać więcej informacji, zobacz [specyfikatorze typu](../c-language/c-type-specifiers.md). Specyfikatory typów można również zdefiniować znaczniki typu, struktury i złożenia składnik nazwy i stałe wyliczenia. Aby uzyskać więcej informacji, zobacz [deklaracje modułów Wyliczających](../c-language/c-enumeration-declarations.md), [deklaracje struktur](../c-language/structure-declarations.md), i [deklaracje złożeń](../c-language/union-declarations.md).  
  
 Istnieją dwa *kwalifikator typu* terminale: **const** i `volatile`. Kwalifikatory określić dodatkowe właściwości typów, które mają zastosowanie tylko wtedy, gdy dostęp do obiektów tego typu za pośrednictwem l wartości. Aby uzyskać więcej informacji na temat **const** i `volatile`, zobacz [kwalifikatory typu](../c-language/type-qualifiers.md). Definicję l-wartości [wartości L i r wyrażenia](../c-language/l-value-and-r-value-expressions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Podsumowanie dotyczące składni języka C](../c-language/c-language-syntax-summary.md)   
 [Deklaracje i typy](../c-language/declarations-and-types.md)   
 [Podsumowanie deklaracji](../c-language/summary-of-declarations.md)