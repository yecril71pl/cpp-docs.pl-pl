---
title: 'Formanty MFC ActiveX: dodawanie dodatkowej niestandardowej strony właściwości'
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
ms.openlocfilehash: 02c87c2c5283b7293c2a7ab028ec9a2abbba2b33
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364740"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>Formanty MFC ActiveX: dodawanie dodatkowej niestandardowej strony właściwości

Od czasu do czasu formant ActiveX będzie miał więcej właściwości niż można rozsądnie zmieścić na jednej stronie właściwości. W takim przypadku można dodać strony właściwości do formantu ActiveX, aby wyświetlić te właściwości.

W tym artykule omówiono dodawanie nowych stron właściwości do formantu ActiveX, który ma już co najmniej jedną stronę właściwości. Aby uzyskać więcej informacji na temat dodawania stron właściwości giełdowych (czcionka, obraz lub kolor), zobacz artykuł [MFC ActiveX Controls: Using Stock Property Pages](../mfc/mfc-activex-controls-using-stock-property-pages.md).

Poniższe procedury używają przykładowej struktury sterowania ActiveX utworzonej przez Kreatora sterowania ActiveX. W związku z tym nazwy klas i identyfikatory są unikatowe dla tego przykładu.

Aby uzyskać więcej informacji na temat używania stron właściwości w formancie ActiveX, zobacz następujące artykuły:

- [Kontrolki ActiveX MFC: strony właściwości](../mfc/mfc-activex-controls-property-pages.md)

- [Kontrolki ActiveX MFC: używanie stron właściwości standardowych](../mfc/mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  Zdecydowanie zaleca się, aby nowe strony właściwości były zgodne ze standardem rozmiaru dla stron właściwości formantu ActiveX. Strony właściwości obrazu stockowego i koloru mierzą jednostki dialogowe 250x62 (DLU). Strona właściwości czcionki standardowej to 250x110 DLU. Domyślna strona właściwości utworzona przez Kreatora sterowania ActiveX używa standardu DLU 250x62.

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>Aby wstawić nowy szablon strony właściwości do projektu

1. Po otwarciu projektu sterującego otwórz widok zasobów w obszarze roboczym projektu.

1. Kliknij prawym przyciskiem myszy widok zasobu, aby otworzyć menu skrótów i kliknąć polecenie **Dodaj zasób**.

1. Rozwiń węzeł **dialogowy** i wybierz **IDD_OLE_PROPPAGE_SMALL**.

1. Kliknij **przycisk Nowy,** aby dodać zasób do projektu.

1. Wybierz nowy szablon strony właściwości, aby **odświeżyć** okno Właściwości (w **widoku zasobu**).

1. Wprowadź nową wartość właściwości **Identyfikator.** W tym przykładzie użyto **IDD_PROPPAGE_NEWPAGE**.

1. Kliknij przycisk **Zapisz** na pasku narzędzi.

### <a name="to-associate-the-new-template-with-a-class"></a>Aby skojarzyć nowy szablon z klasą

1. Otwórz widok klasy.

1. Kliknij prawym przyciskiem myszy widok klasy, aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj,** a następnie kliknij pozycję **Dodaj klasę**.

   Spowoduje to otwarcie okna dialogowego [Dodawanie klasy.](../ide/add-class-dialog-box.md)

1. Kliknij dwukrotnie szablon **klasy MFC.**

1. W polu **Nazwa klasy** w [Kreatorze klas MFC](../mfc/reference/mfc-add-class-wizard.md)wpisz nazwę nowej klasy okna dialogowego. (W tym `CAddtlPropPage`przykładzie .)

1. Jeśli chcesz zmienić nazwy plików, kliknij przycisk **Zmień**. Wpisz nazwy dla implementacji i plików nagłówkowych lub zaakceptuj nazwy domyślne.

1. W polu **Klasa podstawowa** wybierz opcję `COlePropertyPage`.

1. W polu **Identyfikator okna dialogowego** wybierz **IDD_PROPPAGE_NEWPAGE**.

1. Kliknij **przycisk Zakończ,** aby utworzyć klasę.

Aby umożliwić użytkownikom formantu dostęp do tej nowej strony właściwości, należy wprowadzić następujące zmiany w sekcji makra identyfikatorów właściwości formantu (znajdującej się w pliku implementacji formantu):

[!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

Należy zauważyć, że należy zwiększyć drugi parametr makra BEGIN_PROPPAGEIDS (liczba stron właściwości) z 1 do 2.

Należy również zmodyfikować plik implementacji formantu (. CPP) w celu uwzględnienia nagłówka (. H) plik nowej klasy strony właściwości.

Następnym krokiem jest utworzenie dwóch nowych zasobów ciągu, który zapewni nazwę typu i podpis dla nowej strony właściwości.

#### <a name="to-add-new-string-resources-to-a-property-page"></a>Aby dodać nowe zasoby ciągu do strony właściwości

1. Po otwarciu projektu sterującego otwórz widok zasobów.

1. Kliknij dwukrotnie folder **Tabela ciągów,** a następnie kliknij dwukrotnie istniejący zasób tabeli ciągów, do którego chcesz dodać ciąg.

   Spowoduje to otwarcie tabeli ciągów w oknie.

1. Zaznacz pusty wiersz na końcu tabeli ciągów i wpisz tekst lub podpis ciągu: na przykład "Strona właściwości dodatkowych".

   Spowoduje to otwarcie strony **Właściwości ciągu** z **oknami Podpis i** **Identyfikator.** Pole **Podpis** zawiera wpisany ciąg znaków.

1. W polu **Identyfikator** wybierz lub wpisz identyfikator ciągu. Po zakończeniu naciśnij klawisz Enter.

   W tym przykładzie użyto **IDS_SAMPLE_ADDPAGE** dla nazwy typu nowej strony właściwości.

1. Powtórz kroki 3 i 4, używając **IDS_SAMPLE_ADDPPG_CAPTION** dla identyfikatora i "Strony dodatkowej właściwości" dla podpisu.

1. W. Plik CPP nowej klasy strony właściwości (w tym `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` przykładzie) zmodyfikuj tak, `CAddtlPropPage`aby IDS_SAMPLE_ADDPAGE była przekazywana przez [AfxOleRegisterPropertyPageClass](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass), jak w poniższym przykładzie:

   [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. Zmodyfikuj `CAddtlPropPage` konstruktora tak, `COlePropertyPage` aby IDS_SAMPLE_ADDPPG_CAPTION jest przekazywana do konstruktora w następujący sposób:

   [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

Po dokonaniu niezbędnych modyfikacji odbudować projekt i użyj test kontenera, aby przetestować nową stronę właściwości. Zobacz [testowanie właściwości i zdarzenia z kontenerem testowym,](../mfc/testing-properties-and-events-with-test-container.md) aby uzyskać informacje na temat uzyskiwania dostępu do kontenera testowego.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)
