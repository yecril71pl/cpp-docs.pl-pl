---
title: Układ dynamiczny
ms.date: 09/09/2019
ms.assetid: 8598cfb2-c8d4-4f5a-bf2b-59dc4653e042
ms.openlocfilehash: 1b0d035d3c551fd309d515ccb8b22159218c1b0a
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "70907552"
---
# <a name="dynamic-layout"></a>Układ dynamiczny

Za pomocą MFC w programie Visual Studio 2015 można utworzyć okna dialogowe, które użytkownik może zmienić rozmiaru, i można kontrolować sposób, w jaki układ dostosowuje się do zmiany rozmiaru. Na przykład możesz dołączyć przyciski u dołu okna dialogowego do dolnej krawędzi, aby zawsze znajdowały się na dole. Można również skonfigurować pewne kontrolki, takie jak ListBox, editboxes i pola tekstowe, aby rozwinąć, gdy użytkownik rozwija okno dialogowe.

## <a name="specifying-dynamic-layout-settings-for-an-mfc-dialog-box"></a>Określanie ustawień układu dynamicznego dla okna dialogowego MFC

Gdy użytkownik zmienia rozmiar okna dialogowego, kontrolki w oknie dialogowym mogą zmieniać rozmiar lub poruszać się w kierunkach X i Y. Zmiana rozmiaru lub położenia kontrolki, gdy użytkownik zmienia rozmiar okna dialogowego nazywanego układem dynamicznym. Na przykład po zmianie rozmiaru okna dialogowego można wykonać następujące czynności:

![Okna dialogowego przed ponownym rozmiarem.](../mfc/media/mfcdynamiclayout4.png "Okna dialogowego przed ponownym rozmiarem.")

Po zmianie rozmiaru obszar ListBox zostanie powiększony, aby pokazać więcej elementów, a przyciski są przenoszone wraz z prawym dolnym rogu:

![Po zmianie rozmiaru okna dialogowego.](../mfc/media/mfcdynamiclayout5.png "Po zmianie rozmiaru okna dialogowego.")

Układ dynamiczny można kontrolować, określając szczegóły dla każdej kontrolki w edytorze zasobów w środowisku IDE, lub można to zrobić programowo, uzyskując dostęp do obiektu `CMFCDynamicLayout` dla konkretnej kontrolki i ustawiając właściwości.

### <a name="setting-dynamic-layout-properties-in-the-resource-editor"></a>Ustawianie właściwości układu dynamicznego w edytorze zasobów

Można ustawić zachowanie układu dynamicznego dla okna dialogowego bez konieczności pisania kodu przy użyciu edytora zasobów.

#### <a name="to-set-dynamic-layout-properties-in-the-resource-editor"></a>Aby ustawić właściwości układu dynamicznego w edytorze zasobów

1. Przy otwartym projekcie MFC Otwórz okno dialogowe, z którym chcesz korzystać w edytorze okien dialogowych.

   ![Otwórz okno dialogowe w edytorze zasobów.](../mfc/media/mfcdynamiclayout3.png "Otwórz okno dialogowe w edytorze zasobów.")

1. Zaznacz formant i w oknie **Właściwości** (w **Widok klasy**) ustaw jego właściwości układu dynamicznego. Sekcja **układ dynamiczny** w oknie **Właściwości** zawiera właściwości **przenoszenia typu**, **Typ zmiany**i, w zależności od wartości wybranych dla tych właściwości, określonych właściwości, które definiują przenoszenie lub Zmień rozmiar. **Typ przenoszenia** określa sposób przenoszenia kontrolki, gdy zmienia się rozmiar okna dialogowego; **Typ rozmiaru** określa sposób zmiany rozmiaru kontrolki, ponieważ rozmiar okna dialogowego został zmieniony. Typ **przenoszonego** typu i **typu zmiany** mogą być **poziome**, **pionowe**, **oba**lub **nie** , w zależności od wymiarów, które mają być dynamicznie zmieniane. Pozioma to wymiar X; Pionowa to kierunek Y.

