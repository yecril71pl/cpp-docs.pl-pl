---
title: Dostosowywanie klawiatury i myszy
ms.date: 11/19/2018
helpviewer_keywords:
- customizations [MFC], keyboard and mouse (MFC Extensions)
- keyboard and mouse customizations (MFC Extensions)
ms.assetid: 1f789f1b-5f2e-4b11-b974-e3e2a2e49d82
ms.openlocfilehash: 262555b060f226a86438a2189eda44d83c55d5a2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621504"
---
# <a name="keyboard-and-mouse-customization"></a>Dostosowywanie klawiatury i myszy

MFC zezwala użytkownikowi aplikacji na dostosowywanie sposobu obsługi klawiatury i myszy przez program. Użytkownik może dostosować wprowadzanie z klawiatury, przypisując skróty klawiaturowe do poleceń. Użytkownik może również dostosować dane wejściowe myszy, wybierając polecenie, które ma zostać wykonane, gdy użytkownik kliknie dwukrotnie wewnątrz określonych okien aplikacji. W tym temacie wyjaśniono, jak dostosować dane wejściowe dla aplikacji.

W oknie dialogowym **dostosowanie** użytkownik może zmienić niestandardowe kontrolki myszy i klawiatury. Aby wyświetlić to okno dialogowe, użytkownik wskazuje do **dostosowania** w menu **Widok** , a następnie klika **paski narzędzi i dokowanie**. W oknie dialogowym użytkownik klika kartę **Klawiatura** lub kartę **mysz** .

## <a name="keyboard-customization"></a>Dostosowanie klawiatury

Na poniższej ilustracji przedstawiono kartę **Klawiatura** okna dialogowego **Dostosowywanie** .

![Karta klawiatura w oknie dialogowym Dostosowywanie](../mfc/media/mfcnextkeyboardtab.png "Karta klawiatura w oknie dialogowym Dostosowywanie") <br/>
Karta Dostosowywanie klawiatury

Użytkownik współdziała z kartą klawiatury, aby przypisać do polecenia co najmniej jedno skróty klawiaturowe. Dostępne polecenia są wyświetlane po lewej stronie karty. Użytkownik może wybrać dowolne z dostępnych poleceń z menu. Tylko polecenia menu można kojarzyć ze skrótem klawiaturowym. Po wprowadzeniu nowego skrótu przez użytkownika przycisk **Przypisz** zostanie włączony. Gdy użytkownik kliknie ten przycisk, aplikacja kojarzy wybrane polecenie z tym skrótem.

Wszystkie aktualnie przypisane skróty klawiaturowe są wymienione w polu listy w prawej kolumnie. Użytkownik może również wybrać poszczególne skróty i usunąć je lub zresetować wszystkie mapowania aplikacji.

