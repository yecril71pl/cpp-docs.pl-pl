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
ms.openlocfilehash: ccebbad22be92b84fa2fd84434f788484d332cce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376000"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>Formanty MFC ActiveX: tworzenie podklasy formantu okna

W tym artykule opisano proces podklasyfikowania wspólnego formantu systemu Windows w celu utworzenia formantu ActiveX. Podklasyfikowanie istniejącego formantu systemu Windows to szybki sposób na opracowanie formantu ActiveX. Nowy formant będzie miał możliwości podklasyfikowanego formantu systemu Windows, takie jak malowanie i reagowanie na kliknięcia myszą. Przykładowe formanty MFC ActiveX [BUTTON](../overview/visual-cpp-samples.md) jest przykładem podklasy formantu systemu Windows.

>[!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [ActiveX Controls](activex-controls.md).

Aby podklasyfikować formant systemu Windows, wykonaj następujące zadania:

- [Zastępowanie funkcji członkowskich IsSubclassedControl i PreCreateWindow cOleControl](#_core_overriding_issubclassedcontrol_and_precreatewindow)

- [Modyfikowanie funkcji elementu członkowskiego OnDraw](#_core_modifying_the_ondraw_member_function)

- [Obsługa wszelkich komunikatów sterujących ActiveX (OCM) odbitych do](#_core_handling_reflected_window_messages)

   > [!NOTE]
   > Wiele z tej pracy jest wykonywane przez Kreatora sterowania ActiveX, jeśli wybierzesz formant do podklasy przy użyciu listy rozwijanej **Wybierz klasę okna nadrzędnego** na stronie **Ustawienia sterowania.**

## <a name="overriding-issubclassedcontrol-and-precreatewindow"></a><a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a>Zastępowanie IsSubclassedControl i PreCreateWindow

Aby zastąpić `PreCreateWindow` i `IsSubclassedControl`dodać następujące wiersze kodu do **chronionej** sekcji deklaracji klasy kontrolnej:

[!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]

W pliku implementacji formantu (. CPP), dodaj następujące wiersze kodu, aby zaimplementować dwie zastąpione funkcje:

[!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]

Należy zauważyć, że w tym przykładzie `PreCreateWindow`kontrolka przycisku Systemu Windows jest określona w programie . Jednak wszystkie standardowe formanty systemu Windows mogą być podklasyfikowane. Aby uzyskać więcej informacji na temat standardowych formantów systemu Windows, zobacz [Formanty](../mfc/controls-mfc.md).

Podczas podklasy formantu systemu Windows można określić określone flagi stylu okna (WS_) lub rozszerzonego stylu okna (WS_EX_), które mają być używane podczas tworzenia okna formantu. Wartości tych parametrów w `PreCreateWindow` funkcji elementu członkowskiego `cs.style` można `cs.dwExStyle` ustawić, modyfikując pola struktury. Modyfikacje tych pól powinny być dokonywane przy użyciu operacji **OR,** `COleControl`aby zachować domyślne flagi, które są ustawione według klasy . Na przykład jeśli formant jest podklasy button kontroli i chcesz formantu, aby pojawić się `CSampleCtrl::PreCreateWindow`jako pole wyboru, wstawić następujący wiersz kodu do implementacji , przed return instrukcji:

[!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]

Ta operacja dodaje flagę stylu BS_CHECKBOX, pozostawiając domyślną flagę stylu (WS_CHILD) klasy `COleControl` bez zmian.

## <a name="modifying-the-ondraw-member-function"></a><a name="_core_modifying_the_ondraw_member_function"></a>Modyfikowanie funkcji ondraw element członkowski

Jeśli chcesz, aby formant podklasyfikowany zachował taki `OnDraw` sam wygląd jak odpowiedni formant `DoSuperclassPaint` systemu Windows, funkcja elementu członkowskiego formantu powinna zawierać tylko wywołanie funkcji elementu członkowskiego, jak w poniższym przykładzie:

[!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]

Funkcja `DoSuperclassPaint` elementu członkowskiego, `COleControl`zaimplementowana przez program , używa procedury okna formantu systemu Windows do rysowania formantu w określonym kontekście urządzenia w obrębie prostokąta ograniczającego. Dzięki temu formant jest widoczny nawet wtedy, gdy nie jest aktywny.

> [!NOTE]
> Funkcja `DoSuperclassPaint` elementu członkowskiego będzie działać tylko z tymi typami formantów, które umożliwiają przekazywanie kontekstu urządzenia jako *wParam* komunikatu WM_PAINT. Obejmuje to niektóre standardowe formanty systemu Windows, takie jak SCROLLBAR i BUTTON, a także wszystkie typowe formanty. Dla formantów, które nie obsługują tego zachowania, należy podać własny kod, aby poprawnie wyświetlić nieaktywną formant.

## <a name="handling-reflected-window-messages"></a><a name="_core_handling_reflected_window_messages"></a>Obsługa komunikatów okna odbitego

Formanty systemu Windows zazwyczaj wysyłają określone komunikaty okna do okna nadrzędnego. Niektóre z tych komunikatów, takich jak WM_COMMAND, zapewniają powiadomienie o akcji przez użytkownika. Inne, takie jak WM_CTLCOLOR, są używane do uzyskiwania informacji z okna nadrzędnego. Formant ActiveX zwykle komunikuje się z oknem nadrzędnym za pomocą innych środków. Powiadomienia są przekazywane przez wypalania zdarzeń (wysyłanie powiadomień o zdarzeniach), a informacje o kontenerze formantu uzyskuje się przez uzyskanie dostępu do właściwości otoczenia kontenera. Ponieważ istnieją te techniki komunikacji, kontenery kontroli ActiveX nie powinny przetwarzać żadnych komunikatów okna wysyłanych przez formant.

Aby uniemożliwić kontenerowi odbieranie wiadomości okna wysyłanych przez `COleControl` podklasy formantu systemu Windows, tworzy dodatkowe okno, aby służyć jako nadrzędny formantu. To dodatkowe okno, zwane "reflektorem", jest tworzone tylko dla formantu ActiveX, które podklasuje formant systemu Windows i ma taki sam rozmiar i położenie jak okno formantu. Okno reflektora przechwytuje niektóre komunikaty okna i wysyła je z powrotem do formantu. Formant, w swojej procedurze okna, można następnie przetworzyć te komunikaty odzwierciedlenie, podejmując akcje odpowiednie dla activex kontroli (na przykład wypalania zdarzenia). Zobacz [Identyfikatory komunikatów okna odbitego,](../mfc/reflected-window-message-ids.md) aby uzyskać listę przechwyconych wiadomości systemu Windows i odpowiadających im wiadomości odzwierciedlenie.

Kontener formantu ActiveX może być zaprojektowany do wykonywania `COleControl` odbicia wiadomości, eliminując konieczność tworzenia okna reflektora i zmniejszając obciążenie czasu wykonywania dla podklasy formantu systemu Windows. `COleControl`wykrywa, czy kontener obsługuje tę funkcję, sprawdzając właściwość otoczenia MessageReflect o wartości **TRUE**.

Aby obsłużyć komunikat okna odbite, należy dodać wpis do mapy komunikatów kontrolnych i zaimplementować funkcję obsługi. Ponieważ komunikaty odzwierciedlenie nie są częścią standardowego zestawu komunikatów zdefiniowanych przez system Windows, Widok klasy nie obsługuje dodawania takich programów obsługi wiadomości. Jednak nie jest trudne do dodania obsługi ręcznie.

Aby ręcznie dodać program obsługi wiadomości dla odbitej wiadomości okna, wykonaj następujące czynności:

- W klasie kontrolnej . H, zadeklaruj funkcję obsługi. Funkcja powinna mieć typ zwracany **LRESULT** i dwa parametry, odpowiednio z typami **WPARAM** i **LPARAM.** Przykład:

   [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]

- W klasie kontrolnej . CPP, dodaj ON_MESSAGE wpis do mapy wiadomości. Parametry tego wpisu powinny być identyfikator wiadomości i nazwa funkcji obsługi. Przykład:

   [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]

- Również w . CPP, zaimplementuj `OnOcmCommand` funkcję elementu członkowskiego, aby przetworzyć odzwierciedloną wiadomość. Parametry *wParam* i *lParam* są takie same jak parametry oryginalnego okna.

Na przykład sposobu przetwarzania odzwierciedlenie wiadomości, zapoznaj się z przykładowym przykładowym elementem sterującym MFC ActiveX [BUTTON](../overview/visual-cpp-samples.md). Demonstruje `OnOcmCommand` program obsługi, który wykrywa BN_CLICKED kod powiadomienia i odpowiada przez `Click` wypalania (wysyłanie) zdarzenia.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)
