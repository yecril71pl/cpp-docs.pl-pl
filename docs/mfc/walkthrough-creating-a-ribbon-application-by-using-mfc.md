---
title: 'Przewodnik: Tworzenie aplikacji wstążki za pomocą MFC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ribbon application, creating (MFC)
- creating a ribbon aplication (MFC)
ms.assetid: e61393e2-1d6b-4594-a7ce-157d3d1b0d9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8bb7039481469bbd6c307ab1ec88b508ff089733
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169583"
---
# <a name="walkthrough-creating-a-ribbon-application-by-using-mfc"></a>Wskazówki: tworzenie aplikacji wstążki za pomocą MFC

Ten poradnik pokazuje jak używać **Kreator aplikacji MFC** do tworzenia aplikacji, która domyślnie zawiera Wstążkę. Powstałą Wstążkę, dodając **niestandardowe** kategoria wstążki, który ma **ulubione** wstążki, panelu, a następnie dodając kilka często używanych poleceń do panelu.

## <a name="prerequisites"></a>Wymagania wstępne

Instruktaż ten zakłada, że zostało ustawione Visual Studio ma używać **ogólnych ustawieniach projektowych**. Jeśli są używane inne ustawienia, niektóre elementy interfejsu użytkownika, do których odwołują się poniższe instrukcje, mogą nie być wyświetlane.

### <a name="to-create-an-mfc-application-that-has-a-ribbon"></a>Tworzenie aplikacji MFC zawierającej wstążkę

1. Użyj **Kreator aplikacji MFC** do tworzenia aplikacji MFC zawierającej Wstążkę. Aby uruchomić kreatora w **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.

1. W **nowy projekt** okna dialogowego rozwiń **Visual C++** węźle **zainstalowane szablony**, wybierz opcję **MFC**, a następnie wybierz pozycję  **Aplikacja MFC**. Wpisz nazwę projektu, na przykład *MFCRibbonApp*, a następnie kliknij przycisk **OK**.

1. Ustaw następujące opcje **Kreator aplikacji MFC**:

    1. W **typ aplikacji** sekcji w obszarze **styl wizualny i kolory**, wybierz opcję **Office 2007 (motyw niebieski)**. 

    1. W **Obsługa dokumentów złożonych** sekcji, upewnij się, że **Brak** jest zaznaczone.

    1. W **właściwości szablonu dokumentu** sekcji w **rozszerzenie pliku** wpisz rozszerzenie nazwy pliku dla dokumentów, które tworzy tę aplikację, na przykład *mfcrbnapp*.

    1. W **obsługi bazy danych** sekcji, upewnij się, że **Brak** jest zaznaczone.

    1. W **funkcje interfejsu użytkownika** sekcji, upewnij się, że **Użyj wstążki** jest zaznaczone. 

    1. Domyślnie **Kreator aplikacji MFC** dodaje obsługę kilku okienek dokowania. Ponieważ ten instruktaż jest poświęcony wyłącznie wstążce, można usunąć te opcje z aplikacji. W **funkcje zaawansowane** wyczyść wszystkie opcje.

1. Kliknij przycisk **Zakończ** do utworzenia aplikacji MFC.

1. Aby sprawdzić, czy aplikacja została pomyślnie utworzona, należy ją skompilować i uruchomić. Aby skompilować aplikację, na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Jeśli aplikacja zostanie pomyślnie skompilowana, uruchom ją, klikając pozycję **Rozpocznij debugowanie** na **debugowania** menu.

    Kreator automatycznie utworzy Wstążkę z jedną kategorią o nazwie **Home**. Wstążka zawiera trzy panele wstążki, które noszą nazwy **Schowka**, **widoku**, i **okna**.

### <a name="to-add-a-category-and-panel-to-the-ribbon"></a>Dodawanie kategorii i panelu do wstążki

1. Aby otworzyć zasób wstążki utworzony przez kreatora, na **widoku** menu wskaż **Windows inne** a następnie kliknij przycisk **widok zasobów**. W **widok zasobów**, kliknij przycisk **wstążki** a następnie kliknij dwukrotnie **IDR_RIBBON**.

