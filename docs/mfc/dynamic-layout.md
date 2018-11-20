---
title: Układ dynamiczny
ms.date: 11/19/2018
ms.assetid: 8598cfb2-c8d4-4f5a-bf2b-59dc4653e042
ms.openlocfilehash: 396aad5b33a00021ddb5c1143c1d15c130e97eaa
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175694"
---
# <a name="dynamic-layout"></a>Układ dynamiczny

MFC w programie Visual Studio 2015 można utworzyć okien dialogowych, które użytkownik może zmienić rozmiar i kontrolować sposób, w jaki układ dostosowuje się do zmiany rozmiaru. Na przykład można dołączyć przycisków w dolnej części okna dialogowego do dolnej krawędzi, dzięki czemu zawsze pozostają, u dołu. Niektóre formanty, takie jak listy pól, editboxes i pól tekstowych można też skonfigurować rozszerzenia użytkownik rozwija okna dialogowego.

## <a name="specifying-dynamic-layout-settings-for-an-mfc-dialog-box"></a>Określanie ustawień układ dynamiczny dla okna dialogowego MFC

Gdy użytkownik zmienia rozmiar okna dialogowego, formantów w oknie dialogowym zmienić rozmiar lub przenieść w kierunku X i Y. Zmiana rozmiaru lub położenia kontrolki, gdy użytkownik zmienia rozmiar okna dialogowego nosi nazwę układ dynamiczny. Na przykład Oto okna dialogowego zanim zmiany rozmiaru:

![Okno dialogowe przed zmieniany. ](../mfc/media/mfcdynamiclayout4.png "Okno dialogowe przed zmieniany.")

Po zmianie rozmiaru, w obszarze pole listy zostaje zwiększona do Pokaż więcej elementów i przyciski są przenoszone razem z prawym dolnym rogu:

![Okno dialogowe po zmieniany. ](../mfc/media/mfcdynamiclayout5.png "Okna dialogowego po zmieniany.")

Układ dynamiczny można kontrolować, określając szczegóły dla każdego formantu w edytorze zasobów w środowisku IDE lub można zrobić w sposób programowy dostęp do `CMFCDynamicLayout` obiektu dla określonej kontrolki i ustawiając właściwości.

### <a name="setting-dynamic-layout-properties-in-the-resource-editor"></a>Ustawianie właściwości układ dynamiczny w edytorze zasobów

Możesz ustawić zachowanie układ dynamiczny dla okna dialogowego, bez konieczności pisania kodu, za pomocą edytora zasobów.

#### <a name="to-set-dynamic-layout-properties-in-the-resource-editor"></a>Aby ustawić właściwości dynamicznego układu w edytorze zasobów

1. Otwórz projekt MFC Otwórz okno dialogowe, które chcesz pracować w edytorze okien dialogowych.

   ![W edytorze zasobów, należy otworzyć okno dialogowe. ](../mfc/media/mfcdynamiclayout3.png "Otwórz okno dialogowe w edytorze zasobów.")

1. Wybierz kontrolkę, a następnie w oknie właściwości ustaw jego właściwości układ dynamiczny. **Układ dynamiczny** sekcji w oknie dialogowym właściwości zawiera właściwości **Typ przenoszenia**, **typ ustalania rozmiaru**i w zależności od wartości wybranych dla tych właściwości określone właściwości, które określają, ile formantów przenieść lub zmienić rozmiar. **Typ przenoszenia** określa sposobu przenoszenia kontrolki wraz ze zmianą rozmiaru okna dialogowego; **Typ ustalania rozmiaru** Określa, jak zmieni się rozmiar kontrolki wraz ze zmianą rozmiaru okna dialogowego. **Typ przenoszenia** i **typ ustalania rozmiaru** może być **poziomy**, **pionowe**, **zarówno**, lub **Brak**w zależności od wymiarów, które mają być dynamicznie zmieniać. Wykres poziomy jest wymiar X; W pionie jest kierunku Y.

