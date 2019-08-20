---
title: Dodawanie kontrolki (ALT — Samouczek, część 2)
ms.custom: get-started-article
ms.date: 08/19/2019
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
ms.openlocfilehash: b7952f42b24c4211a2c44ea71fd17e4f65c3421a
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630709"
---
# <a name="adding-a-control-atl-tutorial-part-2"></a>Dodawanie kontrolki (ALT — Samouczek, część 2)

W tym kroku dodasz formant do projektu, skompilujesz go i przetestujesz go na stronie sieci Web.

## <a name="procedures"></a>Procedury

### <a name="to-add-an-object-to-an-atl-project"></a>Aby dodać obiekt do projektu ATL

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem `Polygon` myszy projekt.

1. Wskaż polecenie **Dodaj** w menu skrótów, a następnie kliknij pozycję **nowy element** w podmenu.

    **Dodaj nowy element** pojawi się okno dialogowe. Różne kategorie obiektów są wymienione w strukturze drzewa po lewej stronie.

1. Kliknij folder **ATL** .

1. Z listy szablonów po prawej stronie wybierz pozycję **formant ATL**. Kliknij przycisk **Dodaj**. Zostanie otwarty Kreator **kontrolki ATL** i można skonfigurować kontrolkę.

1. Wpisz `PolyCtl` krótką nazwę i pamiętaj, że inne pola są automatycznie uzupełniane. Nie klikaj jeszcze przycisku **Zakończ** , ponieważ musisz wprowadzić więcej zmian.

Strona **nazw** kreatora **kontrolki ATL** zawiera następujące pola:

|Pole|Spis treści|
|-----------|--------------|
|**Krótka nazwa**|Wprowadzona nazwa formantu.|
|**Class**|Nazwa C++ klasy utworzona w celu zaimplementowania formantu.|
|**plik h**|Plik utworzony w celu zawiera definicję C++ klasy.|
|**plik. cpp**|Plik utworzony, aby zawierać implementację C++ klasy.|
|**CoClass**|Nazwa klasy składnika dla tej kontrolki.|
|**Interface**|Nazwa interfejsu, w którym formant będzie implementował swoje niestandardowe metody i właściwości.|
|**Typ**|Opis formantu.|
|**ProgID**|Nazwa możliwa do odczytu, która może służyć do wyszukiwania identyfikatora CLSID formantu.|

Kilka dodatkowych ustawień należy zmienić w kreatorze **kontrolki ATL** .

### <a name="to-enable-support-for-rich-error-information-and-connection-points"></a>Aby włączyć obsługę zaawansowanych informacji o błędzie i punktów połączenia

1. Kliknij przycisk **Opcje** , aby otworzyć stronę **Opcje** .

1. Zaznacz pole wyboru **punkty połączenia** . Ta opcja tworzy obsługę interfejsu wychodzącego w pliku IDL.

Możesz również dodać interfejsy, aby zwiększyć funkcjonalność formantu.

### <a name="to-extend-the-controls-functionality"></a>Aby zwiększyć funkcjonalność formantu

1. Kliknij pozycję **interfejsy** , aby otworzyć stronę **interfejsy** .

1. Wybierz `IProvideClassInfo2` i kliknij strzałkę w **górę** , aby przenieść ją na **obsługiwaną** listę.

1. Wybierz `ISpecifyPropertyPages` i kliknij strzałkę w **górę** , aby przenieść ją na **obsługiwaną** listę.

Możesz również wprowadzić kontrolkę do *wstawienia*, co oznacza, że jest ona osadzana w aplikacjach, które obsługują obiekty osadzone, takie jak Excel lub Word.

### <a name="to-make-the-control-insertable"></a>Aby można było wstawić kontrolkę

1. Kliknij **wygląd** , aby otworzyć stronę **wygląd** .

1. Zaznacz pole wyboru **Wstaw** .

Wielokąt wyświetlany przez obiekt będzie miał pełny kolor wypełnienia, więc musisz dodać `Fill Color` Właściwość giełdową.

### <a name="to-add-a-fill-color-stock-property-and-create-the-control"></a>Aby dodać właściwość kolor wypełnienia i utworzyć kontrolkę

1. Kliknij pozycję **Właściwości** podstawowe, aby otworzyć stronę **Właściwości giełdowe** .

1. Wobszarze nieobsługiwane przewiń w dół listę możliwych właściwości. Wybierz `Fill Color` i kliknij strzałkę w **górę** , aby przenieść ją na **obsługiwaną** listę.

1. Wybierz **Zakończ**.

Po utworzeniu kontrolki przez kreatora jest wykonywana kilka zmian kodu i plików. Tworzone są następujące pliki:

|Plik|Opis|
|----------|-----------------|
|PolyCtl.h|Zawiera większość implementacji `CPolyCtl` C++ klasy.|
|PolyCtl.cpp|Zawiera pozostałe części `CPolyCtl`.|
|PolyCtl.rgs|Plik tekstowy zawierający skrypt rejestru używany do rejestrowania formantu.|
|PolyCtl.htm|Strona sieci Web zawierająca odwołanie do nowo utworzonej kontrolki.|

Kreator wprowadza również następujące zmiany kodu:

- `#include` Dodaje instrukcję do prekompilowanych plików nagłówkowych, aby uwzględnić pliki ATL niezbędne do obsługi kontrolek.

- Zmienia wielokąt. idl, aby dołączyć szczegóły nowej kontrolki.

- Dodaje nową kontrolkę do mapy obiektów w wielokąta. cpp.

Teraz można skompilować formant, aby zobaczyć go w działaniu.

## <a name="building-and-testing-the-control"></a>Kompilowanie i testowanie kontrolki

### <a name="to-build-and-test-the-control"></a>Aby skompilować i przetestować kontrolkę

1. W menu **kompilacja** kliknij pozycję **Kompiluj Wielokąt**.

    Po zakończeniu tworzenia kontrolki kliknij prawym przyciskiem myszy PolyCtl. htm w **Eksplorator rozwiązań** a następnie wybierz pozycję **Wyświetl w przeglądarce**. Zostanie wyświetlona strona sieci Web HTML zawierająca formant. Powinna zostać wyświetlona strona z tytułem "Strona testowa ATL 8,0 dla obiektu PolyCtl" i kontrolka PolyCtl tekst.

> [!NOTE]
> Jeśli formant nie jest widoczny, należy pamiętać, że niektóre przeglądarki wymagają dopasowania ustawień do uruchamiania formantów ActiveX. Zapoznaj się z dokumentacją przeglądarki, aby włączyć kontrolki ActiveX.

> [!NOTE]
> Po ukończeniu tego samouczka, jeśli zostanie wyświetlony komunikat o błędzie informujący o tym, że nie można utworzyć pliku DLL, zamknij plik PolyCtl. htm i kontener testów kontrolki ActiveX i ponownie skompiluj rozwiązanie. Jeśli nadal nie można utworzyć biblioteki DLL, uruchom ponownie komputer lub Wyloguj się, jeśli używasz usług terminalowych.

Następnie dodasz do formantu właściwość niestandardową.

[Wróć do kroku 1](../atl/creating-the-project-atl-tutorial-part-1.md) &#124; [Do kroku 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)

## <a name="see-also"></a>Zobacz także

[Samouczek](../atl/active-template-library-atl-tutorial.md)
