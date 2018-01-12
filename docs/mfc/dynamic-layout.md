---
title: "Układ dynamiczny | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 8598cfb2-c8d4-4f5a-bf2b-59dc4653e042
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e309d8ef023346c0e37babeabe23f7e6e1762939
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dynamic-layout"></a>Układ dynamiczny
Z MFC w programie Visual Studio 2015 można utworzyć okna dialogowe, które użytkownik może zmienić rozmiar i kontrolować sposób, który dostosowuje układ na zmianę rozmiaru. Na przykład można dołączyć przycisków w dolnej części okna dialogowego do dolnej krawędzi, więc zawsze pozostają na dole. Można również skonfigurować niektóre formanty, takie jak pól list, editboxes i pola tekstowego rozszerzenia, ponieważ użytkownik rozwija okna dialogowego.  
  
## <a name="specifying-dynamic-layout-settings-for-an-mfc-dialog-box"></a>Określanie ustawień dynamicznych układu okna dialogowego MFC  
 Gdy użytkownik zmienia rozmiar okna dialogowego, formantów w oknie dialogowym można zmienić rozmiar lub przenieść w kierunku X i Y. Zmiana rozmiaru lub położenia kontrolki, gdy użytkownik zmienia rozmiar okna dialogowego jest nazywany układ dynamiczny. Na przykład Oto okna dialogowego przed zmieniany:  
  
 ![Okno dialogowe przed zmieniany. ] (../mfc/media/mfcdynamiclayout4.png "mfcdynamiclayout4")  
  
 Po zmianie rozmiaru, obszar listbox zostaje zwiększona do Pokaż więcej elementów, a przyciski są przenoszone wraz z prawym dolnym rogu:  
  
 ![Okno dialogowe po zmieniany. ] (../mfc/media/mfcdynamiclayout5.png "mfcdynamiclayout5")  
  
 Układ dynamiczny można kontrolować, określając szczegółów dla każdego formantu w edytorze zasobów w środowisku IDE lub należy więc programowane uzyskiwanie dostępu do obiektu CMFCDynamicLayout dla określonego formantu i ustawiając właściwości.  
  
### <a name="setting-dynamic-layout-properties-in-the-resource-editor"></a>Ustawianie właściwości dynamicznych układu w edytorze zasobów  
 Bez konieczności pisania kodu, za pomocą edytora zasobów można ustawić zachowanie układ dynamiczny dla okna dialogowego.  
  
##### <a name="to-set-dynamic-layout-properties-in-the-resource-editor"></a>Aby ustawić właściwości dynamicznych układu w edytorze zasobów  
  
1.  Z projektu MFC otwarte Otwórz okno dialogowe, przeznaczonych do pracy w programie edytora okien dialogowych.  
  
     ![Otwórz okno dialogowe w edytorze zasobów. ] (../mfc/media/mfcdynamiclayout3.png "mfcdynamiclayout3")  
  
2.  Wybierz kontrolkę i w oknie właściwości ustaw właściwości układ dynamiczny. **Układ dynamiczny** sekcji w oknie właściwości zawiera właściwości **przenoszenie typu**, **typ ustalania rozmiaru**i, w zależności od wartości wybrane do tych właściwości określone właściwości, które określają, ile formanty przenieść lub zmienić rozmiar. **Typ przenoszenia** Określa, jak formant zostanie przesunięty wraz ze zmianą rozmiaru okna dialogowego; **Typ ustalania rozmiaru** określa sposób zmieni się rozmiar kontrolki wraz ze zmianą rozmiaru okna dialogowego. **Typ przenoszenia** i **typ ustalania rozmiaru** może być **poziome**, **pionowy**, **zarówno**, lub **Brak** w zależności od wymiarów, które chcesz zmienić dynamicznie. Poziomy jest wymiarem X; Pionowe jest kierunku Y.  
  
