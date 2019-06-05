---
title: Modyfikowanie kontrolki ATL DHTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, modifying
- DHTML controls
- DHTML controls, modifying
ms.assetid: c053f35f-8629-4600-9595-721f5956777a
ms.openlocfilehash: e594360cc6752a60bf2e07a1fb1d02041604d959
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503004"
---
# <a name="modifying-the-atl-dhtml-control"></a>Modyfikowanie kontrolki ATL DHTML

Kreator kontrolki ATL zawiera kod startowy, dzięki czemu można tworzyć i uruchamiać kontrolki, więc możesz zobaczyć jak metody są zapisywane w plikach projektu i jak DHTML wywołuje kod C++ formantu przy użyciu metod wysyłania. Możesz dodać dowolną metodę wysyłania do interfejsu. Następnie możesz wywołać metod w zasobie HTML.

## <a name="to-modify-the-atl-dhtml-control"></a>Aby zmodyfikować kontrolki ATL DHTML

1. W **Widok klas**, rozwiń węzeł projektu kontroli.

   Należy zauważyć, że interfejs, który kończy się na "Interfejsu" ma jedną metodę `OnClick`. Interfejs, który nie kończy się w interfejsie "użytkownika" nie ma żadnych metod.

1. Dodaj metodę o nazwie `MethodInvoked` do interfejsu, który nie kończy się w interfejsie "użytkownika".

   Ta metoda zostanie dodany do interfejsu, który jest używany w kontenerze kontrolek do interakcji z kontenera, z interfejs używany przez DHTML wchodzić w interakcje z kontrolką. Tylko kontenera można wywołać tej metody.

1. Znajdź metoda zastąpić jej metodą zastępczą w poziomie w pliku .cpp i Dodaj kod, aby wyświetlić okno komunikatu, na przykład:

   [!code-cpp[NVC_ATL_COM#5](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_1.cpp)]

1. Dodaj inną metodę o nazwie `HelloHTML`, tylko tym razem Dodaj go do interfejsu, który kończy się w interfejsie "użytkownika". Znajdź zastąpić jej metodą zastępczą poza `HelloHTML` metody w .cpp pliku i Dodaj kod, aby wyświetlić okno komunikatu, na przykład:

   [!code-cpp[NVC_ATL_COM#6](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_2.cpp)]

1. Dodaj metodę trzeci `GoToURL`, interfejsu, który nie kończy się w interfejsie "użytkownika". Zaimplementować tę metodę, wywołując [IWebBrowser2::Navigate](/previous-versions//aa752133\(v=vs.85\)), wykonując następujące czynności:

   [!code-cpp[NVC_ATL_COM#7](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_3.cpp)]

   Możesz użyć `IWebBrowser2` metody ponieważ ATL dostarcza wskaźnik do interfejsu dla Ciebie w pliku .h.

Następnie można zmodyfikować zasobu HTML do wywołania metody, który został utworzony. Zostaną dodane trzy przyciski wywoływanie tych metod.

## <a name="to-modify-the-html-resource"></a>Aby zmodyfikować zasób HTML

1. W **Eksploratora rozwiązań**, kliknij dwukrotnie plik htm, aby wyświetlić zasobu HTML.

   Sprawdź kod HTML, szczególnie wywołania zewnętrznego metody wysyłania Windows. Kod HTML wywołuje projektu `OnClick` metody i parametrów wskazują treści formantu (`theBody`), a kolor, aby przypisać ("`red`"). Tekst następujący po wywołaniu metody jest etykietę, która pojawia się na przycisku.

1. Dodaj kolejną `OnClick` metodę, Zmień kolor. Na przykład:

    ```html
    <br>
    <br>
    <BUTTON onclick='window.external.OnClick(theBody, "white");'>Refresh</BUTTON>
    ```

   Ta metoda utworzy przycisku, **Odśwież**, czy użytkownik może kliknąć do zwrócenia kontrolki w oryginalnej, białe tło.

1. Dodaj wywołanie do `HelloHTML` metody tworzenia. Na przykład:

    ```html
    <br>
    <br>
    <BUTTON onclick='window.external.HelloHTML();'>HelloHTML</BUTTON>
    ```

   Ta metoda utworzy przycisku, **HelloHTML**, który użytkownik może kliknąć, aby wyświetlić `HelloHTML` okno komunikatu.

Teraz możesz tworzyć i [testowanie zmodyfikowanej kontrolki DHTML](../atl/testing-the-modified-atl-dhtml-control.md).

## <a name="see-also"></a>Zobacz także

[Obsługa kontrolki DHTML](../atl/atl-support-for-dhtml-controls.md)
