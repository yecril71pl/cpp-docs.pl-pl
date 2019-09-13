---
title: 'Przewodnik: Tworzenie aplikacji wstążki za pomocą MFC'
ms.date: 09/09/2019
helpviewer_keywords:
- ribbon application, creating (MFC)
- creating a ribbon aplication (MFC)
ms.assetid: e61393e2-1d6b-4594-a7ce-157d3d1b0d9f
ms.openlocfilehash: 41084a78287521610ba400deab32d1052c9217c1
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907390"
---
# <a name="walkthrough-creating-a-ribbon-application-by-using-mfc"></a>Przewodnik: Tworzenie aplikacji wstążki za pomocą MFC

W tym instruktażu pokazano, jak za pomocą **Kreatora aplikacji MFC** utworzyć aplikację, która domyślnie ma Wstążkę. Następnie można rozwinąć Wstążkę, dodając **niestandardową** kategorię wstążki, która ma panel wstążki **ulubionych** , a następnie dodając kilka często używanych poleceń do panelu.

## <a name="prerequisites"></a>Wymagania wstępne

W tym przewodniku przyjęto założenie, że ustawiono program Visual Studio do używania **ogólnych ustawień deweloperskich**. Jeśli używasz różnych ustawień, niektóre elementy interfejsu użytkownika, do których istnieją odwołania w poniższych instrukcjach, mogą nie być wyświetlane.

### <a name="to-create-an-mfc-application-that-has-a-ribbon"></a>Tworzenie aplikacji MFC zawierającej wstążkę

1. Użyj **Kreatora aplikacji MFC** , aby utworzyć aplikację MFC, która ma Wstążkę. Zobacz [Przewodnik: Aby uzyskać instrukcje dotyczące sposobu otwierania](walkthrough-using-the-new-mfc-shell-controls.md) kreatora dla używanej wersji programu Visual Studio, użyj nowych formantów powłoki MFC.

1. W **Kreatorze aplikacji MFC**ustaw następujące opcje:

    1. W sekcji **Typ aplikacji** w obszarze **styl wizualny i kolory**wybierz pozycję **Office 2007 (motyw niebieski)** .

    1. Upewnij się, że w sekcji **Obsługa dokumentu złożonego** jest zaznaczona opcja **Brak** .

    1. W sekcji **Właściwości szablonu dokumentu** w polu **rozszerzenie pliku** wpisz rozszerzenie nazwy pliku dla dokumentów tworzonych przez tę aplikację, na przykład *mfcrbnapp*.

    1. W sekcji **Obsługa bazy danych** (tylko w programie Visual Studio 2015) Upewnij się, że **żadna opcja nie** jest zaznaczona.

    1. W sekcji **funkcje interfejsu użytkownika** upewnij się, że wybrano opcję **Użyj wstążki** .

    1. Domyślnie **Kreator aplikacji MFC** dodaje obsługę kilku okienek dokowania. Ponieważ ten instruktaż jest poświęcony wyłącznie wstążce, można usunąć te opcje z aplikacji. W sekcji **Zaawansowane funkcje** Wyczyść wszystkie opcje.

1. Kliknij przycisk **Zakończ** , aby utworzyć aplikację MFC.

1. Aby sprawdzić, czy aplikacja została pomyślnie utworzona, należy ją skompilować i uruchomić. Aby skompilować aplikację, w menu **kompilacja** kliknij polecenie **Kompiluj rozwiązanie**. Jeśli aplikacja zostanie pomyślnie skompilowana, uruchom ją, klikając polecenie **Rozpocznij debugowanie** w menu **debugowanie** .

    Kreator automatycznie utworzy Wstążkę z jedną kategorią wstążki o nazwie **Home**. Ta Wstążka zawiera trzy panele wstążki o nazwie **Clipboard**, **View**i **window**.

### <a name="to-add-a-category-and-panel-to-the-ribbon"></a>Dodawanie kategorii i panelu do wstążki

1. Aby otworzyć zasób wstążki utworzony przez kreatora, w menu **Widok** wskaż polecenie **inne okna** , a następnie kliknij przycisk **Widok zasobów**. W **Widok zasobów**kliknij pozycję **wstążka** , a następnie kliknij dwukrotnie pozycję **IDR_RIBBON**.

