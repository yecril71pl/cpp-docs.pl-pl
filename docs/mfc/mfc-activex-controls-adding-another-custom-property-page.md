---
title: 'Formanty MFC ActiveX: dodawanie dodatkowej niestandardowej strony właściwości'
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC ActiveX controls
- custom property pages [MFC]
- ActiveX controls [MFC], property pages
- MFC ActiveX controls [MFC], property pages
ms.assetid: fcf7e119-9f29-41a9-908d-e9b1607e08af
ms.openlocfilehash: 33fd297ee509b341d39d9db21af54a3988f6256e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618289"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>Formanty MFC ActiveX: dodawanie dodatkowej niestandardowej strony właściwości

Czasami formant ActiveX będzie miał więcej właściwości, niż może być odpowiednio dopasowany do jednej strony właściwości. W takim przypadku można dodać do kontrolki ActiveX strony właściwości, aby wyświetlić te właściwości.

W tym artykule omówiono dodawanie nowych stron właściwości do kontrolki ActiveX, która zawiera już co najmniej jedną stronę właściwości. Aby uzyskać więcej informacji na temat dodawania stron właściwości podstawowych (czcionki, obrazu lub koloru), zobacz artykuł [kontrolki ActiveX MFC: używanie stron właściwości podstawowych](mfc-activex-controls-using-stock-property-pages.md).

Poniższe procedury wykorzystują przykładową strukturę formantu ActiveX utworzoną przez kreatora kontrolek ActiveX. W związku z tym nazwy klas i identyfikatory są unikatowe dla tego przykładu.

Aby uzyskać więcej informacji na temat używania stron właściwości w kontrolce ActiveX, zobacz następujące artykuły:

- [Kontrolki ActiveX MFC: strony właściwości](mfc-activex-controls-property-pages.md)

- [Kontrolki ActiveX MFC: używanie stron właściwości standardowych](mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  Zdecydowanie zaleca się, aby nowe strony właściwości były zgodne ze standardem rozmiaru dla stron właściwości kontrolki ActiveX. Strony właściwości obrazu i koloru miar miary 250x62ą jednostki okna dialogowego (DLU). Strona właściwości czcionki standardowej to 250x110 DLU. Domyślna strona właściwości utworzona przez kreatora kontrolki ActiveX używa standardu 250x62 DLU.

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>Aby wstawić nowy szablon strony właściwości do projektu

1. Po otwarciu projektu kontrolki Otwórz Widok zasobów w obszarze roboczym projektu.

1. Kliknij prawym przyciskiem myszy w Widok zasobów, aby otworzyć menu skrótów, a następnie kliknij pozycję **Dodaj zasób**.

1. Rozwiń węzeł **okna dialogowego** , a następnie wybierz pozycję **IDD_OLE_PROPPAGE_SMALL**.

1. Kliknij pozycję **Nowy** , aby dodać zasób do projektu.

1. Wybierz nowy szablon strony właściwości, aby odświeżyć okno **Właściwości** (w **Widok zasobów**).

1. Wprowadź nową wartość właściwości **ID** . Ten przykład używa **IDD_PROPPAGE_NEWPAGE**.

1. Kliknij przycisk **Zapisz** na pasku narzędzi.

### <a name="to-associate-the-new-template-with-a-class"></a>Aby skojarzyć nowy szablon z klasą

1. Otwórz Widok klasy.

1. Kliknij prawym przyciskiem myszy w Widok klasy, aby otworzyć menu skrótów.

1. W menu skrótów kliknij pozycję **Dodaj** , a następnie kliknij pozycję **Dodaj klasę**.

   Spowoduje to otwarcie okna dialogowego [Dodaj klasę](../ide/add-class-dialog-box.md) .

1. Kliknij dwukrotnie szablon **klasy MFC** .

1. W polu **Nazwa klasy** w [Kreatorze klasy MFC](reference/mfc-add-class-wizard.md)wpisz nazwę nowej klasy okna dialogowego. (W tym przykładzie `CAddtlPropPage` ).

1. Jeśli chcesz zmienić nazwy plików, kliknij przycisk **Zmień**. Wpisz nazwy plików implementacji i nagłówka lub zaakceptuj nazwy domyślne.

1. W polu **Klasa podstawowa** wybierz opcję `COlePropertyPage` .

1. W polu **Identyfikator okna dialogowego** wybierz opcję **IDD_PROPPAGE_NEWPAGE**.

1. Kliknij przycisk **Zakończ** , aby utworzyć klasę.

Aby umożliwić użytkownikom formantu dostęp do tej nowej strony właściwości, wprowadź następujące zmiany w sekcji Macro ID strony właściwości kontrolki (znajdującej się w pliku implementacji formantu):

[!code-cpp[NVC_MFC_AxUI#32](codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

Należy pamiętać, że należy zwiększyć drugi parametr makra BEGIN_PROPPAGEIDS (liczba stron właściwości) od 1 do 2.

Należy również zmodyfikować plik implementacji formantu (. CPP) do uwzględnienia nagłówka (. H) plik nowej klasy strony właściwości.

Następny krok polega na utworzeniu dwóch nowych zasobów ciągów, które będą dostarczać nazwę typu i podpis dla nowej strony właściwości.

#### <a name="to-add-new-string-resources-to-a-property-page"></a>Aby dodać nowe zasoby ciągu do strony właściwości

1. Po otwarciu projektu kontrolki Otwórz Widok zasobów.

1. Kliknij dwukrotnie folder **tabeli ciągów** , a następnie kliknij dwukrotnie istniejący zasób tabeli ciągów, do którego chcesz dodać ciąg.

   Spowoduje to otwarcie tabeli ciągów w oknie.

1. Zaznacz pusty wiersz na końcu tabeli ciągów i wpisz tekst, lub podpis, ciągu: na przykład "dodatkowa strona właściwości".

   Spowoduje to otwarcie strony **Właściwości ciągu** pokazującej pola **podpisu** i **identyfikatora** . Pole **podpis** zawiera wpisaną ciąg.

1. W polu **Identyfikator** wybierz lub wpisz identyfikator ciągu. Naciśnij klawisz Enter po zakończeniu.

   Ten przykład używa **IDS_SAMPLE_ADDPAGE** dla nazwy typu nowej strony właściwości.

1. Powtórz kroki 3 i 4, używając **IDS_SAMPLE_ADDPPG_CAPTION** identyfikatorów i "dodatkowej strony właściwości" dla podpisu.

1. W. Plik CPP nowej klasy strony właściwości (w tym przykładzie `CAddtlPropPage` ) zmodyfikuj, `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` tak aby IDS_SAMPLE_ADDPAGE jest przenoszona przez [AfxOleRegisterPropertyPageClass](reference/registering-ole-controls.md#afxoleregisterpropertypageclass), jak w poniższym przykładzie:

   [!code-cpp[NVC_MFC_AxUI#33](codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. Zmodyfikuj konstruktora `CAddtlPropPage` , tak aby IDS_SAMPLE_ADDPPG_CAPTION jest przenoszona do `COlePropertyPage` konstruktora w następujący sposób:

   [!code-cpp[NVC_MFC_AxUI#34](codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

Po dokonaniu niezbędnych modyfikacji Skompiluj projekt i Użyj kontenera testów do przetestowania nowej strony właściwości. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testów,](testing-properties-and-events-with-test-container.md) Aby uzyskać informacje na temat uzyskiwania dostępu do kontenera testowego.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)
