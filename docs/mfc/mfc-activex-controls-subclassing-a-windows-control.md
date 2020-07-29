---
title: 'Formanty MFC ActiveX: tworzenie podklasy formantu okna'
ms.date: 09/12/2018
f1_keywords:
- precreatewindow
- IsSubclassed
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- subclassing
- DoSuperclassPaint method [MFC]
- subclassing Windows controls
- subclassing, Windows controls
- reflected messages, in ActiveX controls
- PreCreateWindow method, overriding
- MFC ActiveX controls [MFC], subclassed controls
- MFC ActiveX controls [MFC], creating
- IsSubclassed method [MFC]
ms.assetid: 3236d4de-401f-49b7-918d-c84559ecc426
ms.openlocfilehash: 354cd1cac5db775ea56cb5215a8528bdfe9ac5ab
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225010"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>Formanty MFC ActiveX: tworzenie podklasy formantu okna

W tym artykule opisano proces podklasy typowej kontroli systemu Windows w celu utworzenia kontrolki ActiveX. Podklasa istniejącej kontrolki systemu Windows jest szybkim sposobem tworzenia kontrolki ActiveX. Nowa kontrolka będzie miała możliwość działania w podklasy kontrolce systemu Windows, takich jak malowanie i reagowanie na kliknięcia myszą. Przykładowy [przycisk](../overview/visual-cpp-samples.md) kontrolek ActiveX MFC jest przykładem podklasy kontrolki systemu Windows.

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [kontrolki ActiveX](activex-controls.md).

Aby podtworzyć podklasę kontrolki systemu Windows, wykonaj następujące zadania:

