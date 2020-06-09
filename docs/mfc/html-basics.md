---
title: Podstawy HTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
ms.openlocfilehash: 29ca2e3df4981db22a10281ba2a2938fc91d5b46
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620003"
---
# <a name="html-basics"></a>Podstawy HTML

Większość przeglądarek ma możliwość zbadania źródła HTML przeglądanych stron. Po wyświetleniu źródła zobaczysz kilka tagów HTML (Hypertext Markup Language), otoczone nawiasami ostrymi (<>), przeplatanymi z tekstem.

W poniższych krokach użyto tagów HTML do utworzenia prostej strony internetowej. W tych krokach wpiszesz zwykły tekst do pliku w Notatniku, wprowadzisz kilka zmian, zapiszesz plik i załadujesz ponownie stronę w przeglądarce, aby zobaczyć zmiany.

#### <a name="to-create-an-html-file"></a>Aby utworzyć plik HTML

1. Otwórz Notatnik lub dowolny edytor zwykłego tekstu.

1. Z menu **plik** wybierz polecenie **Nowy**.

1. Wpisz następujące wiersze:

    ```html
    <HTML>
    <HEAD>
    <TITLE>Top HTML Tags</TITLE>
    </HEAD>
    </HTML>
    ```

1. Z menu **plik** wybierz polecenie **Zapisz**i Zapisz plik jako c:\webpages\First.htm. Pozostaw plik otwarty w edytorze.

1. Przejdź do przeglądarki, a następnie z menu **plik** wybierz polecenie **otwórz**lub wpisz *File://C:/webpages/first.htm* w polu edycji adresu URL w przeglądarce. Powinna zostać wyświetlona pusta strona z podpisem okna "Najważniejsze Tagi HTML".

   Zauważ, że Tagi są sparowane i znajdują się w nawiasach kątowych. W tagach nie jest rozróżniana wielkość liter, ale wielkie litery są często używane do wyróżniania tagów.

   Tag \<HTML> uruchamia dokument, a znacznik \</HTML> zostaje zakończony. Tagi końcowe (nie zawsze wymagane) są takie same jak tag początkowy, ale mają ukośnik (/) przed tagiem. Między nawiasem ostrym (<) i początkiem tagu nie powinny znajdować się spacje.

1. Przełącz się z powrotem do Notatnika, a po \</HEAD> wierszu wpisz:

    ```html
    <BODY>
        HTML is swell.
        Life is good.
    </BODY>
    ```

1. Z menu **plik** wybierz polecenie **Zapisz**.

1. Przełącz się z powrotem do przeglądarki i Odśwież stronę.

   Słowa pojawią się w obszarze klienta okna przeglądarki. Zwróć uwagę, że znak powrotu karetki został zignorowany. Jeśli chcesz mieć podział wiersza, musisz dołączyć `<BR>` tag po pierwszym wierszu.

   Dla wszystkich kroków, które należy wykonać, Wstaw tekst w dowolnym miejscu między elementami \<BODY> i, \</BODY> Aby dodać je do treści dokumentu.

1. Dodaj nagłówek:

    ```html
    <H3>Here's the big picture</H3>
    ```

1. Dodaj obraz przy użyciu pliku GIF zapisanego w tym samym katalogu, w którym znajduje się Strona:

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

1. Aby ponumerować listę zamiast tego, należy użyć par \<OL> i \</OL> tagów w miejscu \<UL> \</UL> tagów i.

Który powinien zostać wyświetlony. Jeśli zobaczysz wspaniałą funkcję na stronie sieci Web, możesz dowiedzieć się, jak została ona utworzona, badając źródło HTML. Edytory HTML, takie jak Microsoft Front Page, mogą służyć do tworzenia prostych i zaawansowanych stron.

Oto całe źródło HTML dla skompilowanego pliku:

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

Pełny opis tagów, atrybutów i rozszerzeń można znaleźć w specyfikacji HTML (HTML):

[Najnowsza opublikowana wersja języka HTML](https://www.w3.org/TR/html/) w W3C.org.

## <a name="see-also"></a>Zobacz też

[MFC — podstawy programowania Internetu](mfc-internet-programming-basics.md)