3.  Jeśli chcesz kontrolować, takie jak przycisk o stałym rozmiarze i pozostanie w miejscu, w prawym dolnym rogu, co jest typowe dla **OK** lub **anulować** przycisków, ustaw **typ ustalania rozmiaru** do  **Brak**i ustaw **przenoszenie typu** do **zarówno**. Dla **przenoszenie X** i **przenoszenie Y** wartości w obszarze **przenoszenie typu**, ustaw 100% powoduje formant pozostanie stała odległość od dołu prawym narożniku.  
  
     ![Układ dynamiczny](../mfc/media/mfcdynamiclayout1.png "mfcdynamiclayout1")  
  
4.  Załóżmy, że masz formant, który chcesz powiększyć rozszerza okna dialogowego. Zazwyczaj użytkownik może rozszerzyć okna dialogowego, aby rozwinąć wielowierszowe pole edycji, aby zwiększyć rozmiar obszaru tekstu lub ich może rozszerzyć kontrolkę listy, aby wyświetlić więcej danych. W tym przypadku należy ustawić **typ ustalania rozmiaru** zarówno i ustaw **przenoszenie typu** None. Następnie ustaw **X zmiany rozmiaru** i **Y zmiany rozmiaru** wartości do 100.  
  
     ![Układ dynamiczny ustawienia](../mfc/media/mfcdynamiclayout2.png "mfcdynamiclayout2")  
  
5.  Wypróbuj inne wartości, które może być uzasadnione dla formantów. Okno dialogowe z jednowierszowe pole tekstowe może być **typ ustalania rozmiaru** ustawioną **poziome** , na przykład.  
  
### <a name="setting-dynamic-layout-properties-programmatically"></a>Programowane Ustawianie właściwości układ dynamiczny  
 Opisane w poprzedniej procedurze jest przydatne w przypadku określania właściwości układ dynamiczny dla okna dialogowego w czasie projektowania, ale jeśli chcesz kontrolować układ dynamiczny w czasie wykonywania, układ dynamiczny właściwości można ustawić programowo.  
  
##### <a name="to-set-dynamic-layout-properties-programmatically"></a>Programowo ustawiać właściwości układ dynamiczny  
  
1.  Znaleźć lub utworzyć miejsce, w którym chcesz określić układ dynamiczny dla okna dialogowego kod implementacji klasy okien dialogowych. Na przykład możesz chcieć takich jak dodawanie metody `AdjustLayout` w oknie dialogowym i połączenie go z miejsc, gdzie układ musi zostać zmienione. Najpierw może to wywołać, z konstruktora lub po wprowadzeniu zmian do okna dialogowego.  
  
