---
title: Dodawanie kontrolki (ALT — samouczek, część 2) | Dokumentacja firmy Microsoft
ms.custom: get-started-article
ms.date: 06/18/2018
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac4f3e1460dc4601e15065cb7b968153bd928c87
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762863"
---
# <a name="adding-a-control-atl-tutorial-part-2"></a>Dodawanie kontrolki (ALT — Samouczek, część 2)

W tym kroku zostanie dodać formant do projektu, skompiluj go i je przetestować na stronie sieci Web.

## <a name="procedures"></a>Procedury

#### <a name="to-add-an-object-to-an-atl-project"></a>Aby dodać obiekt do projektu ATL

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt wielokąt.

2. Wskaż **Dodaj** w menu skrótów, a następnie kliknij przycisk **nowy element** w podmenu.

     **Dodaj nowy element** pojawi się okno dialogowe. Inne kategorie obiektów są wymienione w strukturze drzewa po lewej stronie.

3. Kliknij przycisk **ATL** folderu.

4. Na liście szablonów po prawej stronie zaznacz **kontrolka ATL**. Kliknij przycisk **Dodaj**. Zostanie otwarty Kreator formantu biblioteki ATL i sterowanie można skonfigurować.

5. Typ `PolyCtl` jako krótka nazwa i zwróć uwagę, że inne pola są automatycznie uzupełniane. Nie klikaj **Zakończ** jeszcze, ponieważ trzeba wprowadzić pewne zmiany.

Kreator kontrolki ATL **nazwy** strona zawiera następujące pola:

|Pole|Spis treści|
|-----------|--------------|
|**Krótka nazwa**|Nazwa wprowadzona dla formantu.|
|**Class**|Nazwa klasy języka C++ utworzona w celu wdrożenia kontroli.|
|**plik .h**|Plik utworzony, aby zawierać definicję klasy C++.|
|**Plik CPP**|Plik utworzony, aby zawierać wdrożenie klasy C++.|
|**Klasa coClass**|Nazwa klasy składnika dla tego formantu.|
|**Interface**|Nazwa interfejsu, na którym formant będzie implementował swoje niestandardowe metody i właściwości.|
|**Typ**|Opis formantu.|
|**Identyfikator programu**|Czytelna nazwa, która może służyć do sprawdzania CLSID formantu.|

Musisz wprowadzić kilka dodatkowych ustawień w Kreatorze formantu ATL.

#### <a name="to-enable-support-for-rich-error-information-and-connection-points"></a>Aby włączyć obsługę szczegółowych informacji o błędach i połączenie punktów

1. Kliknij przycisk **opcje** otworzyć **opcje** strony.

2. Wybierz **punkty połączenia** pole wyboru. Spowoduje to utworzenie obsługi interfejsu wychodzącego w pliku IDL.

Można również ustawić formant będzie wstawialny, co oznacza, że mogą być osadzone w aplikacjach, które obsługują obiekty osadzone, takie jak Excel lub Word.

#### <a name="to-make-the-control-insertable"></a>Aby umożliwić wstawianie formantu

1. Kliknij przycisk **wygląd** otworzyć **wygląd** strony.

2. Wybierz **wstawialny** pole wyboru.

Wielokąt wyświetlany przez obiekt będzie miał kolor wypełnienia kryjącego, więc trzeba dodać `Fill Color` właściwość magazynu.

#### <a name="to-add-a-fill-color-stock-property-and-create-the-control"></a>Aby dodać właściwość podstawowy kolor wypełnienia i utworzyć formant

1. Kliknij przycisk **właściwości podstawowe** otworzyć **właściwości podstawowe** strony.

2. W obszarze **nieobsługiwane**, przewiń w dół listę możliwych właściwości stosu. Kliknij dwukrotnie `Fill Color` przenieść je do **obsługiwane** listy.

3. Na tym kończy się opcje dla formantu. Kliknij przycisk **Zakończ**.

Gdy Kreator utworzył już formant, kilka zmian kodu i uzupełnień pliku wystąpił. Utworzone zostały następujące pliki:

|Plik|Opis|
|----------|-----------------|
|PolyCtl.h|Zawiera większość implementacji klasy języka C++ `CPolyCtl`.|
|PolyCtl.cpp|Zawiera pozostałe części `CPolyCtl`.|
|PolyCtl.rgs|Plik tekstowy zawierający skrypt rejestru używany do rejestrowania formantu.|
|PolyCtl.htm|Strona sieci Web zawierająca odwołanie do nowo utworzonego formantu.|

Kreator wykonał również następujące zmiany kodu:

- Dodano `#include` instrukcję do plików stdafx.h i stdafx.cpp, aby uwzględnić ATL pliki niezbędne do obsługi formantów.

- Zmieniono Polygon.idl, aby dołączyć szczegóły nowego formantu.

- Dodany nowy formant do mapy obiektu w Polygon.cpp.

Teraz można skompilować formant aby zobaczyć go w działaniu.

## <a name="building-and-testing-the-control"></a>Tworzenie i testowanie formantu

#### <a name="to-build-and-test-the-control"></a>Aby skompilować i przetestować formant

1. Na **kompilacji** menu, kliknij przycisk **Kompiluj Wielokąt**.

     Po zakończeniu kompilowania formantu, kliknij prawym przyciskiem myszy plik PolyCtl.htm w **Eksploratora rozwiązań** i wybierz **Pokaż w przeglądarce**. Pojawi się Strona HTML sieci Web zawierająca formant. Powinieneś widzieć stronę o tytule "Strona testowa 8.0 ATL dla obiektu PolyCtl" i tekst **PolyCtl**. To jest Twój formant.

> [!NOTE]
>  Po ukończeniu tego samouczka, jeśli zostanie wyświetlony komunikat o błędzie, w których nie można utworzyć pliku DLL, zamknij plik PolyCtl.htm i kontener badania kontrolnego ActiveX i ponownie skompiluj rozwiązanie. Jeśli nadal nie można utworzyć biblioteki DLL, uruchom ponownie komputer lub wyloguj (Jeśli używasz usług terminalowych).

Następnie dodasz właściwość niestandardową do formantu.

[Wróć do kroku 1](../atl/creating-the-project-atl-tutorial-part-1.md) &#124; [do kroku 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)

## <a name="see-also"></a>Zobacz też

[Samouczek](../atl/active-template-library-atl-tutorial.md)