1. Najpierw Dodaj kategorię niestandardową do wstążki przez dwukrotne kliknięcie **kategorii** w **przyborniku**.

    Zostanie utworzona Kategoria z podpisem **Category1** . Domyślnie kategoria zawiera jeden panel.

    Kliknij prawym przyciskiem myszy pozycję **Category1** , a następnie kliknij pozycję **Właściwości**. W oknie **Właściwości** Zmień **napis** na *niestandardowy*.

    Właściwości **duże obrazy** i **małe obrazy** określają mapy bitowe, które są używane jako ikony dla elementów wstążki w tej kategorii. Ponieważ tworzenie niestandardowych map bitowych wykracza poza zakres tego instruktażu, należy po prostu użyć map bitowych utworzonych przez kreatora. Małe mapy bitowe mają rozmiar 16 x 16 pikseli. W przypadku małych obrazów Użyj map bitowych, do których uzyskuje się `IDB_FILESMALL` dostęp za pomocą identyfikatora zasobu. Duże mapy bitowe mają rozmiar 32 x 32 piksele. W przypadku dużych obrazów Użyj map bitowych, do których uzyskuje się `IDB_FILELARGE` dostęp za pomocą identyfikatora zasobu.

    > [!NOTE]
    > Na ekranach o dużej liczbie punktów na cal (HDPI) automatycznie są używane wersje HDPI obrazów.

1. Następnie dostosuj panel. Panele służą do grupowania elementów, które są ze sobą logicznie powiązane. Na przykład na karcie **Narzędzia główne** w tej aplikacji polecenia **wycinania**, **kopiowania**i **wklejania** są dostępne na panelu **schowka** . Aby dostosować panel, kliknij prawym przyciskiem myszy pozycję **element Panel1** , a następnie kliknij pozycję **Właściwości**. W oknie **Właściwości** Zmień **napis** na *Ulubione*.

    Możesz określić **indeks obrazu** dla panelu. Ta liczba określa ikonę wyświetlaną, gdy panel wstążki zostanie dodany do **paska narzędzi Szybki dostęp**. Ikona nie jest wyświetlana na panelu wstążki.

1. Aby sprawdzić, czy kategoria i panel wstążki zostały utworzone pomyślnie, wyświetl podgląd formantu wstążki. Na **pasku narzędzi edytora wstążki**kliknij przycisk **Testuj wstążkę** . Na Wstążce powinna zostać wyświetlona karta **niestandardowa** i panel **Ulubione** .

### <a name="to-add-elements-to-the-ribbon-panels"></a>Dodawanie elementów do paneli wstążki

1. Aby dodać elementy do panelu, który został utworzony w poprzedniej procedurze, przeciągnij kontrolki z sekcji **Edytor wstążki** w **przyborniku** do panelu w widoku projektu.

1. Najpierw Dodaj przycisk **Drukuj** . Przycisk **Drukuj** będzie miał podmenu zawierające polecenie **szybkie drukowanie** , które drukuje przy użyciu drukarki domyślnej. Oba te polecenia są już zdefiniowane dla tej aplikacji. Znajdują się one w menu aplikacji.

    Aby utworzyć przycisk **Drukuj** , przeciągnij narzędzie Button do panelu.

    W oknie **Właściwości** Zmień wartość właściwości **ID** na **ID_FILE_PRINT**, która powinna być już zdefiniowana. Zmień **podpis** , aby *drukować*. Zmień **indeks obrazu** na *4*.

    Aby utworzyć przycisk **szybkiego drukowania** , kliknij kolumnę wartość właściwości obok **pozycji menu elementy**, a następnie kliknij przycisk wielokropka ( **...** ). W **Edytorze elementów**kliknij przycisk **Dodaj** bez etykiety, aby utworzyć element menu. W oknie **Właściwości** Zmień **napis** na *szybkie drukowanie*, **Identyfikator** na *ID_FILE_PRINT_DIRECT*i **obraz** na *5*. Właściwość obrazu określa ikonę **szybkiego drukowania** w `IDB_FILESMALL` zasobie mapy bitowej.

1. Aby sprawdzić, czy przyciski zostały dodane do panelu wstążki, skompiluj aplikację i ją uruchom. Aby skompilować aplikację, w menu **kompilacja** kliknij polecenie **Kompiluj rozwiązanie**. Jeśli aplikacja zostanie pomyślnie skompilowana, uruchom aplikację, klikając polecenie **Rozpocznij debugowanie** w menu **debugowanie** . Na Wstążce powinna zostać wyświetlona przycisk **Drukuj** oraz pole kombi w panelu **Ulubione** .

## <a name="next-steps"></a>Następne kroki

[Instrukcje: dostosowywanie paska narzędzi Szybki dostęp](../mfc/how-to-customize-the-quick-access-toolbar.md)

[Instrukcje: dostosowywanie przycisku Aplikacja](../mfc/how-to-customize-the-application-button.md)

Aby zapoznać się z kompletnymi przykładami, zobacz [przykłady (pakiet MFC Feature Pack)](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Zobacz także

[Przewodniki](../mfc/walkthroughs-mfc.md)<br/>
[Przykłady (pakiet MFC Feature Pack)](../overview/visual-cpp-samples.md)
