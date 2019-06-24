---
title: Dodawanie kontrolki (ALT — Samouczek, część 2)
ms.custom: get-started-article
ms.date: 09/26/2018
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
ms.openlocfilehash: 53f38d63a44328bf014f04635a24989a875ddf1e
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344326"
---
# <a name="adding-a-control-atl-tutorial-part-2"></a>Dodawanie kontrolki (ALT — Samouczek, część 2)

W tym kroku Dodaj formant do projektu, ją skompilować i przetestować go na stronie sieci Web.

## <a name="procedures"></a>Procedury

### <a name="to-add-an-object-to-an-atl-project"></a>Aby dodać obiekt do projektu ATL

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `Polygon` projektu.

1. Wskaż **Dodaj** w menu skrótów, a następnie kliknij przycisk **nowy element** w podmenu.

    **Dodaj nowy element** pojawi się okno dialogowe. Inne kategorie obiektów są wymienione w strukturze drzewa po lewej stronie.

1. Kliknij przycisk **ATL** folderu.

1. Na liście szablonów po prawej stronie zaznacz **kontrolka ATL**. Kliknij przycisk **Dodaj**. **Kontrolka ATL** zostanie otwarty Kreator i sterowanie można skonfigurować.

1. Typ `PolyCtl` jako krótka nazwa i zwróć uwagę, że inne pola są automatycznie uzupełniane. Nie klikaj pozycji **Zakończ** jeszcze, ponieważ należy wprowadzić pewne zmiany więcej.

**Kontrolka ATL** kreatora **nazwy** strona zawiera następujące pola:

|Pole|Spis treści|
|-----------|--------------|
|**Krótka nazwa**|Nazwa wprowadzona dla formantu.|
|**Class**|Nazwa klasy języka C++ utworzona w celu wdrożenia kontroli.|
|**plik .h**|Plik utworzony, aby zawierać definicję klasy C++.|
|**Plik CPP**|Plik utworzony, aby zawierać wdrożenie klasy C++.|
|**CoClass**|Nazwa klasy składnika dla tego formantu.|
|**Interface**|Nazwa interfejsu, na którym formant będzie implementował swoje niestandardowe metody i właściwości.|
|**Typ**|Opis formantu.|
|**ProgID**|Czytelna nazwa, która może służyć do sprawdzania CLSID formantu.|

Znajdziesz kilka dodatkowych ustawień należy zmienić w **kontrolka ATL** kreatora.

### <a name="to-enable-support-for-rich-error-information-and-connection-points"></a>Aby włączyć obsługę szczegółowych informacji o błędach i połączenie punktów

1. Kliknij przycisk **opcje** otworzyć **opcje** strony.

1. Wybierz **punkty połączenia** pole wyboru. Ta opcja powoduje utworzenie obsługi interfejsu wychodzącego w pliku IDL.

Można również dodać interfejsy, aby rozszerzyć funkcjonalność formantu.

### <a name="to-extend-the-controls-functionality"></a>Aby rozszerzyć funkcjonalność formantu

1. Kliknij przycisk **interfejsów** otworzyć **interfejsów** strony.

1. Wybierz `IProvideClassInfo2` i kliknij przycisk **się** strzałkę, aby przenieść go do **obsługiwane** listy.

1. Wybierz `ISpecifyPropertyPages` i kliknij przycisk **się** strzałkę, aby przenieść go do **obsługiwane** listy.

Można również ustawić jako formant *wstawialny*, co oznacza, że jest możliwego do osadzenia w aplikacji, które obsługują obiekty osadzone, takie jak Excel lub Word.

### <a name="to-make-the-control-insertable"></a>Aby umożliwić wstawianie formantu

1. Kliknij przycisk **wygląd** otworzyć **wygląd** strony.

1. Wybierz **wstawialny** pole wyboru.

Wielokąt wyświetlany przez obiekt będzie miał kolor wypełnienia kryjącego, więc trzeba dodać `Fill Color` właściwość magazynu.

### <a name="to-add-a-fill-color-stock-property-and-create-the-control"></a>Aby dodać właściwość podstawowy kolor wypełnienia i utworzyć formant

1. Kliknij przycisk **właściwości podstawowe** otworzyć **właściwości podstawowe** strony.

1. W obszarze **nieobsługiwane**, przewiń w dół listę możliwych właściwości stosu. Wybierz `Fill Color` i kliknij przycisk **się** strzałkę, aby przenieść go do **obsługiwane** listy.

1. Wybierz **Zakończ**.

Jak Kreator utworzy formant, wystąpić kilka zmian kodu i uzupełnień pliku. Są tworzone następujące pliki:

|Plik|Opis|
|----------|-----------------|
|PolyCtl.h|Zawiera większość implementacji klasy języka C++ `CPolyCtl`.|
|PolyCtl.cpp|Zawiera pozostałe części `CPolyCtl`.|
|PolyCtl.rgs|Plik tekstowy zawierający skrypt rejestru używany do rejestrowania formantu.|
|PolyCtl.htm|Strona sieci Web zawierająca odwołanie do nowo utworzonego formantu.|

Kreator przeprowadza także następujących zmian w kodzie:

- Dodaje `#include` instrukcję do plików stdafx.h i stdafx.cpp, aby uwzględnić ATL pliki niezbędne do obsługi formantów.

- Zmienia Polygon.idl, aby dołączyć szczegóły nowego formantu.

- Dodaje nowy formant do mapy obiektu w Polygon.cpp.

Teraz można skompilować formant aby zobaczyć go w działaniu.

## <a name="building-and-testing-the-control"></a>Tworzenie i testowanie formantu

### <a name="to-build-and-test-the-control"></a>Aby skompilować i przetestować formant

1. Na **kompilacji** menu, kliknij przycisk **Kompiluj Wielokąt**.

    Po zakończeniu kompilowania formantu, kliknij prawym przyciskiem myszy plik PolyCtl.htm w **Eksploratora rozwiązań** i wybierz **Pokaż w przeglądarce**. Zostanie wyświetlona strona HTML sieci Web zawierająca formant. Powinieneś widzieć stronę o tytule "strona testowa 8.0 ATL dla obiektu PolyCtl" i kontroli nad tekstem PolyCtl.

> [!NOTE]
> Jeśli formant nie jest widoczne, wiadomo, że niektóre przeglądarki wymagać dostosowania ustawień, aby uruchomić formanty ActiveX. Zajrzyj do dokumentacji w przeglądarce na temat włączania formantów ActiveX.

> [!NOTE]
> Po ukończeniu tego samouczka, jeśli zostanie wyświetlony komunikat o błędzie, że nie można utworzyć pliku DLL, zamknij plik PolyCtl.htm i kontener badania kontrolnego ActiveX i ponownie skompiluj rozwiązanie. Jeśli nadal nie można utworzyć biblioteki DLL, uruchom ponownie komputer lub się wylogować, jeśli używasz usług terminalowych.

Następnie dodasz właściwość niestandardową do formantu.

[Wróć do kroku 1](../atl/creating-the-project-atl-tutorial-part-1.md) &#124; [do kroku 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)

## <a name="see-also"></a>Zobacz także

[Samouczek](../atl/active-template-library-atl-tutorial.md)
