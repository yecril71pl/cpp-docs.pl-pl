---
title: Dostosowywanie klawiatury i myszy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- customizations [MFC], keyboard and mouse (MFC Extensions)
- keyboard and mouse customizations (MFC Extensions)
ms.assetid: 1f789f1b-5f2e-4b11-b974-e3e2a2e49d82
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 090c74c87810f6c2e7a7641deb248aa97931d93f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="keyboard-and-mouse-customization"></a>Dostosowywanie klawiatury i myszy
MFC umożliwia użytkownikom aplikacji w celu dostosowania sposobu obsługi klawiatury i myszy. Użytkownik może dostosować klawiatury, przypisując skróty klawiaturowe do poleceń. Użytkownika można również dostosować wejście myszy przez wybranie polecenia, który ma być wykonany, gdy użytkownik kliknie dwukrotnie wewnątrz windows określonych aplikacji. W tym temacie wyjaśniono, jak dostosować dane wejściowe dla aplikacji.  
  
 W **dostosowywania** okno dialogowe, użytkownik może zmienić Kontrolki niestandardowe dla myszy i klawiatury. Aby wyświetlić to okno dialogowe, użytkownik wskaże **Dostosuj** na **widoku** menu, a następnie klika przycisk **paski narzędzi i dokowanie**. W oknie dialogowym zostanie kliknięty albo **klawiatury** kartę lub **myszy** kartę.  
  
## <a name="keyboard-customization"></a>Dostosowywanie klawiatury  
 Na poniższej ilustracji pokazano **klawiatury** karcie **dostosowywania** okno dialogowe.  
  
 ![Karta klawiatury w oknie dialogowym Dostosuj](../mfc/media/mfcnextkeyboardtab.png "mfcnextkeyboardtab")  
