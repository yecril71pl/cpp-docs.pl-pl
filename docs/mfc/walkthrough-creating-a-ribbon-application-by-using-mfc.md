---
title: 'Wskazówki: Tworzenie aplikacji wstążki za pomocą MFC | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 7f715830c110f03811202d2e98dc097bfe712208
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-a-ribbon-application-by-using-mfc"></a>Wskazówki: tworzenie aplikacji wstążki za pomocą MFC
Ten przewodnik przedstawia sposób użycia **Kreator aplikacji MFC** do tworzenia aplikacji, która domyślnie ma wstążki. Można następnie rozwiń węzeł wstążki, dodając **niestandardowy** wstążki kategorię, która ma **ulubione** wstążki panelu, a następnie dodać niektóre często używane polecenia do panelu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym przewodniku przyjęto założenie, że ustawiono [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] do używania **ogólne ustawienia środowiska deweloperskiego**. Jeśli są używane inne ustawienia, niektóre elementy interfejsu użytkownika, do których odwołują się poniższe instrukcje, mogą nie być wyświetlane. Aby uzyskać informacje dotyczące zmiany ustawień, zobacz [porady: resetowanie ustawień](http://msdn.microsoft.com/en-us/c95c51be-e609-4769-abba-65e6beedec76).  
  
### <a name="to-create-an-mfc-application-that-has-a-ribbon"></a>Tworzenie aplikacji MFC zawierającej wstążkę  
  
1.  Użyj **Kreator aplikacji MFC** do utworzenia aplikacji MFC, która ma wstążki. Aby uruchomić kreatora, na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **Visual C++** węźle **zainstalowane szablony**, wybierz pozycję **MFC**, a następnie wybierz  **Aplikacja MFC**. Wpisz nazwę projektu, na przykład `MFCRibbonApp`, a następnie kliknij przycisk **OK**.  
  
3.  Na pierwszej stronie **Kreator aplikacji MFC**, kliknij przycisk **dalej**.  
  
4.  Na **typu aplikacji** w obszarze **styl wizualny i kolory**, wybierz pozycję **Office 2007 (motyw niebieski)**. Pozostałych ustawień nie zmieniaj. Kliknij przycisk **Dalej**.  
  
5.  Na **Obsługa dokumentów złożonych** strony, upewnij się, że **Brak** jest zaznaczone, a następnie kliknij przycisk **dalej**.  
  
6.  Na **właściwości szablonu dokumentu** strony w **rozszerzenie pliku** wpisz rozszerzenie nazwy pliku dla dokumentów, które tworzy tej aplikacji, na przykład `mfcrbnapp`. Kliknij przycisk **Dalej**.  
  
7.  Na **obsługi bazy danych** strony, upewnij się, że **Brak** jest zaznaczone, a następnie kliknij przycisk **dalej**.  
  
8.  Na **funkcje interfejsu użytkownika** strony, upewnij się, że **Użyj wstążki** jest zaznaczone. Kliknij przycisk **Dalej**.  
  
9. Domyślnie **Kreator aplikacji MFC** dodaje obsługę kilku okienek dokowania. Ponieważ ten instruktaż jest poświęcony wyłącznie wstążce, można usunąć te opcje z aplikacji. Na **funkcje zaawansowane** Usuń zaznaczenie wszystkich opcji. Kliknij przycisk **Dalej**.  
  
10. Na **wygenerowane klasy** kliknij przycisk **Zakończ** do tworzenia aplikacji MFC.  
  
11. Aby sprawdzić, czy aplikacja została pomyślnie utworzona, należy ją skompilować i uruchomić. Do skompilowania aplikacji, na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Jeśli aplikacja tworzy się pomyślnie, uruchom go, klikając **Rozpocznij debugowanie** na **debugowania** menu.  
  
     Kreator automatycznie tworzy wstążką, który ma jedną kategorię wstążki o nazwie **Home**. Trzy panele wstążki, które są nazywane zawiera tę Wstążkę **Schowka**, **widoku**, i **okna**.  
  
### <a name="to-add-a-category-and-panel-to-the-ribbon"></a>Dodawanie kategorii i panelu do wstążki  
  
1.  Aby otworzyć Kreatora utworzony na zasób wstążki **widoku** menu wskaż **inne okna** , a następnie kliknij przycisk **widok zasobów**. W **widok zasobów**, kliknij przycisk **wstążki** , a następnie kliknij dwukrotnie ikonę **IDR_RIBBON**.  
  
2.  Najpierw Dodaj kategorię niestandardową do wstążki, klikając dwukrotnie **kategorii** w **przybornika**.  
  
     Kategorię, która ma podpis **kategoria 1** jest tworzony. Domyślnie kategoria zawiera jeden panel.  
  
     Kliknij prawym przyciskiem myszy **kategoria 1** , a następnie kliknij przycisk **właściwości**. W **właściwości** Zmień **podpis** do `Custom`.  
  
     **Duże obrazy** i **małe obrazy** właściwości określają mapy bitowe, które są używane jako ikony dla elementów wstążki w tej kategorii. Ponieważ tworzenie niestandardowych map bitowych wykracza poza zakres tego instruktażu, należy po prostu użyć map bitowych utworzonych przez kreatora. Małe mapy bitowe mają rozmiar 16 x 16 pikseli. Do małych obrazów należy stosować mapy bitowe wykorzystywane przez identyfikator zasobu IDB_FILESMALL. Duże mapy bitowe mają rozmiar 32 x 32 piksele. Do dużych obrazów należy stosować mapy bitowe używane przez identyfikator zasobu IDB_FILELARGE.  
  
    > [!NOTE]
    >  Na ekranach o dużej liczbie punktów na cal (HDPI) automatycznie są używane wersje HDPI obrazów.  
  
3.  Następnie dostosuj panel. Panele służą do grupowania elementów, które są ze sobą logicznie powiązane. Na przykład na **Home** tej aplikacji, na karcie **Wytnij**, **kopiowania**, i **Wklej** polecenia znajdują się na  **Schowek** panelu. Aby dostosować panelu, kliknij prawym przyciskiem myszy **Panel1** , a następnie kliknij przycisk **właściwości**. W **właściwości** Zmień **podpis** do `Favorites`.  
  
     Można określić **indeks obrazu** panelu. Liczba ta określa ikonę, która jest wyświetlana, jeśli panel wstążki jest dodawany do **pasek narzędzi Szybki dostęp**. Ikona nie jest wyświetlana na samym panelu wstążki.  
  
4.  Aby sprawdzić, czy kategoria i panel wstążki zostały utworzone pomyślnie, wyświetl podgląd formantu wstążki. Na **paska narzędzi edytora wstążki**, kliknij przycisk **wstążki testu** przycisku. A **niestandardowy** kartę i **ulubione** panelu powinna być wyświetlana na Wstążce.  
  
### <a name="to-add-elements-to-the-ribbon-panels"></a>Dodawanie elementów do paneli wstążki  
  
1.  Aby dodać elementy do panelu, który został utworzony w poprzedniej procedurze, przeciągnij formanty z **edytora wstążki** sekcji **przybornika** do panelu w widoku Projekt.  
  
2.  Najpierw dodaj **drukowania** przycisku. **Drukowania** przycisk ma podmenu, który zawiera **szybkie drukowanie** polecenie, które wyświetla przy użyciu drukarki domyślnej. Oba te polecenia są już zdefiniowane dla tej aplikacji. Znajdują się w menu aplikacji.  
  
     Aby utworzyć **drukowania** przycisku, przeciągnij narzędzie przycisk do panelu.  
  
     W **właściwości** Zmień **identyfikator** właściwości **id_file_print —**, który już powinien być zdefiniowany. Zmień **podpis** do `Print`. Zmień **indeks obrazu** do `4`.  
  
     Aby utworzyć **szybkie drukowanie** , kliknij Dalej, aby kolumna wartości właściwości **elementów Menu**, a następnie kliknij przycisk wielokropka (**...** ). W **Edytor elementów**, kliknij przycisk bez etykiety **Dodaj** przycisk, aby utworzyć element menu. W **właściwości** Zmień **podpis** do `Quick Print`, **identyfikator** do `ID_FILE_PRINT_DIRECT`, i **obrazu** do `5` . Właściwość obrazu określa ikonę Szybkie drukowanie w zasobie mapy bitowej IDB_FILESMALL.  
  
3.  Aby sprawdzić, czy przyciski zostały dodane do panelu wstążki, skompiluj aplikację i ją uruchom. Do skompilowania aplikacji, na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Jeśli aplikacja tworzy się pomyślnie, uruchom aplikację, klikając **Rozpocznij debugowanie** na **debugowania** menu. **Drukowania** przycisk i pole kombi pole na **ulubione** panelu na **niestandardowy** powinna być wyświetlana na Wstążce.  
  
## <a name="next-steps"></a>Następne kroki  
 [Instrukcje: dostosowywanie paska narzędzi Szybki dostęp](../mfc/how-to-customize-the-quick-access-toolbar.md)  
  
 [Instrukcje: dostosowywanie przycisku Aplikacja](../mfc/how-to-customize-the-application-button.md)  
  
 Przykłady end-to-end można wyświetlić [przykłady (pakiet funkcji MFC)](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instruktaże](../mfc/walkthroughs-mfc.md)   
 [Przykłady (pakiet funkcji MFC)](../visual-cpp-samples.md)

