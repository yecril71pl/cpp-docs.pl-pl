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
ms.openlocfilehash: 2b25f957615d738d0608f911736bb42f8e3731dd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391625"
---
# <a name="html-basics"></a>Podstawy HTML

W większości przeglądarek mają możliwość zbadania źródło HTML strony, które można przeglądać. Podczas wyświetlania źródła, zobaczysz liczbę tagów (Hypertext markup language) HTML są ujęte w nawiasy (<>) oraz z tekstem.

Poniższe kroki kompilacji prostą stronę sieci Web za pomocą tagów HTML. W tych krokach będzie wpisz zwykłego tekstu do pliku w Notatniku, wprowadzić kilka zmian, Zapisz plik i załadować ponownie stronę w przeglądarce, aby zobaczyć zmiany.

#### <a name="to-create-an-html-file"></a>Aby utworzyć plik HTML

1. Otwórz Notatnik lub dowolnym edytorze zwykły tekst.

1. Z **pliku** menu, wybierz **New**.

1. Wpisz następujące polecenia:

```
<HTML>
<HEAD>
<TITLE>Top HTML Tags</TITLE>
</HEAD>
</HTML>
```

1. Z **pliku** menu, wybierz **Zapisz**, a następnie zapisz plik jako c:\webpages\First.htm. Zostaw plik otwarty w edytorze.

1. Przełącznik do przeglądarki i z **pliku** menu, wybierz **Otwórz**, lub typu *file://C:/webpages/first.htm* w polu edycji adresu URL w przeglądarce. Powinien zostać wyświetlony pustą stronę z opisem okna "Najpopularniejsze tagi HTML".

     Zwróć uwagę, znaczniki są skojarzone i znajdują się w nawiasy ostre. Tagi nie jest rozróżniana wielkość liter, ale wielkość liter jest często używana, aby wyróżnić tagi.

     Tag \<HTML > uruchamia dokument i tagu \<polecenia > kończy go. Kończenie tagi (nie zawsze wymagane) są takie same jak tag początkowy, ale mają ukośnika (/) przed znacznikiem. Powinna istnieć bez spacji między nawiasu ostrego (<) a początkiem tag.

1. Przełącz do Notatnika i po  \< /HEAD > wiersz, wpisz:

```
<BODY>
    HTML is swell.
    Life is good.
</BODY>
```

1. Z **pliku** menu, wybierz **Zapisz**.

1. Przejdź z powrotem do przeglądarki, a następnie odśwież stronę.

     Wyrazy pojawi się w klienckim obszarze okna przeglądarki. Należy zauważyć, że powrót karetki jest ignorowana. Jeśli chcesz mieć podział wiersza, należy uwzględnić `<BR>` tagu po pierwszym wierszu.

     Aby uzyskać instrukcje, które należy wykonać, wstawianie tekstu na dowolnym \<treści > i  \< /BODY > do dodania do treści dokumentu.

9. Dodaj nagłówek:

```
<H3>Here's the big picture</H3>
```

10. Dodawanie obrazu, przy użyciu pliku GIF, zapisana w tym samym katalogu co strona:

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

12. Zamiast tego numer listy, należy użyć sparowane \<OL > i \</OL > tagi zamiast \<UL > i \</UL > tagów.

Która powinna rozpocząć pracę. Jeśli wspaniałych funkcji jest wyświetlane na stronie sieci Web, można znaleźć się, jak został on utworzony przez zbadanie źródła HTML. Edytorów HTML, takich jak Microsoft FrontPage może służyć do tworzenia stron zarówno proste, jak i zaawansowanych.

Poniżej przedstawiono całą źródła HTML w przypadku pliku, który został możesz tworzyć:

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

Aby uzyskać pełny opis znaczniki, atrybuty i rozszerzenia Zobacz specyfikację znaczników języka HTML (Hypertext):

[http://www.w3.org/pub/WWW/MarkUp/](http://www.w3.org/pub/www/markup/)

## <a name="see-also"></a>Zobacz też

[MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)