Karta dostosowywania klawiatury  
  
 Użytkownik wchodzi w interakcję z kartą klawiatury można przypisać skróty klawiaturowe do polecenia. Dostępne polecenia są wyświetlane po lewej stronie karty. Użytkownik może wybrać wszystkie dostępne polecenia w menu. Tylko polecenia menu mogą być skojarzone ze skrótem klawiaturowym. Gdy użytkownik wprowadzi nowego skrótu **przypisać** przycisk staje się dostępny. Po kliknięciu tego przycisku aplikacji powoduje skojarzenie skrót wybranego polecenia.  
  
 Wszystkie aktualnie przypisane skróty klawiaturowe są wyświetlane w polu listy w prawej kolumnie. Użytkownika można również wybrać poszczególne skróty i ich usunięcia lub zresetowania wszystkie mapowania dla aplikacji.  
  
 Jeśli chcesz obsługuje dostosowywania tej aplikacji, należy utworzyć [CKeyboardManager](../mfc/reference/ckeyboardmanager-class.md) obiektu. Aby utworzyć `CKeyboardManager` obiektów, wywołaj funkcję [CWinAppEx::InitKeyboardManager](../mfc/reference/cwinappex-class.md#initkeyboardmanager). Ta metoda tworzy i inicjuje Menedżera klawiatury. Jeśli tworzysz klawiatury manager ręcznie, nadal należy wywołać `CWinAppEx::InitKeyboardManager` można go zainicjować.  
  
 Jeśli tworzenie aplikacji za pomocą Kreatora Menedżera klawiatury zainicjować kreatora. Po aplikacji inicjuje Menedżera klawiatury, dodaje platformę **klawiatury** karty, aby **dostosowywania** okno dialogowe.  
  
## <a name="mouse-customization"></a>Dostosowywanie myszy  
 Na poniższej ilustracji pokazano **myszy** karcie **dostosowywania** okno dialogowe.  
  
 ![Karta myszy w oknie dialogowym Dostosuj](../mfc/media/mfcnextmousetab.png "mfcnextmousetab")  
Karta dostosowywania myszy  
  
 Użytkownik wchodzi w interakcję z na tej karcie, aby przypisać menu Akcja kliknij dwukrotnie polecenie, aby wskaźnik myszy. Użytkownik wybiera widoku z lewej strony okna, a następnie używa formanty po prawej stronie, aby skojarzyć polecenie ze skrótem akcji kliknij dwukrotnie. Gdy użytkownik kliknie **Zamknij**, aplikacja wykonuje skojarzone polecenie zawsze, gdy użytkownik kliknie dwukrotnie dowolne miejsce w widoku.  
  
 Domyślnie dostosowania myszy nie jest włączona, gdy za pomocą Kreatora tworzenia aplikacji.  
  
#### <a name="to-enable-mouse-customization"></a>Aby włączyć Dostosowywanie myszy  
  
1.  Inicjowanie [CMouseManager](../mfc/reference/cmousemanager-class.md) obiektu przez wywołanie metody [CWinAppEx::InitMouseManager](../mfc/reference/cwinappex-class.md#initmousemanager).  
  
2.  Wskaźnik do Menedżera myszy uzyskany przy użyciu [CWinAppEx::GetMouseManager](../mfc/reference/cwinappex-class.md#getmousemanager).  
  
3.  Dodawanie widoków do Menedżera myszy przy użyciu [CMouseManager::AddView](../mfc/reference/cmousemanager-class.md#addview) metody. W tym dla każdego widoku, który ma zostać dodany do Menedżera myszy.  
  
 Po aplikacji inicjuje Menedżera mysz, dodaje platformę **myszy** karty, aby **Dostosuj** okno dialogowe. Jeśli nie zostaną dodane wszystkie widoki, uzyskiwanie dostępu do karty spowoduje, że wystąpił nieobsługiwany wyjątek. Po utworzeniu listy widoków, **myszy** karta jest dostępna dla użytkownika.  
  
 Po dodaniu nowego widoku do Menedżera myszy możesz nadać mu unikatowy identyfikator. Jeśli chcesz obsługuje myszy dostosowywania okna musi przetworzyć `WM_LBUTTONDBLCLICK` komunikat i wywołanie [CWinAppEx::OnViewDoubleClick](../mfc/reference/cwinappex-class.md#onviewdoubleclick) funkcji. Podczas wywoływania tej funkcji, jeden z parametrów jest identyfikator dla tego okna. Jest odpowiedzialny za programisty, aby śledzić numery identyfikatorów i obiekty skojarzone z nimi.  
  
## <a name="security-concerns"></a>Zagadnienia dotyczące zabezpieczeń  
 Zgodnie z opisem w [narzędzia zdefiniowane przez użytkownika](../mfc/user-defined-tools.md), użytkownik może skojarzyć Identyfikatora użytkownika narzędzia ze zdarzeniem kliknij dwukrotnie. Gdy użytkownik kliknie dwukrotnie widoku, aplikacja szuka narzędzia użytkownika odpowiadającego skojarzony identyfikator. Jeśli aplikacja znajduje dopasowywania narzędzie, wykonuje narzędzie. Jeśli aplikacja nie może odnaleźć pasującego narzędzia, wysyła komunikat WM_COMMAND o identyfikatorze do widoku, który został dwukrotnie kliknięty.  
  
 Dostosowane ustawienia są przechowywane w rejestrze. Edytując rejestr, osoba atakująca może zastąpić prawidłowy narzędzia identyfikator użytkownika dowolne polecenie. Gdy użytkownik kliknie dwukrotnie widoku, widok procesy polecenie, które osoba atakująca których. Może to spowodować nieoczekiwane i potencjalnie niebezpiecznych zachowanie.  
  
 Ponadto ten rodzaj ataku mogą omijać zabezpieczenia interfejsu użytkownika. Na przykład załóżmy, że aplikacja ma drukowanie wyłączone. Oznacza to, że w jego interfejsie użytkownika **drukowania** menu i przycisk są niedostępne. Zapobiega to zwykle aplikacji drukowania. Ale jeśli osoba atakująca edytować rejestr, użytkownik może teraz może wysłać polecenia print bezpośrednio przez dwukrotne kliknięcie widoku, pomijając elementy interfejsu użytkownika, które są niedostępne.  
  
 W celu ochrony przed ten rodzaj ataku, należy dodać kod do programu obsługi polecenia aplikacji, aby sprawdzić poprawność polecenia przed jej wykonaniem. Nie zależą od interfejsu użytkownika, aby zapobiec polecenia wysyłane do aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie na potrzeby MFC](../mfc/customization-for-mfc.md)   
 [Klasa CKeyboardManager](../mfc/reference/ckeyboardmanager-class.md)   
 [Klasa CMouseManager](../mfc/reference/cmousemanager-class.md)   
 [Zabezpieczenia konsekwencje dostosowania związane z](../mfc/security-implications-of-customization.md)