1. Jeśli chcesz, aby kontrolce, takiej jak przycisk o stałym rozmiarze i pozostają w miejscu, w prawym dolnym rogu, w jakim są typowe dla **OK** lub **anulować** przyciski, ustaw **typ ustalania rozmiaru** do  **Brak**i ustaw **Typ przenoszenia** do **zarówno**. Dla **przenoszenie X** i **przenoszenie Y** wartości w obszarze **Typ przenoszenia**, ustaw 100%, aby spowodować, że formant pozostanie stała odległość od dołu rogu.

   ![Układ dynamiczny](../mfc/media/mfcdynamiclayout1.png "układ dynamiczny")

1. Załóżmy, że masz również formant, który ma zostać rozszerzony w miarę rozszerzania okna dialogowego. Zazwyczaj użytkownik może rozszerzyć okna dialogowego, aby rozwinąć wielowierszowe pole edycji, aby zwiększyć rozmiar obszaru tekstu lub może być rozszerzają kontrolkę listy do wyświetlania większej ilości danych. W tym przypadku należy ustawić **typ ustalania rozmiaru** na wartość oba i ustaw **Typ przenoszenia** None. Następnie ustaw **X rozmiaru** i **Y rozmiaru** wartości do 100.

   ![Ustawienia układu dynamicznego](../mfc/media/mfcdynamiclayout2.png "ustawień układ dynamiczny")

1. Wypróbuj inne wartości, które może mieć sens dla kontrolki. Okno dialogowe za pomocą textbox jednego wiersza może mieć **typ ustalania rozmiaru** równa **poziomy** , na przykład.

### <a name="setting-dynamic-layout-properties-programmatically"></a>Programowe Ustawianie właściwości układ dynamiczny

Powyższej procedury przydaje się do określania właściwości układ dynamiczny dla okna dialogowego w czasie projektowania, ale jeśli chcesz kontrolować układ dynamiczny w czasie wykonywania, można programowo ustawić właściwości układ dynamiczny.

#### <a name="to-set-dynamic-layout-properties-programmatically"></a>Aby programowo ustawić właściwości układ dynamiczny

1. Znajdź lub Utwórz miejsce w kodzie implementacji klasy okien dialogowych, które chcesz określić układ dynamiczny dla okna dialogowego. Na przykład możesz chcieć dodać metody takie jak `AdjustLayout` w oknie dialogowym i połączenie go z miejsc, gdzie trzeba zmienić układ. Najpierw może to wywołać, z konstruktora lub po wprowadzeniu zmian do okna dialogowego.

