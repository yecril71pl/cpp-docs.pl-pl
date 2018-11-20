---
title: Dostosowywanie klawiatury i myszy
ms.date: 11/19/2018
helpviewer_keywords:
- customizations [MFC], keyboard and mouse (MFC Extensions)
- keyboard and mouse customizations (MFC Extensions)
ms.assetid: 1f789f1b-5f2e-4b11-b974-e3e2a2e49d82
ms.openlocfilehash: 0ccbe83185c48439273024a97c881f1c32a2ddc7
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175685"
---
# <a name="keyboard-and-mouse-customization"></a>Dostosowywanie klawiatury i myszy

MFC umożliwia aplikacji, aby dostosować sposób obsługi klawiatury i myszy. Użytkownik może dostosować dane wejściowe z klawiatury, przez przypisanie skróty klawiaturowe do polecenia. Użytkownika można również dostosować wejście myszy, wybierając polecenie, które mają zostać wykonane, gdy użytkownik kliknie dwukrotnie wewnątrz określonego okna aplikacji. W tym temacie wyjaśniono, jak dostosować dane wejściowe dla swojej aplikacji.

W **dostosowywania** okno dialogowe, użytkownik może zmienić niestandardowe formanty dla klawiatury i myszy. Aby wyświetlić to okno dialogowe, użytkownik wskaże **Dostosuj** na **widoku** menu, a następnie klika przycisk **pasków narzędzi i dokowanie**. W oknie dialogowym użytkownik klika polecenie albo **klawiatury** karty lub **myszy** kartę.

## <a name="keyboard-customization"></a>Dostosowywanie klawiatury

Poniższa ilustracja przedstawia **klawiatury** karcie **dostosowywania** okno dialogowe.

![Karta klawiatury w oknie dialogowym Dostosuj](../mfc/media/mfcnextkeyboardtab.png "klawiatury karty w oknie dialogowym Dostosuj") <br/>
Karta dostosowywania klawiatury

Użytkownik wchodzi w interakcję z kartą klawiatury, aby przypisać jeden lub więcej skrótów klawiaturowych do polecenia. Dostępne polecenia są wyświetlane po lewej stronie karty. Użytkownik może wybrać dowolne polecenie dostępne z menu. Tylko polecenia menu można skojarzyć za pomocą skrótów klawiaturowych. Gdy użytkownik wprowadzi nowy skrót **przypisać** przycisk staje się dostępny. Po kliknięciu tego przycisku aplikacji powoduje skojarzenie skrót wybranego polecenia.

W polu listy, w prawej kolumnie tabeli są wymienione wszystkie aktualnie przypisanych skrótów klawiaturowych. Użytkownika można również wybrać pojedyncze skróty i je usunąć lub zresetować wszystkie mapowania dla aplikacji.

