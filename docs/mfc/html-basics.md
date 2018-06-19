---
title: Podstawy HTML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c59004f27e0f3a1c629daae621df831fe82cd7a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347220"
---
# <a name="html-basics"></a>Podstawy HTML
W większości przeglądarek mają możliwość badania źródło HTML strony, które możesz przeglądać. Po wyświetleniu źródła zobaczysz liczba tagów HTML (Hypertext markup language) ujęta w nawiasy (<>) oraz tekst.  
  
 Poniższe kroki użyć tagów HTML do zbudowania prostego strony sieci Web. W tych krokach będzie wpisz zwykłego tekstu do pliku w Notatniku, wprowadzić kilka zmian, Zapisz plik i ponownie załaduj stronę w przeglądarce, aby zobaczyć zmiany.  
  
#### <a name="to-create-an-html-file"></a>Aby utworzyć plik HTML  
  
1.  Otwórz Notatnik lub dowolnego edytora tekstów.  
  
2.  Z **pliku** menu, wybierz `New`.  
  
3.  Wpisz następujące wiersze:  
  
 ```  
 <HTML>  
 <HEAD>  
 <TITLE>Top HTML Tags</TITLE>  
 </HEAD>  
 </HTML>  
 ```  
  
4.  Z **pliku** menu, wybierz **zapisać**i Zapisz plik jako c:\webpages\First.htm. Zostaw plik otwarty w edytorze.  
  
5.  Przełącznik do przeglądarki, a także z **pliku** menu, wybierz **Otwórz**, lub typ `file://C:/webpages/first.htm` edytowania w przeglądarce adres URL. Powinna zostać wyświetlona pusta strona z tytuł okna "Top tagów HTML".  
  
     Zwróć uwagę, znaczniki są skojarzone i znajdują się w nawiasy. Tagi nie są z uwzględnieniem wielkości liter, ale wielkość liter jest często umożliwia znaczniki wyróżnienia.  
  
     Tag \<HTML > rozpoczyna dokumentu i tagu \<polecenia > kończy się go. Kończenie tagi (nie zawsze wymagana) są takie same jak tag początkowy, ale ma ukośnika (/) przed tagu. Należy między nawiasu ostrego (<) i uruchom z tagu nie może zawierać spacji.  
  
6.  Przełącz do Notatnika i po  \< /HEAD > wiersz, wpisz:  
  
 ```  
 <BODY>  
    HTML is swell.  
    Life is good.  
 </BODY>  
 ```  
  
7.  Z **pliku** menu, wybierz **zapisać**.  
  
8.  Wrócić do przeglądarki i Odśwież stronę.  
  
     Wyrazy będą wyświetlane w klienckim obszarze okna przeglądarki. Zwróć uwagę, że powrót karetki jest ignorowane. Jeśli chcesz mieć podział wiersza musi zawierać `<BR>` tagu po pierwszym wierszu.  
  
     Aby uzyskać instrukcje, które należy wykonać, wstawianie tekstu na dowolnym \<treści > i  \< /BODY > do dodania do treści dokumentu.  
  
9. Dodaj nagłówek:  
  
 ```  
 <H3>Here's the big picture</H3>  
 ```  
  
10. Dodawanie obrazu, przy użyciu pliku GIF zapisane w tym samym katalogu co strona:  
  
 ```  
 <IMG src="yourfile.gif">  
 ```  
  
11. Dodaj listę:  
  
 ```  
 <UL>Make me an unordered list.  
 <LI>One programmer</LI>  
 <LI>Ten SDKs</LI>  
 <LI>Great Internet Apps</LI>  
 </UL>  
 ```  
  
12. Aby zamiast tego numeru listy, użyj łączyć \<OL > i \</OL > Znaczniki zamiast \<UL > i \</UL > tagów.  
  
 Który powinna ułatwiające rozpoczęcie pracy. Jeśli widzisz wspaniałych funkcji na stronie sieci Web można znaleźć sposobu utworzenia, sprawdzając źródła HTML. Edytora HTML, takiego jak Microsoft FrontPage może służyć do tworzenia stron zarówno proste, jak i zaawansowane.  
  
 Oto całego źródła HTML w pliku, który należy już został tworzenie:  
  
```  
<HTML>  
<HEAD>  
<TITLE>Top HTML Tags</TITLE>  
</HEAD>  
<BODY>  
HTML is swell.<BR>  
Life is good.  
<H3>Here's the big picture</H3>  
<IMG src="yourfile.gif">  
<UL>Make me an unordered list.  
<LI>One programmer</LI>  
<LI>Ten SDKs</LI>  
<LI>Great Internet Apps</LI>  
</UL>  
</BODY>  
</HTML>  
```  
  
 Pełny opis tagów, atrybutów i rozszerzeń zobacz specyfikację Hypertext Markup Language (HTML):  
  
 [http://www.w3.org/pub/WWW/MarkUp/](http://www.w3.org/pub/www/markup/)  
  
## <a name="see-also"></a>Zobacz też  
 [MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)