1. Okno dialogowe, można wywołać [GetDynamicLayout](../mfc/reference/cwnd-class.md#getdynamiclayout), Metoda `CWnd` klasy. `GetDynamicLayout` Zwraca wskaźnik do `CMFCDynamicLayout` obiektu.

    ```cpp
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();
    ```

1. Dla pierwszego formantu, do którego chcesz dodać dynamiczne zachowanie, użyj metod statycznych układ dynamiczny klasy do utworzenia [MoveSettings](../mfc/reference/cmfcdynamiclayout-class.md#movesettings_structure) strukturę, która koduje sposób kontrolki powinien zostać dostosowany. Można to zrobić, pierwszy wybór odpowiedniej metody statycznej: [CMFCDynamicLayout::MoveHorizontal](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontal), [CMFCDynamicLayout::MoveVertical](../mfc/reference/cmfcdynamiclayout-class.md#movevertical), [CMFCDynamicLayout::MoveNone](../mfc/reference/cmfcdynamiclayout-class.md#movenone), lub [CMFCDynamicLayout::MoveHorizontalAndVertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical). Należy przekazać w postaci wartości procentowej poziomej lub pionowej aspektów przeniesienie. Te metody statyczne, wszystkie zwraca nowo utworzony obiekt MoveSettings, który służy do określania zachowania przenoszenia formantu.

   Należy pamiętać, że 100 oznacza, że przenoszenie dokładnie tak jak okna dialogowego zmiany rozmiaru, co powoduje, że krawędzi kontrolki na bieżąco Stała odległość od nowej granicy.

    ```cpp
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);
    ```

1. Te same czynności wykonasz zachowania rozmiar, który używa [SizeSettings](../mfc/reference/cmfcdynamiclayout-class.md#sizesettings_structure) typu. Na przykład aby określić, że formant nie ulega zmianie rozmiaru, gdy zmienia rozmiar okna dialogowego, należy użyć następującego kodu:

    ```cpp
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();
    ```

1. Dodaj formant do Menedżera układ dynamiczny, przy użyciu [CMFCDynamicLayout::AddItem](../mfc/reference/cmfcdynamiclayout-class.md#additem) metody. Istnieją dwa przeciążenia dla różnych sposobów określania żądanego formantu. Jedno wykorzystuje formantu uchwyt okna (HWND), a druga pobiera identyfikator kontrolki.

    ```cpp
    dynamicLayout->AddItem(hWndControl,
    moveSettings,
    sizeSettings);
    ```

1. Należy powtórzyć dla każdego formantu, który należy do przeniesienia lub zmiany rozmiaru.

1. Jeśli to konieczne, można użyć [CMFCDynamicLayout::HasItem](../mfc/reference/cmfcdynamiclayout-class.md#hasitem) metodę, aby określić, jeśli formant znajduje się już na liście kontrolek poddane dyamic zmiany układu, lub [CMFCDynamicLayout::IsEmpty](../mfc/reference/cmfcdynamiclayout-class.md#isempty) Metoda określa, czy wszystkie kontrolki, których może ulec zmianie.

1. Aby włączyć układ okna dialogowego, należy wywołać [CWnd::EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) metody.

    ```cpp
    pDialog->EnableDynamicLayout(TRUE);
    ```

1. Następnym razem użytkownik zmienia rozmiar okna dialogowego, [CMFCDynamicLayout::Adjust](../mfc/reference/cmfcdynamiclayout-class.md#adjust) wywoływana jest metoda, która faktycznie stosuje ustawienia.

1. Jeśli chcesz wyłączyć układ dynamiczny, należy wywołać [CWnd::EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) z **FALSE** jak w przypadku *bWłączony* parametru.

    ```cpp
    pDialog->EnableDynamicLayout(FALSE);
    ```

#### <a name="to-set-the-dynamic-layout-programmatically-from-a-resource-file"></a>Aby programowo ustawić układ dynamiczny z pliku zasobów

1. Użyj [CMFCDynamicLayout::MoveHorizontalAndVertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical) metodę, aby określić nazwę zasobu w pliku skryptu odpowiedni zasób (plik .rc), który określa informacje układ dynamiczny, jak w poniższym przykładzie:

    ```cpp
    dynamicLayout->LoadResource("IDD_DIALOG1");
    ```

   Nazwany zasób musi odwoływać się okno dialogowe, które zawiera informacje o układzie w formie **AFX_DIALOG_LAYOUT** wpisu w pliku zasobów, jak w poniższym przykładzie:

    ```RC
    /////////////////////////////////////////////////////////////////////////////
    //
    // AFX_DIALOG_LAYOUT
    //

    IDD_MFCAPPLICATION1_DIALOG AFX_DIALOG_LAYOUT
    BEGIN
    0x0000,
    0x6400,
    0x0028,
    0x643c,
    0x0028
    END

    IDD_DIALOG1 AFX_DIALOG_LAYOUT
    BEGIN
    0x0000,
    0x6464,
    0x0000,
    0x6464,
    0x0000,
    0x0000,
    0x6464,
    0x0000,
    0x0000

    END
    ```

## <a name="see-also"></a>Zobacz także

[Klasa CMFCDynamicLayout](../mfc/reference/cmfcdynamiclayout-class.md)<br/>
[Klasy kontrolek](../mfc/control-classes.md)<br/>
[Klasy okien dialogowych](../mfc/dialog-box-classes.md)<br/>
[Edytor okien dialogowych](../windows/dialog-editor.md)<br/>
[Układ dynamiczny okna dialogowego MFC w programie Visual C++ 2015](https://mariusbancila.ro/blog/2015/07/27/dynamic-dialog-layout-for-mfc-in-visual-c-2015/)