- [Przesłoń funkcje składowe IsSubclassedControl i PreCreateWindow elementu COleControl](#_core_overriding_issubclassedcontrol_and_precreatewindow)

- [Modyfikowanie funkcji składowej OnDraw](#_core_modifying_the_ondraw_member_function)

- [Obsłuż wszystkie komunikaty kontrolek ActiveX (OCM) odzwierciedlone na kontrolce](#_core_handling_reflected_window_messages)

   > [!NOTE]
   > Większość tej pracy jest wykonywana przez kreatora kontrolek ActiveX w przypadku wybrania opcji formant, który ma zostać podklasą, przy użyciu listy rozwijanej **Wybieranie klasy okna nadrzędnego** na stronie **Ustawienia kontroli** .

## <a name="overriding-issubclassedcontrol-and-precreatewindow"></a><a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a>Zastępowanie IsSubclassedControl i PreCreateWindow

Aby przesłonić `PreCreateWindow` i `IsSubclassedControl` dodać następujące wiersze kodu do **`protected`** sekcji deklaracji klasy kontrolki:

[!code-cpp[NVC_MFC_AxSub#1](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]

W pliku implementacji formantu (. CPP) Dodaj następujące wiersze kodu, aby zaimplementować dwie przesłonięte funkcje:

[!code-cpp[NVC_MFC_AxSub#2](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]

Zwróć uwagę, że w tym przykładzie formant przycisku systemu Windows jest określony w `PreCreateWindow` . Jednak wszystkie standardowe formanty systemu Windows mogą być podklasy. Aby uzyskać więcej informacji na temat standardowych formantów systemu Windows, zobacz [Controls](controls-mfc.md).

Podczas tworzenia podklasy kontrolki systemu Windows, możesz określić konkretny styl okna (WS_) lub flagi rozszerzonego stylu okna (WS_EX_), które mają być używane w tworzeniu okna kontrolki. Możesz ustawić wartości tych parametrów w `PreCreateWindow` funkcji składowej, modyfikując `cs.style` `cs.dwExStyle` pola struktury i. Modyfikacje tych pól należy wykonać przy użyciu operacji **lub** , aby zachować domyślne flagi, które są ustawiane przez klasę `COleControl` . Na przykład, Jeśli kontrolka jest podklasą kontrolki BUTTON i chcesz, aby kontrolka była wyświetlana jako pole wyboru, Wstaw następujący wiersz kodu do implementacji elementu `CSampleCtrl::PreCreateWindow` , przed instrukcją Return:

[!code-cpp[NVC_MFC_AxSub#3](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]

Ta operacja dodaje flagę BS_CHECKBOX stylu, pozostawiając domyślną flagę stylu (WS_CHILD) klasy `COleControl` bez zmian.

## <a name="modifying-the-ondraw-member-function"></a><a name="_core_modifying_the_ondraw_member_function"></a>Modyfikowanie funkcji składowej OnDraw

Jeśli chcesz, aby formant podklasy miał taki sam wygląd jak odpowiadający mu formant systemu Windows, `OnDraw` funkcja członkowska kontrolki powinna zawierać tylko wywołanie `DoSuperclassPaint` funkcji składowej, jak w poniższym przykładzie:

[!code-cpp[NVC_MFC_AxSub#4](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]

`DoSuperclassPaint`Funkcja członkowska zaimplementowana przez `COleControl` program używa procedury okna kontrolki systemu Windows do narysowania kontrolki w określonym kontekście urządzenia w obrębie prostokąta ograniczenia. Formant jest widoczny, nawet gdy nie jest aktywny.

> [!NOTE]
> `DoSuperclassPaint`Funkcja członkowska będzie działać tylko z tymi typami formantów, które zezwalają na przekazywanie kontekstu urządzenia jako *wParam* komunikatu WM_PAINT. Obejmuje to niektóre standardowe formanty systemu Windows, takie jak pasek przewijania i przycisk oraz wszystkie typowe kontrolki. W przypadku formantów, które nie obsługują tego zachowania, należy podać własny kod, aby prawidłowo wyświetlić nieaktywną kontrolkę.

## <a name="handling-reflected-window-messages"></a><a name="_core_handling_reflected_window_messages"></a>Obsługa komunikatów okna odbitego

Formanty systemu Windows zazwyczaj wysyłają niektóre komunikaty okna do okna nadrzędnego. Niektóre z tych komunikatów, takie jak WM_COMMAND, zapewniają powiadomienie użytkownika o akcji. Inne, takie jak WM_CTLCOLOR, są używane do uzyskiwania informacji z okna nadrzędnego. Kontrolka ActiveX zazwyczaj komunikuje się z oknem nadrzędnym w inny sposób. Powiadomienia są przekazywane przez Wyzwalanie zdarzeń (wysyłanie powiadomień o zdarzeniach), a informacje o kontenerze sterowania są uzyskiwane przez uzyskanie dostępu do właściwości otoczenia kontenera. Ponieważ te techniki komunikacji istnieją, kontenery kontrolek ActiveX nie mogą przetwarzać żadnych komunikatów okna wysyłanych przez formant.

Aby uniemożliwić odbiór komunikatów okna wysyłanych przez formant systemu Windows z podklasą, program `COleControl` tworzy dodatkowe okno służące jako element nadrzędny kontrolki. To dodatkowe okno zwane "reflektorem" jest tworzone tylko dla formantu ActiveX, który jest podklasą kontrolki systemu Windows i ma ten sam rozmiar i położenie, jak okno sterowania. Okno reflektora przechwytuje niektóre komunikaty okna i wysyła je z powrotem do kontrolki. Kontrolka, w procedurze okna, może następnie przetwarzać te odbite komunikaty przez podejmowanie akcji odpowiednich dla kontrolki ActiveX (na przykład wyzwolenie zdarzenia). Aby wyświetlić listę przechwyconych komunikatów systemu Windows i odpowiadających im wiadomości, zobacz [identyfikatory komunikatów okien odbitej](reflected-window-message-ids.md) .

Kontener formantów ActiveX może być zaprojektowany w celu przeprowadzenia odbicia komunikatu, eliminując konieczność `COleControl` tworzenia okna reflektora i zmniejszania obciążenia w czasie wykonywania dla podklasy formantu systemu Windows. `COleControl`wykrywa, czy kontener obsługuje tę funkcję, sprawdzając, czy Właściwość otoczenia MessageReflect ma wartość **true**.

Aby obsłużyć komunikat odbitego okna, Dodaj wpis do mapy komunikatów kontrolki i zaimplementuj funkcję procedury obsługi. Ponieważ wiadomości odbite nie są częścią standardowego zestawu komunikatów zdefiniowanych przez system Windows, Widok klasy nie obsługuje dodawania takich programów obsługi komunikatów. Nietrudno jest jednak dodać procedurę obsługi ręcznie.

Aby dodać procedurę obsługi komunikatów dla komunikatu odbitego okna, ręcznie wykonaj następujące czynności:

- W klasie Control. Plik H, zadeklaruj funkcję procedury obsługi. Funkcja powinna mieć typ zwracany **LRESULT** i dwa parametry z odpowiednio typami **wParam** i **lParam**. Na przykład:

   [!code-cpp[NVC_MFC_AxSub#5](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]
    [!code-cpp[NVC_MFC_AxSub#6](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]

- W klasie Control. Plik CPP Dodaj wpis ON_MESSAGE do mapy komunikatów. Parametry tego wpisu powinny być identyfikatorem komunikatu i nazwą funkcji obsługi. Na przykład:

   [!code-cpp[NVC_MFC_AxSub#7](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]

- Również w. CPP plik, zaimplementuj `OnOcmCommand` funkcję członkowską, aby przetworzyć komunikat odbity. Parametry *wParam* i *lParam* są takie same jak w przypadku oryginalnego komunikatu okna.

Aby zapoznać się z przykładem sposobu przetwarzania komunikatów odbitych, zapoznaj się z [przyciskiem](../overview/visual-cpp-samples.md)Przykładowy formant ActiveX MFC. Zademonstrowano `OnOcmCommand` procedurę obsługi, która wykrywa BN_CLICKED kod powiadomienia i reaguje przez wyzwolenie (wysyłanie) `Click` zdarzenia.

## <a name="see-also"></a>Zobacz także

[Kontrolki ActiveX MFC](mfc-activex-controls.md)
