---
title: Podstawy HTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
ms.openlocfilehash: 6d3a692eab47a1309ee0248b51ab8563fb077d5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377248"
---
# <a name="html-basics"></a>Podstawy HTML

Większość przeglądarek ma możliwość badania źródła HTML przeglądanych stron. Podczas przeglądania źródła zostanie wyświetlonych kilka znaczników HTML (Język znaczników hipertekstowych), otoczonych nawiasami kątowymi (<>), przeplatanych tekstem.

Poniższe kroki używają tagów HTML do tworzenia prostej strony sieci Web. W tych krokach wpiszesz zwykły tekst do pliku w Notatniku, dokonasz kilku zmian, zapisz plik i ponownie załadujesz stronę w przeglądarce, aby zobaczyć zmiany.

#### <a name="to-create-an-html-file"></a>Aby utworzyć plik HTML

1. Otwórz Notatnik lub dowolny edytor zwykłego tekstu.

1. Z menu **Plik** wybierz polecenie **Nowy**.

1. Wpisz następujące wiersze:

    ```html
    <HTML>
    <HEAD>
    <TITLE>Top HTML Tags</TITLE>
    </HEAD>
    </HTML>
    ```

1. Z menu **Plik** wybierz polecenie **Zapisz**i zapisz plik jako c:\webpages\First.htm. Pozostaw plik otwarty w edytorze.

1. Przełącz się do przeglądarki i z menu **Plik** wybierz polecenie **Otwórz**lub *wpisz file://C:/webpages/first.htm* w polu edycji adresu URL przeglądarki. Powinna zostać wyświetlona pusta strona z podpisem okna "Najlepsze tagi HTML".

   Zwróć uwagę, że znaczniki są sparowane i są zawarte w nawiasach kątowych. W tagach nie rozróżnia się wielkość liter, ale wielkość liter jest często używana do wyróżniania znaczników.

   Tag \<HTML> uruchamia dokument, a tag \</HTML> go kończy. Znaczniki końcowe (nie zawsze wymagane) są takie same jak znacznik początkowy, ale mają ukośnik do przodu (/) przed tagiem. Między nawiasem kątowym (<) a początkiem znacznika nie powinno być spacji.

1. Przełącz się z powrotem \<do Notatnika i po wierszu /HEAD> wpisz:

    ```html
    <BODY>
        HTML is swell.
        Life is good.
    </BODY>
    ```

1. Z menu **Plik** wybierz polecenie **Zapisz**.

1. Przełącz się z powrotem do przeglądarki i odśwież stronę.

   Słowa pojawią się w obszarze klienta okna przeglądarki. Należy zauważyć, że zwrot karetki jest ignorowany. Jeśli chcesz mieć podział wiersza, musisz `<BR>` dołączyć znacznik po pierwszym wierszu.

   Aby uzyskać wszystkie następujące kroki, wstaw tekst w dowolnym miejscu między \<> i \</BODY>, aby dodać go do treści dokumentu.

1. Dodaj nagłówek:

    ```html
    <H3>Here's the big picture</H3>
    ```

1. Dodawanie obrazu przy użyciu pliku gif zapisanego w tym samym katalogu co strona:

    ```html
    <IMG src="yourfile.gif">
    ```

1. Dodaj listę:

    ```html
    <UL>Make me an unordered list.
    <LI>One programmer</LI>
    <LI>Ten SDKs</LI>
    <LI>Great Internet Apps</LI>
    </UL>
    ```

1. Zamiast znaczników> UL i \< \</UL> \<należy użyć sparowanych znaczników \<OL> i /OL>.

To powinno zacząć. Jeśli na stronie sieci Web jest widoczna wspaniała funkcja, możesz dowiedzieć się, jak została utworzona, sprawdzając źródło HTML. Edytory HTML, takie jak Microsoft Front Page, mogą być używane do tworzenia zarówno stron prostych, jak i zaawansowanych.

Oto całe źródło HTML dla pliku, który zostałeś budulcem:

```html
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

Pełny opis znaczników, atrybutów i rozszerzeń można znaleźć w specyfikacji języka HTML (Hypertext Markup Language):

[Najnowsza opublikowana wersja HTML](https://www.w3.org/TR/html/) w W3C.org.

## <a name="see-also"></a>Zobacz też

[MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)
