---
title: 'Kontrolki ActiveX MFC: Dodawanie dodatkowej niestandardowej strony właściwości | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 1599500a775bcd1c76f2e63a1f7b20126a2fb329
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078209"
---
# <a name="mfc-activex-controls-adding-another-custom-property-page"></a>Kontrolki ActiveX MFC: dodawanie dodatkowej niestandardowej strony właściwości

Od czasu do czasu formant ActiveX ma więcej właściwości, niż jest mieści się na jednej stronie właściwości. W takim przypadku można dodać strony właściwości do kontrolki ActiveX, aby wyświetlić te właściwości.

W tym artykule omówiono, dodając nowe właściwości do kontrolki ActiveX, który ma już co najmniej jedną stronę właściwości. Aby uzyskać więcej informacji na temat dodawania właściwości podstawowych stron (czcionkę, obrazu lub kolor), zobacz artykuł [kontrolki ActiveX MFC: przy użyciu strony właściwości zasobów](../mfc/mfc-activex-controls-using-stock-property-pages.md).

W poniższych procedurach użyto przykładowej framework formantu ActiveX utworzone przez kreatora kontrolek ActiveX. W związku z tym nazwy klas i identyfikatory są unikatowe dla tego przykładu.

Aby uzyskać więcej informacji na temat używania stron właściwości w kontrolce ActiveX zobacz następujące artykuły:

- [Kontrolki ActiveX MFC: strony właściwości](../mfc/mfc-activex-controls-property-pages.md)

- [Kontrolki ActiveX MFC: używanie stron właściwości standardowych](../mfc/mfc-activex-controls-using-stock-property-pages.md)

    > [!NOTE]
    >  Zdecydowanie zaleca się tej nowej właściwości, które strony stosować się do rozmiaru standardem dla stron właściwości kontrolki ActiveX. Właściwości podstawowych obrazu i kolor strony miary 250 x 62 jednostki okna dialogowego (DLU). Strona właściwości czcionki standardowej jest Dlu 250 x 110. Strona właściwości domyślne utworzone przez kreatora kontrolek ActiveX używa standardu DLU 250 x 62.

### <a name="to-insert-a-new-property-page-template-into-your-project"></a>Aby wstawić nowy szablon strony właściwości do projektu

1. Za pomocą formantu projektu open Otwórz widok zasobów w obszarze roboczym projektu.

1. Kliknij prawym przyciskiem myszy w widoku zasobu, aby otworzyć menu skrótów, a następnie kliknij przycisk **Dodaj zasób**.

1. Rozwiń **okna dialogowego** , a następnie wybierz węzeł **IDD_OLE_PROPPAGE_SMALL**.

1. Kliknij przycisk **New** można dodać zasobu do projektu.

1. Wybierz nowy szablon strony właściwości, aby odświeżyć okno właściwości.

1. Wprowadź nową wartość dla **identyfikator** właściwości. W tym przykładzie użyto **IDD_PROPPAGE_NEWPAGE**.

1. Kliknij przycisk **Zapisz** na pasku narzędzi.

### <a name="to-associate-the-new-template-with-a-class"></a>Aby skojarzyć nowego szablonu przy użyciu klasy

1. Otwórz widok klas.

1. Kliknij prawym przyciskiem myszy w widoku klas, aby otworzyć menu skrótów.

1. W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodaj klasę**.

   Spowoduje to otwarcie [Dodaj klasę](../ide/add-class-dialog-box.md) okno dialogowe.

1. Kliknij dwukrotnie **klasy MFC** szablonu.

1. W **Nazwa klasy** pole w [Kreator klas MFC](../mfc/reference/mfc-add-class-wizard.md), wpisz nazwę dla nowej klasy okien dialogowych. (W tym przykładzie `CAddtlPropPage`.)

1. Aby zmienić nazwy pliku, kliknij przycisk **zmienić**. Wpisz nazwy dla Twojego wdrożenia a plikami nagłówka, lub zaakceptować domyślne nazwy.

1. W **klasa bazowa** wybierz opcję `COlePropertyPage`.

1. W **identyfikator okna dialogowego** wybierz opcję **IDD_PROPPAGE_NEWPAGE**.

9. Kliknij przycisk **Zakończ** Aby utworzyć klasę.

Aby umożliwić użytkownikom kontroli dostępu do tej nowej strony właściwości, należy wprowadzić następujące zmiany do formantu właściwości strony identyfikatory — makro sekcji (znajdujący się w pliku implementacji):

[!code-cpp[NVC_MFC_AxUI#32](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_1.cpp)]

Należy pamiętać, że należy zwiększyć drugi parametr BEGIN_PROPPAGEIDS — makro (liczba stron właściwości) z zakresu od 1 do 2.

Musisz także zmodyfikować plik implementacji kontroli (. Plik CPP), aby dołączyć nagłówek (. H) plik nowej klasy strony właściwości.

Następny krok polega na utworzenie dwóch nowych zasobów ciągów, które zapewnią nazwę typu i podpis nowe strony właściwości.

#### <a name="to-add-new-string-resources-to-a-property-page"></a>Aby dodać nowe zasoby ciągu do strony właściwości

1. Za pomocą formantu projektu open Otwórz widok zasobów.

1. Kliknij dwukrotnie **tabeli ciągów** folder, a następnie kliknij dwukrotnie istniejących parametrów tabeli zasobów, do której chcesz dodać ciąg.

   Spowoduje to otwarcie tabeli ciągów w oknie.

1. Wybierz pusty wiersz na końcu tabeli ciągów i typu text lub caption ciągu: na przykład "dodatkowe właściwości Page."

   Spowoduje to otwarcie **właściwości ciągu** przedstawiający stronę **podpis** i **identyfikator** pola. **Podpis** pole zawiera ciąg wpisany.

1. W **identyfikator** wybierz lub wpisz identyfikator ciągu. Po zakończeniu naciśnij klawisz Enter.

   W tym przykładzie użyto **IDS_SAMPLE_ADDPAGE** dla nazwy typu nowej strony właściwości.

1. Powtórz kroki 3 i 4 używające funkcji **IDS_SAMPLE_ADDPPG_CAPTION** dla Identyfikatora i "Dodatkowe właściwości Page" podpisu.

1. W. Plik CPP nowej klasy strony właściwości (w tym przykładzie `CAddtlPropPage`) zmodyfikuj `CAddtlPropPage::CAddtlPropPageFactory::UpdateRegistry` tak, aby IDS_SAMPLE_ADDPAGE jest przekazywany przez [afxoleregisterpropertypageclass —](../mfc/reference/registering-ole-controls.md#afxoleregisterpropertypageclass), jak w poniższym przykładzie:

   [!code-cpp[NVC_MFC_AxUI#33](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_2.cpp)]

1. Zmodyfikuj konstruktora `CAddtlPropPage` tak, aby IDS_SAMPLE_ADDPPG_CAPTION jest przekazywany do `COlePropertyPage` konstruktora, w następujący sposób:

   [!code-cpp[NVC_MFC_AxUI#34](../mfc/codesnippet/cpp/mfc-activex-controls-adding-another-custom-property-page_3.cpp)]

Po dokonaniu niezbędnych modyfikacji ponownie skompiluj projekt i użyj kontener testu, aby przetestować nową stronę właściwości. Zobacz [testowanie właściwości i zdarzeń za pomocą kontenera testu](../mfc/testing-properties-and-events-with-test-container.md) informacji na temat dostępu do kontenera testu.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