1. Jeśli chcesz, aby kontrolka, taka jak przycisk, ma stały rozmiar i pozostać w miejscu w prawym dolnym rogu, tak jak w przypadku przycisków **OK** lub **Anuluj** , ustaw **Typ zmiany** na **Brak**i ustaw **Typ przesunięcia** na **oba**. Dla **przesuwanych wartości X** i **przeniesień Y** w obszarze **Typ przeniesienia**Ustaw 100%, aby formant miał stałą odległość od prawego dolnego rogu.

   ![Układ dynamiczny](../mfc/media/mfcdynamiclayout1.png "Układ dynamiczny")

1. Załóżmy, że masz również formant, który chcesz rozwinąć, gdy okno dialogowe zostanie rozwinięte. Zazwyczaj użytkownik może rozwinąć okno dialogowe, aby rozwinąć wielowierszowe EditBox w celu zwiększenia rozmiaru obszaru tekstowego lub rozszerzyć formant listy, aby wyświetlić więcej danych. W takim przypadku należy ustawić **Typ zmiany typu** na oba i ustawić **Typ przesunięcia** na brak. Następnie ustaw wartości właściwości **Rozmiar X** i **rozmiar Y** na 100.

   ![Ustawienia układu dynamicznego](../mfc/media/mfcdynamiclayout2.png "Ustawienia układu dynamicznego")

1. Eksperymentuj z innymi wartościami, które mogą mieć sens dla kontrolek. Okno dialogowe z jednowierszowym polem tekstowym może mieć ustawiony **Typ zmiany** **poziomej** na na przykład.

### <a name="setting-dynamic-layout-properties-programmatically"></a>Programowe Ustawianie właściwości układu dynamicznego

Poprzednia procedura jest przydatna do określania właściwości układu dynamicznego okna dialogowego w czasie projektowania, ale jeśli chcesz kontrolować układ dynamiczny w czasie wykonywania, możesz programowo ustawiać dynamiczne właściwości układu.

#### <a name="to-set-dynamic-layout-properties-programmatically"></a>Aby programowo ustawić właściwości układu dynamicznego

1. Znajdź lub Utwórz miejsce w kodzie implementacji klasy okna dialogowego, w którym chcesz określić układ dynamiczny okna dialogowego. Na przykład możesz chcieć dodać metodę, taką jak `AdjustLayout` w oknie dialogowym, i wywoływać ją z miejsc, w których układ musi zostać zmieniony. Użytkownik może najpierw wywołać ten program z konstruktora lub po wprowadzeniu zmian w oknie dialogowym.