Jeśli chcesz obsługiwać to dostosowanie do aplikacji, należy utworzyć [CKeyboardManager](../mfc/reference/ckeyboardmanager-class.md) obiektu. Aby utworzyć `CKeyboardManager` obiektu, wywołaj funkcję [CWinAppEx::InitKeyboardManager](../mfc/reference/cwinappex-class.md#initkeyboardmanager). Ta metoda tworzy i inicjuje Menedżera klawiatury. Jeśli tworzysz klawiatury manager ręcznie, nadal należy wywołać `CWinAppEx::InitKeyboardManager` zainicjować go.

Jeśli używasz kreatora do tworzenia aplikacji, Kreator będzie inicjował Menedżera klawiatury. Po aplikacji inicjuje Menedżera klawiatury, struktura dodaje **klawiatury** kartę **dostosowywania** okno dialogowe.

## <a name="mouse-customization"></a>Dostosowywanie myszy

Poniższa ilustracja przedstawia **myszy** karcie **dostosowywania** okno dialogowe.

![Karta myszy w oknie dialogowym Dostosuj](../mfc/media/mfcnextmousetab.png "myszy karty w oknie dialogowym Dostosuj") <br/>
Karta dostosowywania myszy

Użytkownik wchodzi w interakcję z tę kartę, aby przypisać menu polecenie, aby przycisk myszy, kliknij dwukrotnie działanie. Użytkownik wybiera widok z lewej strony okna i następnie używa formanty po prawej stronie, aby skojarzyć polecenia za pomocą akcji kliknij dwukrotnie plik. Po użytkownik klika **Zamknij**, aplikacja wykonuje polecenie skojarzone zawsze wtedy, gdy użytkownik kliknie dwukrotnie dowolne miejsce w widoku.

Domyślnie dostosowywania myszy nie jest włączona podczas tworzenia aplikacji za pomocą kreatora.

#### <a name="to-enable-mouse-customization"></a>Aby włączyć Dostosowywanie myszy

1. Inicjowanie [CMouseManager](../mfc/reference/cmousemanager-class.md) obiektu przez wywołanie metody [CWinAppEx::InitMouseManager](../mfc/reference/cwinappex-class.md#initmousemanager).

1. Uzyskiwanie wskaźnika do Menedżera myszy przy użyciu [CWinAppEx::GetMouseManager](../mfc/reference/cwinappex-class.md#getmousemanager).

1. Dodawanie widoków do Menedżera myszy przy użyciu [CMouseManager::AddView](../mfc/reference/cmousemanager-class.md#addview) metody. W tym dla każdego widoku, który ma zostać dodany do Menedżera myszy.

Po aplikacji zostają Menedżera myszy platformę dodaje **myszy** kartę **Dostosuj** okno dialogowe. Jeśli nie dodasz żadnych widoków, uzyskiwanie dostępu do karty spowoduje, że nieobsługiwany wyjątek. Po utworzeniu listy widoków, **myszy** karta jest dostępna dla użytkownika.

Po dodaniu nowego widoku z menedżerem myszy tworzonemu elementowi nadawana unikatowego identyfikatora. Jeśli chcesz obsługiwać mysz dostosowywania okna, musisz przetworzyć WM_LBUTTONDBLCLICK komunikatów i wywołania [CWinAppEx::OnViewDoubleClick](../mfc/reference/cwinappex-class.md#onviewdoubleclick) funkcji. Jeśli chcesz wywołać tę funkcję, jeden z parametrów jest identyfikator dla tego okna. Jest odpowiedzialny za programisty, aby śledzić numery identyfikatorów i obiektów skojarzonych z nimi.

## <a name="security-concerns"></a>Zagadnienia dotyczące zabezpieczeń

Zgodnie z opisem w [narzędzia zdefiniowane przez użytkownika](../mfc/user-defined-tools.md), użytkownik może skojarzyć identyfikator narzędzia zdefiniowanego przez użytkownika za pomocą zdarzenia kliknij dwukrotnie plik. Gdy użytkownik kliknie dwukrotnie widoku, aplikacja szuka narzędzie użytkownika, które odpowiada skojarzony identyfikator. Jeśli aplikacja wykryje pasującego narzędzia, uruchamia narzędzie. Jeśli aplikacja nie można odnaleźć pasującego narzędzia, wysyła komunikat WM_COMMAND o identyfikatorze do widoku, który był dwukrotnym kliknięciu.

Niestandardowe ustawienia są przechowywane w rejestrze. Edytując rejestr, osoba atakująca może zastąpić identyfikator narzędzia prawidłowego użytkownika dowolne polecenie. Gdy użytkownik kliknie dwukrotnie widoku, widok procesy polecenie, które osoba atakująca obsadzony. Może to spowodować nieoczekiwane i potencjalnie niebezpieczne zachowania.

Oprócz tego rodzaju ataków można pominąć zabezpieczenia interfejsu użytkownika. Na przykład załóżmy, że aplikacja ma wyłączone drukowania. Oznacza to, że w jego interfejsie użytkownika **drukowania** menu i przycisk są niedostępne. Zapobiega to zwykle aplikacji drukowanie. Ale jeśli osoba atakująca edytować rejestr, użytkownik może teraz można wysłać polecenia drukowania bezpośrednio przez dwukrotne kliknięcie widoku, pomijając elementy interfejsu użytkownika, które są niedostępne.

Aby zabezpieczyć się przed tego rodzaju atak, należy dodać kod do obsługi polecenia Twojej aplikacji, aby sprawdzić, czy polecenie jest prawidłowa, zanim zostanie on wykonany. Nie są zależne od interfejsu użytkownika, aby uniemożliwić polecenia wysyłane do aplikacji.

## <a name="see-also"></a>Zobacz też

[Dostosowywanie na potrzeby MFC](../mfc/customization-for-mfc.md)<br/>
[Klasa CKeyboardManager](../mfc/reference/ckeyboardmanager-class.md)<br/>
[Klasa CMouseManager](../mfc/reference/cmousemanager-class.md)<br/>
[Konsekwencje dostosowania związane z zabezpieczeniami](../mfc/security-implications-of-customization.md)