1. Najpierw Dodaj kategorię niestandardową do wstążki, klikając dwukrotnie **kategorii** w **przybornika**.

    Kategoria, który ma podpis **Category1** zostanie utworzony. Domyślnie kategoria zawiera jeden panel.

    Kliknij prawym przyciskiem myszy **Category1** a następnie kliknij przycisk **właściwości**. W **właściwości** oknie zmiany **podpis** do *niestandardowe*.

    **Duże obrazy** i **małe obrazy** właściwości określają mapy bitowe, które są używane jako ikony elementów wstążki w tej kategorii. Ponieważ tworzenie niestandardowych map bitowych wykracza poza zakres tego instruktażu, należy po prostu użyć map bitowych utworzonych przez kreatora. Małe mapy bitowe mają rozmiar 16 x 16 pikseli. Do małych obrazów należy stosować mapy bitowe, które są dostępne dla `IDB_FILESMALL` identyfikator zasobu. Duże mapy bitowe mają rozmiar 32 x 32 piksele. Do dużych obrazów należy stosować mapy bitowe, które są dostępne dla `IDB_FILELARGE` identyfikator zasobu.

    > [!NOTE]
    > Na ekranach o dużej liczbie punktów na cal (HDPI) automatycznie są używane wersje HDPI obrazów.

1. Następnie dostosuj panel. Panele służą do grupowania elementów, które są ze sobą logicznie powiązane. Na przykład na **Home** tej aplikacji na karcie **Wytnij**, **kopiowania**, i **Wklej** polecenia znajdują się na  **Schowek** panelu. Aby dostosować panel, kliknij prawym przyciskiem myszy **Panel1** a następnie kliknij przycisk **właściwości**. W **właściwości** oknie zmiany **podpis** do *ulubione*.

    Można określić **indeks obrazu** panelu. Liczba ta określa ikonę, która jest wyświetlana po dodaniu panelu wstążki do **paska narzędzi szybkiego dostępu**. Ikona nie jest wyświetlana na samym panelu wstążki.

1. Aby sprawdzić, czy kategoria i panel wstążki zostały utworzone pomyślnie, wyświetl podgląd formantu wstążki. Na **pasek narzędzi edytora wstążki**, kliknij przycisk **Testuj Wstążkę** przycisku. A **niestandardowe** kartę i **ulubione** panelu powinien być wyświetlany na Wstążce.

### <a name="to-add-elements-to-the-ribbon-panels"></a>Dodawanie elementów do paneli wstążki

1. Aby dodać elementy do panelu, który został utworzony w poprzedniej procedurze, przeciągnij formanty z **edytora wstążki** części **przybornika** do panelu w widoku Projekt.

1. Najpierw dodaj **drukowania** przycisku. **Drukowania** przycisk będzie miał podmenu zawierające **szybkie drukowanie** polecenia, które inicjuje drukowanie przy użyciu domyślnej drukarki. Oba te polecenia są już zdefiniowane dla tej aplikacji. Znajdują się w menu aplikacji.

    Aby utworzyć **drukowania** przycisk, przeciągnij narzędzie przycisk na panel.

    W **właściwości** oknie zmiany **identyfikator** właściwości **ID_FILE_PRINT**, która już powinna być zdefiniowana. Zmiana **podpis** do *drukowania*. Zmiana **indeks obrazu** do *4*.

    Aby utworzyć **szybkie drukowanie** przycisk, kliknij kolumnę wartości właściwości **elementów Menu**, a następnie kliknij przycisk wielokropka (**...** ). W **Edytor elementów**, kliknij przycisk, który nie ma etykiety **Dodaj** przycisk, aby utworzyć element menu. W **właściwości** oknie zmiany **podpis** do *szybkie drukowanie*, **identyfikator** do *ID_FILE_PRINT_DIRECT*, i **obraz** do *5*. Właściwość obrazu Określa **szybkie drukowanie** ikonę `IDB_FILESMALL` mapy bitowej zasobów.

1. Aby sprawdzić, czy przyciski zostały dodane do panelu wstążki, skompiluj aplikację i ją uruchom. Aby skompilować aplikację, na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Jeśli aplikacja zostanie pomyślnie skompilowana, uruchom ją, klikając pozycję **Rozpocznij debugowanie** na **debugowania** menu. **Drukowania** przycisku oraz pole kombi na **ulubione** panelu **niestandardowe** karty na Wstążce powinna być wyświetlana.

## <a name="next-steps"></a>Następne kroki

[Instrukcje: dostosowywanie paska narzędzi Szybki dostęp](../mfc/how-to-customize-the-quick-access-toolbar.md)

[Instrukcje: dostosowywanie przycisku Aplikacja](../mfc/how-to-customize-the-application-button.md)

Aby uzyskać przykłady end-to-end, zobacz [przykłady (MFC Feature Pack)](../visual-cpp-samples.md).

## <a name="see-also"></a>Zobacz też

[Przewodniki](../mfc/walkthroughs-mfc.md)<br/>
[Przykłady (MFC Feature Pack)](../visual-cpp-samples.md)