Jeśli chcesz obsłużyć to dostosowanie w aplikacji, musisz utworzyć obiekt [CKeyboardManager](reference/ckeyboardmanager-class.md) . Aby utworzyć `CKeyboardManager` obiekt, wywołaj funkcję [CWinAppEx:: InitKeyboardManager](reference/cwinappex-class.md#initkeyboardmanager). Ta metoda służy do tworzenia i inicjowania Menedżera klawiatury. W przypadku ręcznego tworzenia Menedżera klawiatury nadal trzeba wywołać metodę `CWinAppEx::InitKeyboardManager` inicjalizacji.

W przypadku tworzenia aplikacji za pomocą kreatora zostanie zainicjowany Menedżer klawiatury. Po zainicjowaniu przez aplikację Menedżera klawiatury, struktura dodaje kartę **klawiatury** do okna dialogowego **Dostosowywanie** .

## <a name="mouse-customization"></a>Dostosowywanie myszy

Na poniższej ilustracji przedstawiono kartę **myszy** okna dialogowego **Dostosowywanie** .

![Karta myszy w oknie dialogowym Dostosowywanie](../mfc/media/mfcnextmousetab.png "Karta myszy w oknie dialogowym Dostosowywanie") <br/>
Karta Dostosowywanie myszy

Użytkownik współdziała z tą kartą, aby przypisać polecenie menu do akcji dwukrotnego kliknięcia przycisku myszy. Użytkownik wybiera widok z lewej strony okna, a następnie używa formantów po prawej stronie, aby skojarzyć polecenie z akcją dwukrotnego kliknięcia. Gdy użytkownik kliknie przycisk **Zamknij**, aplikacja wykonuje skojarzone polecenie za każdym razem, gdy użytkownik kliknie dwukrotnie dowolne miejsce w widoku.

Domyślnie Dostosowywanie myszy nie jest włączane podczas tworzenia aplikacji za pomocą kreatora.

#### <a name="to-enable-mouse-customization"></a>Aby włączyć Dostosowywanie myszy

1. Zainicjuj obiekt [CMouseManager](reference/cmousemanager-class.md) przez wywołanie [CWinAppEx:: InitMouseManager](reference/cwinappex-class.md#initmousemanager).

1. Uzyskaj wskaźnik do Menedżera myszy przy użyciu [CWinAppEx:: GetMouseManager](reference/cwinappex-class.md#getmousemanager).

1. Dodaj widoki do Menedżera myszy przy użyciu metody [CMouseManager:: AddView](reference/cmousemanager-class.md#addview) . Zrób to dla każdego widoku, który chcesz dodać do Menedżera myszy.

Po zainicjowaniu przez aplikację Menedżera myszy, struktura dodaje kartę **myszy** do okna dialogowego **Dostosowywanie** . Jeśli nie dodasz żadnych widoków, uzyskanie dostępu do karty spowoduje nieobsługiwany wyjątek. Po utworzeniu listy widoków karta **mysz** jest dostępna dla użytkownika.

Po dodaniu nowego widoku do Menedżera myszy należy nadać mu unikatowy identyfikator. Jeśli chcesz obsługiwać Dostosowywanie myszy dla okna, musisz przetworzyć WM_LBUTTONDBLCLICK komunikat i wywołać funkcję [CWinAppEx:: OnViewDoubleClick](reference/cwinappex-class.md#onviewdoubleclick) . Po wywołaniu tej funkcji jeden z parametrów jest IDENTYFIKATORem tego okna. Programista jest odpowiedzialny za śledzenie numerów IDENTYFIKACYJNych i skojarzonych z nimi obiektów.

## <a name="security-concerns"></a>Zagadnienia dotyczące zabezpieczeń

Zgodnie z opisem w [narzędziach zdefiniowanych przez użytkownika](user-defined-tools.md), użytkownik może skojarzyć identyfikator narzędzia zdefiniowanego przez użytkownika z zdarzeniem dwukrotnego kliknięcia. Gdy użytkownik kliknie dwukrotnie widok, aplikacja szuka narzędzia użytkownika odpowiadającego skojarzonemu IDENTYFIKATORowi. Jeśli aplikacja odnajdzie pasujące narzędzie, uruchamia narzędzie. Jeśli aplikacja nie może znaleźć pasującego narzędzia, wysyła komunikat WM_COMMAND z IDENTYFIKATORem do widoku, który został dwukrotnie kliknięty.

Dostosowane ustawienia są przechowywane w rejestrze. Edytując rejestr, osoba atakująca może zastąpić prawidłowy identyfikator narzędzia użytkownika za pomocą dowolnego polecenia. Gdy użytkownik kliknie dwukrotnie widok, widok przetwarza polecenie, którego osoba atakująca zasadzonie. Może to spowodować nieoczekiwane i potencjalnie niebezpieczne zachowanie.

Ponadto ten rodzaj ataku może obejść zabezpieczenia interfejsu użytkownika. Załóżmy na przykład, że aplikacja ma wyłączone drukowanie. Oznacza to, że w interfejsie użytkownika menu i przycisk **Drukuj** są niedostępne. Zwykle zapobiega to drukowaniu aplikacji. Jeśli jednak osoba atakująca przeedytował rejestr, może wysłać polecenie drukowania bezpośrednio przez dwukrotne kliknięcie widoku, pomijając elementy interfejsu użytkownika, które są niedostępne.

Aby zabezpieczyć przed tym rodzajem ataku, Dodaj kod do programu obsługi poleceń aplikacji, aby sprawdzić, czy polecenie jest prawidłowe przed wykonaniem. Nie należy polegać na interfejsie użytkownika, aby zapobiec wysyłaniu polecenia do aplikacji.

## <a name="see-also"></a>Zobacz też

[Dostosowywanie na potrzeby MFC](customization-for-mfc.md)<br/>
[Klasa CKeyboardManager](reference/ckeyboardmanager-class.md)<br/>
[Klasa CMouseManager](reference/cmousemanager-class.md)<br/>
[Konsekwencje dostosowania związane z zabezpieczeniami](security-implications-of-customization.md)
