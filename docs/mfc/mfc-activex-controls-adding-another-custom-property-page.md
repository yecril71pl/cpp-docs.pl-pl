---
title: 'Formanty ActiveX MFC: Dodawanie dodatkowej niestandardowej strony właściwości | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a0e8713bc228e65cb06e58d7ccb5389f7366e76
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>Kontrolki ActiveX MFC: dodawanie dodatkowej niestandardowej strony właściwości
Czasami formantu ActiveX ma więcej właściwości, niż można przypuszczać zmieścić na jednej stronie właściwości. W takim przypadku można dodać strony właściwości do formantu ActiveX, aby wyświetlić te właściwości.  
  
 W tym artykule omówiono Dodawanie nowych stron właściwości do formantu ActiveX, który ma już co najmniej jedną stronę właściwości. Aby uzyskać więcej informacji na temat dodawania właściwości standardowych stron (czcionki, obraz lub kolor), zobacz artykuł [kontrolki ActiveX MFC: przy użyciu strony właściwości zasobów](../mfc/mfc-activex-controls-using-stock-property-pages.md).  
  
 Poniższe procedury użyj przykładowych framework formantu ActiveX utworzone przez kreatora formantu ActiveX. W związku z tym nazwy klas i identyfikatory różnią się w tym przykładzie.  
  
 Aby uzyskać więcej informacji na używanie stron właściwości formantu ActiveX zobacz następujące artykuły:  
  
-   [Kontrolki ActiveX MFC: strony właściwości](../mfc/mfc-activex-controls-property-pages.md)  
  
-   [Kontrolki ActiveX MFC: używanie stron właściwości standardowych](../mfc/mfc-activex-controls-using-stock-property-pages.md)  
  
    > [!NOTE]
    >  Zalecane jest tej właściwości nowej strony odpowiednia rozmiar standardowego dla strony właściwości formantu ActiveX. Właściwości podstawowych obrazu i kolor strony miary 250 x 62 jednostki okna dialogowego (DLU). Strona właściwości standardowej czcionki jest Dlu 250 x 110. Właściwości domyślnej strony utworzone przez kreatora formantu ActiveX korzysta ze standardu DLU 250 x 62.  
  
### <a name="to-insert-a-new-property-page-template-into-your-project"></a>Aby wstawić nowy szablon strony właściwości do projektu  
  
1.  Otwarciu projektu kontroli Otwórz widok zasobów w obszarze roboczym projekt.  
  
2.  Kliknij prawym przyciskiem myszy w widoku zasobów, aby otworzyć menu skrótów, a następnie kliknij przycisk **dodawania zasobów**.  
  
3.  Rozwiń węzeł **okna dialogowego** , a następnie wybierz węzeł **IDD_OLE_PROPPAGE_SMALL**.  
  
4.  Kliknij przycisk `New` można dodać zasobu do projektu.  
  
5.  Wybierz nowy szablon strony właściwości, aby odświeżyć okno właściwości.  
  
6.  Wprowadź nową wartość dla **identyfikator** właściwości. W tym przykładzie użyto **IDD_PROPPAGE_NEWPAGE**.  
  
7.  Kliknij przycisk **zapisać** na pasku narzędzi.  
  
### <a name="to-associate-the-new-template-with-a-class"></a>Aby skojarzyć nowego szablonu z klasy  
  
1.  Otwórz widok klas.  
  
2.  Kliknij prawym przyciskiem myszy w widoku klas, aby otworzyć menu skrótów.  
  
3.  W menu skrótów kliknij **Dodaj** , a następnie kliknij przycisk **Dodaj klasę**.  
  
     Spowoduje to otwarcie [Dodaj klasę](../ide/add-class-dialog-box.md) okno dialogowe.  
  
4.  Kliknij dwukrotnie **klasy MFC** szablonu.  
  
5.  W **Nazwa klasy** polu [Kreator klas MFC](../mfc/reference/mfc-add-class-wizard.md), wpisz nazwę dla nowej klasy okna dialogowego. (W tym przykładzie `CAddtlPropPage`.)  
  
6.  Aby zmienić nazwy pliku, kliknij przycisk **zmienić**. Wpisz nazwy plików implementacji i nagłówka, lub zaakceptować domyślne nazwy.  
  
7.  W **klasa podstawowa** wybierz opcję `COlePropertyPage`.  
  
8.  W **identyfikator okna dialogowego** wybierz opcję **IDD_PROPPAGE_NEWPAGE**.  
  
9. Kliknij przycisk **Zakończ** Aby utworzyć klasę.  
  
 Aby umożliwić użytkownikom kontroli dostępu do tej nowej strony właściwości, należy wprowadzić następujące zmiany do formantu właściwości strony identyfikatorów makro sekcji (znajdujący się w pliku implementacji):  
  
 [!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]  
  
 Należy pamiętać, że należy zwiększyć drugi parametr funkcji `BEGIN_PROPPAGEIDS` makra (liczba stron właściwości) z zakresu od 1 do 2.  
  
 Musisz także zmodyfikować plik implementacji formantu (. Dołącz nagłówek pliku CPP) (. H) pliku nowej klasy strony właściwości.  
  
 Następny krok polega na utworzenie dwóch nowych zasobów ciągu, które zapewnią nazwę typu i podpis nowej strony właściwości.  
  
#### <a name="to-add-new-string-resources-to-a-property-page"></a>Aby dodać nowe zasoby ciągu do strony właściwości  
  
1.  Otwórz projekt kontroli Otwórz widok zasobów.  
  
2.  Kliknij dwukrotnie **tabeli ciągów** folder, a następnie dwukrotnie kliknij istniejący ciąg tabeli zasobów, do której chcesz dodać ciąg.  
  
     Spowoduje to otwarcie tabeli ciągów w oknie.  
  
3.  Wybierz pusty wiersz na końcu tabeli ciągów i wpisz tekst lub podpis ciągu: na przykład "dodatkowe strony właściwości."  
  
     Spowoduje to otwarcie **właściwości ciągu** stronie **podpis** i **identyfikator** pola. **Podpis** pole zawiera ciąg został wpisany.  
  
4.  W **identyfikator** wybierz lub wpisz identyfikator ciągu. Po zakończeniu naciśnij klawisz Enter.  
  
     W tym przykładzie użyto **IDS_SAMPLE_ADDPAGE** dla typu nazwa nowej strony właściwości.  
  
5.  Powtórz kroki 3 i 4 przy użyciu **IDS_SAMPLE_ADDPPG_CAPTION** dla Identyfikatora i "Dodatkowe właściwości Page" podpisu.  
  
6.  W. Pliku CPP nowej klasy strony właściwości (w tym przykładzie `CAddtlPropPage`) zmodyfikować `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` tak, aby IDS_SAMPLE_ADDPAGE jest przekazywana przez [afxoleregisterpropertypageclass —](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass), jak w poniższym przykładzie:  
  
     [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]  
  
7.  Modyfikowanie konstruktora `CAddtlPropPage` , aby **IDS_SAMPLE_ADDPPG_CAPTION** jest przekazywana do `COlePropertyPage` konstruktora w następujący sposób:  
  
     [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]  
  
 Po dokonaniu niezbędnych modyfikacji ponownie skompiluj projekt i testować nowe strony właściwości przy użyciu kontenera testu. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](../mfc/testing-properties-and-events-with-test-container.md) informacji na temat sposobu dostępu kontener testu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

