---
title: Wywoływanie kodu w języku C++ z elementu DHTML
ms.date: 11/04/2016
helpviewer_keywords:
- DHTML, calling C++ code from
ms.assetid: 37329acd-4c22-40ca-a85a-b7480748f75f
ms.openlocfilehash: 0fa4f51f4488be61edb0f01d9fddc956cd7a45b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555197"
---
# <a name="calling-c-code-from-dhtml"></a>Wywoływanie kodu w języku C++ z elementu DHTML

Kontrolki DHTML mogą być hostowane w kontenerze, np. kontenerze testów lub programu Internet Explorer. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](../mfc/testing-properties-and-events-with-test-container.md) informacji na temat dostępu do kontenera testu.

Kontrolki do hostowania kontenerów komunikuje się za pomocą kontrolki przy użyciu interfejsów normalnej kontroli. DHTML wykorzystuje interfejs ekspedycji, który kończy się ciągiem "UI", do komunikowania się z kodu C++ i zasobu HTML. W [modyfikowanie kontrolki DHTML ATL](../atl/modifying-the-atl-dhtml-control.md), ćwiczenie dodawanie metod, które ma zostać wywołana przez te różne interfejsy.

Aby zobaczyć przykład wywołania kodu w języku C++ z elementu DHTML, [tworzenie kontrolki DHTML](../atl/creating-an-atl-dhtml-control.md) za pomocą Kreatora formantu biblioteki ATL i sprawdź kod w pliku nagłówkowym, jak i w pliku HTML.

## <a name="declaring-webbrowser-methods-in-the-header-file"></a>Deklarowanie metody WebBrowser w pliku nagłówkowym

Aby wywołać metody C++ z poziomu interfejsu użytkownika DHTML, należy dodać metody do kontroli nad interfejs użytkownika. Na przykład plik nagłówka, utworzony przez Kreator kontrolki ATL zawiera metodę C++ `OnClick`, który jest składową interfejsu interfejsu użytkownika formantu generowane przez kreatora.

Sprawdź `OnClick` w plik h kontrolki:

[!code-cpp[NVC_ATL_COM#4](../atl/codesnippet/cpp/calling-cpp-code-from-dhtml_1.h)]

Pierwszy parametr *pdispBody*, jest wskaźnikiem do obiektu treści interfejs ekspedycji. Drugi parametr *varColor*, identyfikuje kolor do zastosowania do formantu.

## <a name="calling-c-code-in-the-html-file"></a>Wywoływanie kodu C++ w pliku HTML

Po zadeklarowaniu metody WebBrowser w pliku nagłówkowym, można wywoływać metod z pliku HTML. W pliku HTML powiadomienie, że Kreator kontrolki ATL wstawia trzy metody wysyłania Windows: trzy `OnClick` metody, które wysyłają komunikaty, aby zmienić kolor tła kontrolki.

Sprawdź jedną z metod w pliku HTML:

`<BUTTON onclick='window.external.OnClick(theBody, "red");'>Red</BUTTON>`

W kodzie HTML powyżej metody zewnętrznej okna `OnClick`, jest wywoływana jako części tagu przycisku. Metoda ma dwa parametry: `theBody`, które odwołują się do treści dokumentu HTML i `"red"`, co oznacza, że kolor tła kontrolki zmieni się na czerwony po kliknięciu przycisku. `Red` Po tagu jest etykieta przycisku.

Zobacz [modyfikowanie kontrolki DHTML ATL](../atl/modifying-the-atl-dhtml-control.md) uzyskać więcej informacji o podanie własnych metod. Zobacz [identyfikowanie elementów projektu kontrolki DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md) uzyskać więcej informacji o pliku HTML.

## <a name="see-also"></a>Zobacz też

[Obsługa kontrolki DHTML](../atl/atl-support-for-dhtml-controls.md)