1. Dla okna dialogowego Wywołaj [GetDynamicLayout](../mfc/reference/cwnd-class.md#getdynamiclayout), metodę klasy `CWnd`. `GetDynamicLayout` zwraca wskaźnik do obiektu `CMFCDynamicLayout`.

    ```cpp
    CMFCDynamicLayout* dynamicLayout = pDialog->GetDynamicLayout();
    ```

1. W przypadku pierwszej kontrolki, do której ma zostać dodane dynamiczne zachowanie, użyj metod statycznych klasy układu dynamicznego, aby utworzyć strukturę [MoveSettings](../mfc/reference/cmfcdynamiclayout-class.md#movesettings_structure) , która koduje sposób, w jaki formant powinien zostać dostosowany. W tym celu należy najpierw wybrać odpowiednią metodę statyczną: [CMFCDynamicLayout:: MoveHorizontal](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontal), [CMFCDynamicLayout:: MoveVertical](../mfc/reference/cmfcdynamiclayout-class.md#movevertical), [CMFCDynamicLayout:: MoveNone](../mfc/reference/cmfcdynamiclayout-class.md#movenone)lub [CMFCDynamicLayout:: MoveHorizontalAndVertical ](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical). Należy przekazać wartość procentową dla aspektów poziomych i/lub pionowych przenoszenia. Wszystkie te metody statyczne zwracają nowo utworzony obiekt MoveSettings, którego można użyć do określenia zachowania przenoszenia kontrolki.

   Należy pamiętać, że 100 oznacza przeniesieniu dokładnie tak, jak zmienia się rozmiar okna dialogowego, co powoduje, że krawędź kontrolki pozostaje stała odległość od nowego obramowania.

    ```cpp
    MoveSettings moveSettings = CMFCDynamicLayout::MoveHorizontal(100);
    ```

1. Wykonaj tę samą czynność dla zachowania rozmiaru, który używa typu [SizeSettings —](../mfc/reference/cmfcdynamiclayout-class.md#sizesettings_structure) . Na przykład, aby określić, że formant nie zmienia rozmiaru w przypadku zmiany rozmiaru okna dialogowego, użyj następującego kodu:

    ```cpp
    SizeSettings sizeSettings = CMFCDynamicLayout::SizeNone();
    ```

1. Dodaj formant do dynamicznego Menedżera układu przy użyciu metody [CMFCDynamicLayout:: AddItem](../mfc/reference/cmfcdynamiclayout-class.md#additem) . Istnieją dwa przeciążenia dla różnych sposobów określania żądanego formantu. Jeden przyjmuje uchwyt okna kontrolki (HWND), a drugi Pobiera identyfikator formantu.

    ```cpp
    dynamicLayout->AddItem(hWndControl,
    moveSettings,
    sizeSettings);
    ```

1. Powtórz tę czynność dla każdej kontrolki, która musi zostać przeniesiona lub zmieniono jej rozmiar.

1. W razie potrzeby można użyć metody [CMFCDynamicLayout:: HasItem](../mfc/reference/cmfcdynamiclayout-class.md#hasitem) , aby określić, czy kontrolka znajduje się już na liście formantów podlegających zmianom układu dynamicznego, czy też [CMFCDynamicLayout:: IsEmpty](../mfc/reference/cmfcdynamiclayout-class.md#isempty) , aby określić, czy istnieją jakieś kontrolki, które mogą ulec zmianom.

1. Aby włączyć układ okna dialogowego, wywołaj metodę [CWnd:: EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) .

    ```cpp
    pDialog->EnableDynamicLayout(TRUE);
    ```

1. Gdy następnym razem użytkownik zmieni rozmiar okna dialogowego, wywoływana jest metoda [CMFCDynamicLayout:: Dostosowywanie](../mfc/reference/cmfcdynamiclayout-class.md#adjust) , która rzeczywiście stosuje ustawienia.

1. Jeśli chcesz wyłączyć układ dynamiczny, wywołaj [CWnd:: EnableDynamicLayout](../mfc/reference/cwnd-class.md#enabledynamiclayout) z **wartością false** jako dla parametru *bEnabled* .

    ```cpp
    pDialog->EnableDynamicLayout(FALSE);
    ```

#### <a name="to-set-the-dynamic-layout-programmatically-from-a-resource-file"></a>Aby programowo ustawić układ dynamiczny z pliku zasobów

1. Użyj metody [CMFCDynamicLayout:: MoveHorizontalAndVertical](../mfc/reference/cmfcdynamiclayout-class.md#movehorizontalandvertical) , aby określić nazwę zasobu w odpowiednim pliku skryptu zasobu (plik. RC), który określa dynamiczne informacje o układzie, jak w poniższym przykładzie:

    ```cpp
    dynamicLayout->LoadResource("IDD_DIALOG1");
    ```

   Nazwany zasób musi odwoływać się do okna dialogowego zawierającego informacje o układzie w postaci wpisu **AFX_DIALOG_LAYOUT** w pliku zasobów, jak w poniższym przykładzie:

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
[Dynamiczny układ okien dla MFC w Visual C++ 2015](https://mariusbancila.ro/blog/2015/07/27/dynamic-dialog-layout-for-mfc-in-visual-c-2015/)
