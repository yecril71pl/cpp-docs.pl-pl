---
title: "Formanty MFC ActiveX: Tematy dotyczące zaawansowanego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- MFC ActiveX controls [MFC], accessing invisible dialog controls
- MFC ActiveX controls [MFC], advanced topics
- FireError method [MFC]
- MFC ActiveX controls [MFC], database classes
- MFC ActiveX controls [MFC], special keys
- PreTranslateMessage method [MFC]
- MFC ActiveX controls [MFC], parameterized property
- ThrowError method [MFC]
ms.assetid: e9e34abb-8e2d-461e-bb9c-a1aec5dcecbd
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2205862a438099c08801556f511ebf3c5e93a277
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-advanced-topics"></a>Kontrolki ActiveX MFC: tematy zaawansowane
W tym artykule omówiono Tematy zaawansowane powiązany Programowanie formantów ActiveX. Należą do nich następujące elementy:  
  
-   [Używanie klas baz danych w kontrolkach ActiveX](#_core_using_database_classes_in_activex_controls)  
  
-   [Implementowanie sparametryzowane](#_core_implementing_a_parameterized_property)  
  
-   [Obsługa błędów formantu ActiveX](#_core_handling_errors_in_your_activex_control)  
  
-   [Klawisze specjalne Obsługa w formancie](#_core_handling_special_keys_in_your_control)  
  
-   [Uzyskiwanie dostępu do formantów okna dialogowego, które nie są widoczne w czasie wykonywania](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)  
  
##  <a name="_core_using_database_classes_in_activex_controls"></a>Używanie klas baz danych w kontrolkach ActiveX  
 Klasy formantów ActiveX są częścią biblioteki klas, należy zastosować te same procedury i reguły dotyczące używania klas baz danych w przypadku standardowej aplikacji MFC Programowanie formantów ActiveX, korzystających z klasami baz danych MFC.  
  
 Ogólne omówienie klasami baz danych MFC, zobacz [klasami baz danych MFC (DAO i ODBC)](../data/mfc-database-classes-odbc-and-dao.md). Artykuł wprowadzono klasach MFC ODBC i MFC DAO klas i kieruje użytkownika, aby uzyskać więcej szczegółów, w zależności.  
  
> [!NOTE]
>  Środowiska Visual C++ i kreatorów nie obsługują DAO (mimo że uwzględniono klasy DAO i nadal można ich używać). Firma Microsoft zaleca użycie [szablony OLE DB](../data/oledb/ole-db-programming.md) lub [ODBC i MFC](../data/odbc/odbc-and-mfc.md) dla nowych projektów. Obiekty DAO należy używać tylko w zachowaniu istniejących aplikacji.  
  
##  <a name="_core_implementing_a_parameterized_property"></a>Implementowanie sparametryzowane  
 Właściwość parametrycznego (nazywane również tablicy właściwości) to metoda udostępnianie jednorodnych kolekcję wartości jako jedna właściwość formantu. Na przykład służy sparametryzowane właściwości do udostępnienia tablicy lub słownika jako właściwość. W języku Visual Basic takiego dostępu do właściwości tablicy notacji:  
  
 [!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]  
  
 Kreator Dodaj właściwość do zaimplementowania sparametryzowane właściwości. Kreator dodawania właściwości implementuje właściwości, dodając pary funkcji Get i Set, które umożliwiają użytkownikom kontroli dostępu do właściwości przy użyciu notacji powyżej lub w sposób standardowy.  
  
 Podobny do metody i właściwości sparametryzowane również mieć maksymalną dozwoloną liczbę parametrów. W przypadku właściwości sparametryzowane limit wynosi 15 parametrów (za pomocą jednego parametru zastrzeżone do przechowywania wartości właściwości).  
  
 Poniższa procedura dodaje parametryczne właściwość o nazwie tablicy, które są dostępne jest tablicą dwuwymiarową liczb całkowitych.  
  
#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>Aby dodać właściwość sparametryzowana przy użyciu Kreatora dodawania właściwości  
  
1.  Załaduj projekt z kontroli.  
  
2.  W widoku klas rozwiń węzeł Biblioteka formantu.  
  
3.  Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugiego węzła węzeł biblioteki), aby otworzyć menu skrótów.  
  
4.  W menu skrótów kliknij **Dodaj** , a następnie kliknij przycisk **Dodaj właściwość**.  
  
5.  W **nazwa właściwości** wpisz `Array`.  
  
6.  W **typ właściwości** wybierz opcję **krótki**.  
  
7.  Dla **implementacji** typu, kliknij przycisk **metod Get/Set**.  
  
8.  W **uzyskać funkcji** i **ustawić funkcja** pola, wpisz unikatowe nazwy Get i ustawić funkcji lub zaakceptuj domyślne nazwy.  
  
9. Dodawanie parametru o nazwie `row` (typ `short`), za pomocą narzędzia **Nazwa parametru** i **typ parametru** kontrolki.  
  
10. Dodaj drugi parametr o nazwie `column` (typ `short`).  
  
11. Kliknij przycisk **Zakończ**.  
  
### <a name="changes-made-by-the-add-property-wizard"></a>Zmiany wprowadzone przez Dodaj Kreatora właściwości  
 Podczas dodawania właściwości niestandardowej, Kreator dodawania właściwości zmienia nagłówka klasy formantu (. H), jak i implementację (. Pliki CPP).  
  
 Następujące wiersze są dodawane do klasy formantu. Plik H:  
  
 [!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]  
  
 Ten kod deklaruje dwóch funkcji o nazwie `GetArray` i `SetArray` umożliwiające użytkownikowi żądanie określonych wierszy i kolumn podczas uzyskiwania dostępu do właściwości.  
  
 Ponadto Kreator dodawania właściwości dodaje następujące wiersze do formantu mapy wysyłania, znajduje się w implementacji klasy formantu (. Pliku CPP):  
  
 [!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]  
  
 Na koniec implementacje `GetArray` i `SetArray` funkcje są dodawane na końcu. Pliku CPP. W większości przypadków należy zmodyfikować funkcji Get zwraca wartość właściwości. Funkcja zestawu zazwyczaj zawiera kod, który powinien zostać wykonany, przed lub po zmianie właściwości.  
  
 Dla tej właściwości powinna być użyteczna, można zadeklarować zmiennej członkowskiej tablicą dwuwymiarową w klasie formantu typu **krótki**, do przechowywania wartości dla właściwości sparametryzowana. Można następnie zmodyfikuj funkcję Get, aby powrócić do wartości przechowywanej w odpowiednich wiersz i kolumnę, wskazane przez parametry i zmodyfikuj funkcję zestaw aktualizacji wartości odwołuje się parametry wierszy i kolumn.  
  
##  <a name="_core_handling_errors_in_your_activex_control"></a>Obsługa błędów formantu ActiveX  
 Jeśli wystąpią błędy w formancie, konieczne może być raport o błędzie do formantu kontenera. Istnieją dwie metody zgłaszania błędów, w zależności od sytuacji, w której występuje błąd. Jeśli wystąpi błąd w wartości właściwości pobierania lub ustawiania funkcji, lub w implementacji metody automatyzacji OLE, powinny wywoływać formantu [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror), które sygnały do kontrolki użytkownika wystąpił błąd. Jeśli błąd pojawia się w dowolnym momencie, powinny wywoływać formantu [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror), który generowane zdarzenie błędu.  
  
 Aby wskazać typ błędu, który wystąpił, kontrolki musi przejść pomyślnie kodu błędu `ThrowError` lub `FireError`. Kod błędu to kod stanu OLE, który ma wartość 32-bitowych. Jeśli to możliwe, wybierz kod błędu z standardowy zestaw kodów zdefiniowanych w OLECTL. Plik nagłówka H. W poniższej tabeli przedstawiono te kody.  
  
### <a name="activex-control-error-codes"></a>Kody błędów kontrolki ActiveX  
  
|Błąd|Opis|  
|-----------|-----------------|  
|**CTL_E_ILLEGALFUNCTIONCALL**|Niedozwolone wywołanie funkcji|  
|**CTL_E_OVERFLOW**|Przepełnienie|  
|**CTL_E_OUTOFMEMORY**|Za mało pamięci|  
|**CTL_E_DIVISIONBYZERO**|Dzielenie przez zero|  
|**CTL_E_OUTOFSTRINGSPACE**|Za mało miejsca na ciąg|  
|**CTL_E_OUTOFSTACKSPACE**|Za mało miejsca na stosie|  
|**CTL_E_BADFILENAMEORNUMBER**|Zła nazwa lub numer pliku|  
|**CTL_E_FILENOTFOUND**|Nie można odnaleźć pliku|  
|**CTL_E_BADFILEMODE**|Zły tryb pliku|  
|**CTL_E_FILEALREADYOPEN**|Plik jest już otwarty|  
|**CTL_E_DEVICEIOERROR**|Błąd We/Wy urządzenia|  
|**CTL_E_FILEALREADYEXISTS**|Plik już istnieje.|  
|**CTL_E_BADRECORDLENGTH**|Zła długość rekordu|  
|**CTL_E_DISKFULL**|Dysk jest zapełniony|  
|**CTL_E_BADRECORDNUMBER**|Nieprawidłowy numer rekordu|  
|**CTL_E_BADFILENAME**|Nieprawidłowa nazwa pliku|  
|**CTL_E_TOOMANYFILES**|Za dużo plików|  
|**CTL_E_DEVICEUNAVAILABLE**|Urządzenie jest niedostępne|  
|**CTL_E_PERMISSIONDENIED**|Odmowa uprawnień|  
|**CTL_E_DISKNOTREADY**|Dysk nie jest gotowy|  
|**CTL_E_PATHFILEACCESSERROR**|Błąd dostępu do ścieżki/pliku|  
|**CTL_E_PATHNOTFOUND**|Nie można odnaleźć ścieżki|  
|**CTL_E_INVALIDPATTERNSTRING**|Nieprawidłowy ciąg znaków wzorca|  
|**CTL_E_INVALIDUSEOFNULL**|Nieprawidłowe użycie wartości NULL|  
|**CTL_E_INVALIDFILEFORMAT**|Nieprawidłowy format pliku|  
|**CTL_E_INVALIDPROPERTYVALUE**|Nieprawidłowa wartość właściwości|  
|**CTL_E_INVALIDPROPERTYARRAYINDEX**|Nieprawidłowy indeks tablicy właściwości|  
|**CTL_E_SETNOTSUPPORTEDATRUNTIME**|Zestaw nie jest obsługiwana w czasie wykonywania|  
|**CTL_E_SETNOTSUPPORTED**|Set nie jest możliwa (właściwość tylko do odczytu)|  
|**CTL_E_NEEDPROPERTYARRAYINDEX**|Potrzebny indeks tablicy właściwości|  
|**CTL_E_SETNOTPERMITTED**|Zestaw nie jest dozwolone|  
|**CTL_E_GETNOTSUPPORTEDATRUNTIME**|Get nie jest możliwa w czasie wykonywania|  
|**CTL_E_GETNOTSUPPORTED**|Pobierz nie jest obsługiwany (właściwość tylko do zapisu)|  
|**CTL_E_PROPERTYNOTFOUND**|Nie odnaleziono właściwości|  
|**CTL_E_INVALIDCLIPBOARDFORMAT**|Nieprawidłowy format Schowka|  
|**CTL_E_INVALIDPICTURE**|Nieprawidłowy obraz|  
|**CTL_E_PRINTERERROR**|Błąd drukarki|  
|**CTL_E_CANTSAVEFILETOTEMP**|Nie można zapisać pliku do katalogu TEMP|  
|**CTL_E_SEARCHTEXTNOTFOUND**|Nie można odnaleźć wyszukiwania tekstu|  
|**CTL_E_REPLACEMENTSTOOLONG**|Zbyt długie elementy zastępujące|  
  
 Jeśli to konieczne, użyj **CUSTOM_CTL_SCODE** makra, aby zdefiniować kod błędów niestandardowych dla warunku, który nie pasuje do przez jeden z kodów standardowa. Parametr to makro powinna być liczbą całkowitą z zakresu od 1000 do 32767 włącznie. Na przykład:  
  
 [!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]  
  
 Jeśli tworzysz formantu ActiveX, aby zastąpić istniejący formant VBX zdefiniuj Twojej kody błędów kontrolki ActiveX z wartości liczbowych używanych przez formant VBX aby upewnić się, że kody błędów są zgodne.  
  
##  <a name="_core_handling_special_keys_in_your_control"></a>Klawisze specjalne Obsługa w formancie  
 W niektórych przypadkach można obsługiwać niektórych kombinacji klawiszy w specjalny sposób; na przykład, Wstaw nowy wiersz po naciśnięciu klawisza ENTER w tekście wielowierszowym polu formantu lub przenosić między grupy edycji kontroluje, gdy kierunkowe naciśnięty Identyfikatora klucza.  
  
 Jeśli klasą podstawową formantu ActiveX jest `COleControl`, można zastąpić [CWnd::PreTranslateMessage](../mfc/reference/cwnd-class.md#pretranslatemessage) do obsługi wiadomości, zanim kontenera przetwarza je. Korzystając z tej techniki, zawsze zwracają **TRUE** Jeśli obsługi wiadomości w zastąpienia z `PreTranslateMessage`.  
  
 Poniższy przykład kodu pokazuje sposób możliwości obsługi komunikatów dotyczących klawiszy strzałek.  
  
 [!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]  
  
 Więcej informacji dotyczących obsługi interfejsy klawiatury dla formantu ActiveX znajduje się w dokumentacji zestawu SDK ActiveX.  
  
##  <a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a>Uzyskiwanie dostępu do formantów okna dialogowego, które nie są widoczne w czasie wykonywania  
 Można utworzyć kontrolki okna dialogowego, bez interfejsu użytkownika, które nie są widoczne w czasie wykonywania. Jeśli dodasz niewidoczne w czasie wykonywania formantu ActiveX — okno dialogowe i użyj [CWnd::GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem) do kontroli dostępu, kontrolka nie będzie działać poprawnie. Zamiast tego warto z nich korzystać z poniższych można uzyskać obiektu, który reprezentuje kontrolkę:  
  
-   Za pomocą elementu członkowskiego zmiennej Kreatora dodawania, wybierz **zmiennej formantu** , a następnie wybierz identyfikator formantu. Wprowadź nazwę zmiennej elementu członkowskiego i wybierz klasy otoki formantu jako **— typ formantu**.  
  
     —lub—  
  
-   Deklarowanie zmiennej lokalnej i podklasy elementu okna dialogowego. Wstaw kod, który jest podobny do następującego (`CMyCtrl` to klasa otoki `IDC_MYCTRL1` jest identyfikator formantu):  
  
     [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

