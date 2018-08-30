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
ms.openlocfilehash: 495f5b415aac2a59eeae45720944a03251b0faa5
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210700"
---
# <a name="walkthrough-creating-a-ribbon-application-by-using-mfc"></a>Wskazówki: tworzenie aplikacji wstążki za pomocą MFC
Ten poradnik pokazuje jak używać **Kreator aplikacji MFC** do tworzenia aplikacji, która domyślnie zawiera Wstążkę. Powstałą Wstążkę, dodając **niestandardowe** kategoria wstążki, który ma **ulubione** wstążki, panelu, a następnie dodając kilka często używanych poleceń do panelu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Instruktaż ten zakłada, że zostało ustawione Visual Studio ma używać **ogólnych ustawieniach projektowych**. Jeśli są używane inne ustawienia, niektóre elementy interfejsu użytkownika, do których odwołują się poniższe instrukcje, mogą nie być wyświetlane. Aby dowiedzieć się, jak zmienić ustawienia, zobacz [jak: Reset Your Settings](https://msdn.microsoft.com/c95c51be-e609-4769-abba-65e6beedec76).  
  
### <a name="to-create-an-mfc-application-that-has-a-ribbon"></a>Tworzenie aplikacji MFC zawierającej wstążkę  
  
1.  Użyj **Kreator aplikacji MFC** do tworzenia aplikacji MFC zawierającej Wstążkę. Aby uruchomić kreatora w **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **Visual C++** węźle **zainstalowane szablony**, wybierz opcję **MFC**, a następnie wybierz pozycję  **Aplikacja MFC**. Wpisz nazwę projektu, na przykład *MFCRibbonApp*, a następnie kliknij przycisk **OK**.  
  
3.  Na pierwszej stronie **Kreator aplikacji MFC**, kliknij przycisk **dalej**.  
  
4.  Na **typ aplikacji** w obszarze **styl wizualny i kolory**, wybierz opcję **Office 2007 (motyw niebieski)**. Pozostałych ustawień nie zmieniaj. Kliknij przycisk **Dalej**.  
  
5.  Na **Obsługa dokumentów złożonych** strony, upewnij się, że **Brak** jest zaznaczone, a następnie kliknij przycisk **dalej**.  
  
6.  Na **właściwości szablonu dokumentu** stronie **rozszerzenie pliku** wpisz rozszerzenie nazwy pliku dla dokumentów, które tworzy tę aplikację, na przykład *mfcrbnapp*. Kliknij przycisk **Dalej**.  
  
7.  Na **obsługi bazy danych** strony, upewnij się, że **Brak** jest zaznaczone, a następnie kliknij przycisk **dalej**.  
  
8.  Na **funkcje interfejsu użytkownika** strony, upewnij się, że **Użyj wstążki** jest zaznaczone. Kliknij przycisk **Dalej**.  
  
9. Domyślnie **Kreator aplikacji MFC** dodaje obsługę kilku okienek dokowania. Ponieważ ten instruktaż jest poświęcony wyłącznie wstążce, można usunąć te opcje z aplikacji. Na **funkcje zaawansowane** strony, wyczyść wszystkie opcje. Kliknij przycisk **Dalej**.  
  
10. Na **wygenerowane klasy** kliknij **Zakończ** do utworzenia aplikacji MFC.  
  
11. Aby sprawdzić, czy aplikacja została pomyślnie utworzona, należy ją skompilować i uruchomić. Aby skompilować aplikację, na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Jeśli aplikacja zostanie pomyślnie skompilowana, uruchom ją, klikając pozycję **Rozpocznij debugowanie** na **debugowania** menu.  
  
     Kreator automatycznie utworzy Wstążkę z jedną kategorią o nazwie **Home**. Wstążka zawiera trzy panele wstążki, które noszą nazwy **Schowka**, **widoku**, i **okna**.  
  
### <a name="to-add-a-category-and-panel-to-the-ribbon"></a>Dodawanie kategorii i panelu do wstążki  
  
1.  Aby otworzyć zasób wstążki utworzony przez kreatora, na **widoku** menu wskaż **Windows inne** a następnie kliknij przycisk **widok zasobów**. W **widok zasobów**, kliknij przycisk **wstążki** a następnie kliknij dwukrotnie **IDR_RIBBON**.  
  
2.  Najpierw Dodaj kategorię niestandardową do wstążki, klikając dwukrotnie **kategorii** w **przybornika**.  
  
     Kategoria, który ma podpis **Category1** zostanie utworzony. Domyślnie kategoria zawiera jeden panel.  
  
     Kliknij prawym przyciskiem myszy **Category1** a następnie kliknij przycisk **właściwości**. W **właściwości** oknie zmiany **podpis** do *niestandardowe*.  
  
     **Duże obrazy** i **małe obrazy** właściwości określają mapy bitowe, które są używane jako ikony elementów wstążki w tej kategorii. Ponieważ tworzenie niestandardowych map bitowych wykracza poza zakres tego instruktażu, należy po prostu użyć map bitowych utworzonych przez kreatora. Małe mapy bitowe mają rozmiar 16 x 16 pikseli. Do małych obrazów należy stosować mapy bitowe wykorzystywane przez identyfikator zasobu IDB_FILESMALL. Duże mapy bitowe mają rozmiar 32 x 32 piksele. Do dużych obrazów należy stosować mapy bitowe używane przez identyfikator zasobu IDB_FILELARGE.  
  
    > [!NOTE]
    >  Na ekranach o dużej liczbie punktów na cal (HDPI) automatycznie są używane wersje HDPI obrazów.  
  
3.  Następnie dostosuj panel. Panele służą do grupowania elementów, które są ze sobą logicznie powiązane. Na przykład na **Home** tej aplikacji na karcie **Wytnij**, **kopiowania**, i **Wklej** polecenia znajdują się na  **Schowek** panelu. Aby dostosować panel, kliknij prawym przyciskiem myszy **Panel1** a następnie kliknij przycisk **właściwości**. W **właściwości** oknie zmiany **podpis** do *ulubione*.  
  
     Można określić **indeks obrazu** panelu. Liczba ta określa ikonę, która jest wyświetlana po dodaniu panelu wstążki do **paska narzędzi szybkiego dostępu**. Ikona nie jest wyświetlana na samym panelu wstążki.  
  
4.  Aby sprawdzić, czy kategoria i panel wstążki zostały utworzone pomyślnie, wyświetl podgląd formantu wstążki. Na **pasek narzędzi edytora wstążki**, kliknij przycisk **Testuj Wstążkę** przycisku. A **niestandardowe** kartę i **ulubione** panelu powinien być wyświetlany na Wstążce.  
  
### <a name="to-add-elements-to-the-ribbon-panels"></a>Dodawanie elementów do paneli wstążki  
  
1.  Aby dodać elementy do panelu, który został utworzony w poprzedniej procedurze, przeciągnij formanty z **edytora wstążki** części **przybornika** do panelu w widoku Projekt.  
  
2.  Najpierw dodaj **drukowania** przycisku. **Drukowania** przycisk będzie miał podmenu zawierające **szybkie drukowanie** polecenia, które inicjuje drukowanie przy użyciu domyślnej drukarki. Oba te polecenia są już zdefiniowane dla tej aplikacji. Znajdują się w menu aplikacji.  
  
     Aby utworzyć **drukowania** przycisk, przeciągnij narzędzie przycisk na panel.  
  
     W **właściwości** oknie zmiany **identyfikator** właściwości **ID_FILE_PRINT**, która już powinna być zdefiniowana. Zmiana **podpis** do *drukowania*. Zmiana **indeks obrazu** do *4*.  
  
     Aby utworzyć **szybkie drukowanie** przycisk, kliknij kolumnę wartości właściwości **elementów Menu**, a następnie kliknij przycisk wielokropka (**...** ). W **Edytor elementów**, kliknij przycisk, który nie ma etykiety **Dodaj** przycisk, aby utworzyć element menu. W **właściwości** oknie zmiany **podpis** do *szybkie drukowanie*, **identyfikator** do *ID_FILE_PRINT_DIRECT*, i **obraz** do *5*. Właściwość obrazu określa ikonę Szybkie drukowanie w zasobie mapy bitowej IDB_FILESMALL.  
  
3.  Aby sprawdzić, czy przyciski zostały dodane do panelu wstążki, skompiluj aplikację i ją uruchom. Aby skompilować aplikację, na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Jeśli aplikacja zostanie pomyślnie skompilowana, uruchom ją, klikając pozycję **Rozpocznij debugowanie** na **debugowania** menu. **Drukowania** przycisku oraz pole kombi na **ulubione** panelu **niestandardowe** karty na Wstążce powinna być wyświetlana.  
  
## <a name="next-steps"></a>Następne kroki  
 [Instrukcje: dostosowywanie paska narzędzi Szybki dostęp](../mfc/how-to-customize-the-quick-access-toolbar.md)  
  
 [Instrukcje: dostosowywanie przycisku Aplikacja](../mfc/how-to-customize-the-application-button.md)  
  
 Aby uzyskać przykłady end-to-end, zobacz [przykłady (MFC Feature Pack)](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instruktaże](../mfc/walkthroughs-mfc.md)   
 [Przykłady (MFC Feature Pack)](../visual-cpp-samples.md)