2.  Okno dialogowe, wywołaj [GetDynamicLayout](../mfc/reference/cwnd-class.md#getdynamiclayout), metody klasy CWnd. GetDynamicLayout zwraca wskaźnik do obiektu CMFCDynamicLayout.  
  
 ```  
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();

 ```  
  
3.  Dla pierwszego formantu, do której chcesz dodać dynamicznego zachowania, użyj metody statyczne układ dynamiczny klasy można utworzyć [MoveSettings](../mfc/reference/cmfcdynamiclayout-class.md#movesettings_structure) struktury, który koduje sposób należy dostosować formantu. Aby to zrobić, pierwszy wybór odpowiedniej metody statycznej: [CMFCDynamicLayout::MoveHorizontal](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontal), [CMFCDynamicLayout::MoveVertical](../mfc/reference/cmfcdynamiclayout-class.md#movevertical), [CMFCDynamicLayout::MoveNone](../mfc/reference/cmfcdynamiclayout-class.md#movenone), lub [CMFCDynamicLayout::MoveHorizontalAndVertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical). Należy przekazać w procentach aspekty poziomej lub pionowej przesunięcia. Te metody statyczne wszystkich zwraca nowo utworzony obiekt MoveSettings, który służy do określania zachowania przenoszenia formantu.  
  
     Należy pamiętać o tym, której przenieść 100 oznacza dokładnie jako okna dialogowego zmiany rozmiaru, co powoduje, że krawędzią formantu pozostanie stała odległość od nowej granicy.  
  
 ```  
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);

 ```  
  
4.  Tak samo postąpić zachowania rozmiar, który używa [SizeSettings](../mfc/reference/cmfcdynamiclayout-class.md#sizesettings_structure) typu. Na przykład aby określić, że formant nie ulega zmianie rozmiaru, gdy zmienia rozmiar okna dialogowego, należy użyć poniższego kodu:  
  
 ```  
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();

 ```  
  
5.  Dodawanie formantu do Menedżera układ dynamiczny przy użyciu [CMFCDynamicLayout::AddItem](../mfc/reference/cmfcdynamiclayout-class.md#additem) metody. Istnieją dwa przeciążenia dla różnych sposobów określania żądanego formantu. Wyższy uchwytu okna dla formantu (HWND), a druga ma identyfikator formantu.  
  
 ```  
    dynamicLayout->AddItem(hWndControl,
    moveSettings,
    sizeSettings);

 ```  
  
6.  Należy powtórzyć dla każdego formantu, który musi zostać przeniesiona lub zmiany rozmiaru.  
  
7.  Jeśli to konieczne, można użyć [CMFCDynamicLayout::HasItem](../mfc/reference/cmfcdynamiclayout-class.md#hasitem) metodę, aby określić, czy formant jest już na liście kontrolek narażone na zmiany układu dyamic, lub [CMFCDynamicLayout::IsEmpty](../mfc/reference/cmfcdynamiclayout-class.md#isempty) Metoda do ustalenia, czy są wszystkie formanty, które mogą ulec zmianom.  
  
8.  Aby włączyć układu okna dialogowego, należy wywołać [CWnd::EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) metody.  
  
 ```  
    pDialog->EnableDynamicLayout(TRUE);

 ```  
  
9. Następnym razem, użytkownik zmienia rozmiar okna dialogowego [CMFCDynamicLayout::Adjust](../mfc/reference/cmfcdynamiclayout-class.md#adjust) wywoływana jest metoda, która faktycznie stosuje ustawienia.  
  
10. Jeśli chcesz wyłączyć układ dynamiczny, wywołanie [CWnd::EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) z `FALSE` jak w przypadku `bEnabled` parametru.  
  
 ```  
    pDialog->EnableDynamicLayout(FALSE);

 ```  
  
##### <a name="to-set-the-dynamic-layout-programmatically-from-a-resource-file"></a>Aby ustawić układ dynamiczny programowo z pliku zasobów  
  
1.  Użyj [CMFCDynamicLayout::MoveHorizontalAndVertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical) metodę, aby określić nazwę zasobu w pliku skryptu odpowiednich zasobów (plik .rc), który określa układ dynamiczny informacje, jak w poniższym przykładzie:  
  
 ```  
    dynamicLayout->LoadResource("IDD_DIALOG1");

 ```  
  
     Zasób o nazwie musi odwoływać się okno dialogowe, który zawiera informacje o układzie w formie AFX_DIALOG_LAYOUT wpis w pliku zasobów, jak w poniższym przykładzie:  
  
 "" * / / / * / / * / / AFX_DIALOG_LAYOUT * / /  
 
    IDD_MFCAPPLICATION1_DIALOG AFX_DIALOG_LAYOUT  
    ROZPOCZNIJ OD 0X0000, 0X6400, 0X0028, 0X643C, 0X0028  
    END 
 
    IDD_DIALOG1 AFX_DIALOG_LAYOUT  
    ROZPOCZNIJ OD 0X0000, 0X6464, 0X6464, 0X0000, 0X0000, 0X6464, 0X0000, 0X0000, 0X0000  
 
    END 
 ```  
  
## See Also  
 [CMFCDynamicLayout Class](../mfc/reference/cmfcdynamiclayout-class.md)   
 [Control Classes](../mfc/control-classes.md)   
 [Dialog Box Classes](../mfc/dialog-box-classes.md)   
 [Dialog Editor](../windows/dialog-editor.md)

