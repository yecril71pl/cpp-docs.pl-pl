---
title: 'Kontrolki ActiveX MFC: tematy zaawansowane'
ms.date: 09/12/2018
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
ms.openlocfilehash: 607fd1c0ee5ae35f46ef26584f7f8e3ac2f1c32f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645591"
---
# <a name="mfc-activex-controls-advanced-topics"></a>Kontrolki ActiveX MFC: tematy zaawansowane

W tym artykule omówiono zaawansowane tematy związane z tworzenia formantów ActiveX. Należą do nich następujące elementy:

- [Używanie klas baz danych w kontrolkach ActiveX](#_core_using_database_classes_in_activex_controls)

- [Implementowanie właściwości sparametryzowane](#_core_implementing_a_parameterized_property)

- [Obsługa błędów w kontrolce ActiveX](#_core_handling_errors_in_your_activex_control)

- [Obsługa klawisze specjalne w kontrolce](#_core_handling_special_keys_in_your_control)

- [Uzyskiwanie dostępu do formantów okna dialogowego, które są niewidoczne w czasie wykonywania](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które zastępują ActiveX zobacz [formantów ActiveX](activex-controls.md).

##  <a name="_core_using_database_classes_in_activex_controls"></a> Używanie klas baz danych w kontrolkach ActiveX

Ponieważ klasy kontrolek ActiveX są częścią biblioteki klas, można zastosować te same procedury i reguły dotyczące używania klas baz danych w standardowej aplikacji MFC do tworzenia kontrolek ActiveX, które używają klas baz danych MFC.

Aby uzyskać ogólne omówienie klas baz danych MFC, zobacz [klas baz danych MFC (DAO i ODBC)](../data/mfc-database-classes-odbc-and-dao.md). Artykuł wprowadza klasach MFC ODBC i MFC DAO klasy i kieruje użytkownika do szczegółowe informacje na temat albo.

> [!NOTE]
>  Środowiska Visual C++ i kreatory nie obsługują DAO (mimo że uwzględniono klas DAO i nadal można użyć). Firma Microsoft zaleca się, że używasz [szablony OLE DB](../data/oledb/ole-db-programming.md) lub [ODBC i MFC](../data/odbc/odbc-and-mfc.md) dla nowych projektów. DAO należy używać tylko w zachowaniu istniejących aplikacji.

##  <a name="_core_implementing_a_parameterized_property"></a> Implementowanie właściwości sparametryzowane

Właściwości sparametryzowane (czasami nazywany tablicy właściwości) jest metodą udostępnianie jednorodnych zbiór wartości jako pojedynczej właściwości formantu. Na przykład umożliwia sparametryzowane tablicy lub słownika jako właściwość. W języku Visual Basic taką właściwość odbywa się przy użyciu notacji tablicy:

[!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

Kreator dodawania właściwości do zaimplementowania sparametryzowane. Kreator dodawania właściwości implementuje właściwość poprzez dodanie pary funkcji Get/Set, które umożliwia użytkownikowi kontroli dostępu do właściwości przy użyciu notacji powyżej, lub w sposób standardowy.

Podobnie jak metod i właściwości sparametryzowane również mieć maksymalną dozwoloną liczbę parametrów. W przypadku właściwości parametryzowania limit wynosi 15 parametrów (za pomocą jednego parametru zastrzeżone do przechowywania wartości właściwości).

Poniższa procedura dodaje właściwość sparametryzowane, o nazwie tablicy, która może być dostępna jako tablicę dwuwymiarową liczb całkowitych.

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>Aby dodać właściwości sparametryzowane przy użyciu Kreatora dodawania właściwości

1. Załaduj projekt formantu.

1. W widoku klas rozwiń węzeł biblioteki kontrolki.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla kontrolki (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij **Dodaj** a następnie kliknij przycisk **Dodaj właściwość**.

1. W **nazwa właściwości** wpisz `Array`.

1. W **typ właściwości** wybierz opcję **krótki**.

1. Dla **implementacji** typu, kliknij przycisk **metod Get/Set**.

1. W **funkcja Pobierz** i **zestawu funkcji** pola, wpisz unikatowe nazwy zestawu funkcji i Get lub zaakceptować domyślne nazwy.

9. Dodaj parametr o nazwie *wiersz* (typ *krótki*) przy użyciu **Nazwa parametru** i **typ parametru** kontrolki.

10. Dodaj drugi parametr o nazwie *kolumny* (typ *krótki*).

11. Kliknij przycisk **Zakończ**.

### <a name="changes-made-by-the-add-property-wizard"></a>Zmiany wprowadzone przez Kreator dodawania właściwości

Po dodaniu właściwości niestandardowej, Kreator dodawania właściwości sprawia, że zmiany do formantu nagłówka klasy (. Godz.), jak i implementację (. Plikach CPP).

Następujące wiersze są dodawane do klasy formantu. Plik H:

[!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

Ten kod deklaruje dwie funkcje o nazwie `GetArray` i `SetArray` umożliwiające użytkownikowi żądanie określonych wierszy i kolumn podczas uzyskiwania dostępu do właściwości.

Ponadto Kreator dodawania właściwości dodaje następujące wiersze do kontrolki mapy wysyłania, znajduje się w implementacji klasy formantu (. Plik CPP):

[!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

Na koniec implementacje `GetArray` i `SetArray` funkcje są dodawane na końcu. Plik CPP. W większości przypadków należy zmodyfikować funkcję Get w celu zwrócenia wartości właściwości. Funkcja Set zwykle zawiera kod, który powinien zostać wykonany przed lub po zmianie właściwości.

Dla tej właściwości, które były przydatne, można zadeklarować zmienną członkowską dwuwymiarową tablicę w klasie kontrolki typu **krótki**w celu przechowywania wartości właściwości sparametryzowane. Można następnie zmodyfikuj funkcję Get, aby zwrócić wartość przechowywaną w odpowiednich wierszy i kolumn, wskazane przez parametry i zmodyfikuj funkcję Set, można zaktualizować wartości odwołuje się parametry wierszy i kolumn.

##  <a name="_core_handling_errors_in_your_activex_control"></a> Obsługa błędów w kontrolce ActiveX

Jeśli wystąpią błędy w kontrolce, może być konieczne Zgłoś błąd kontener formantu. Istnieją dwie metody dla raportowania błędów, w zależności od sytuacji, w której występuje błąd. Jeśli wystąpi błąd w ramach właściwości należy pobrać lub ustawić funkcji, lub w obrębie implementacji metody automatyzacji OLE, powinny wywoływać kontrolki [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror), które sygnałów do kontrolki użytkownika wystąpił błąd. Jeśli błąd wystąpi w dowolnym innym czasie, formant powinien wywoływać [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror), która wyzwala zdarzenie błędu.

Kontrolka musi pomyślnie przejść kod błędu wskazujący rodzaj błędu, który wystąpił, `ThrowError` lub `FireError`. Kod błędu jest kod stanu OLE, który jest wartością 32-bitową. Jeśli to możliwe, wybierać standardowy zestaw kodów zdefiniowanych w OLECTL kod błędu. Plik nagłówkowy H. W poniższej tabeli przedstawiono te kody.

### <a name="activex-control-error-codes"></a>Kody błędów kontrolki ActiveX

|Błąd|Opis|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|Niedozwolone wywołanie funkcji|
|CTL_E_OVERFLOW|przepełnienia|
|CTL_E_OUTOFMEMORY|Za mało pamięci|
|CTL_E_DIVISIONBYZERO|Dzielenie przez zero|
|CTL_E_OUTOFSTRINGSPACE|Za mało miejsca na ciąg|
|CTL_E_OUTOFSTACKSPACE|Za mało miejsca na stosie|
|CTL_E_BADFILENAMEORNUMBER|Zła nazwa lub numer pliku|
|CTL_E_FILENOTFOUND|Nie można odnaleźć pliku|
|CTL_E_BADFILEMODE|Zły tryb pliku|
|CTL_E_FILEALREADYOPEN|Plik jest już otwarty|
|CTL_E_DEVICEIOERROR|Błąd We/Wy urządzenia|
|CTL_E_FILEALREADYEXISTS|Plik już istnieje.|
|CTL_E_BADRECORDLENGTH|Zła długość rekordu|
|CTL_E_DISKFULL|Dysk zapełniony|
|CTL_E_BADRECORDNUMBER|Nieprawidłowy numer rekordu|
|CTL_E_BADFILENAME|Nieprawidłowa nazwa pliku|
|CTL_E_TOOMANYFILES|Za dużo plików|
|CTL_E_DEVICEUNAVAILABLE|Urządzenie jest niedostępne|
|CTL_E_PERMISSIONDENIED|Odmowa uprawnień|
|CTL_E_DISKNOTREADY|Dysk nie jest gotowy|
|CTL_E_PATHFILEACCESSERROR|Błąd dostępu do ścieżki/pliku|
|CTL_E_PATHNOTFOUND|Nie można odnaleźć ścieżki|
|CTL_E_INVALIDPATTERNSTRING|Nieprawidłowy ciąg wzorca|
|CTL_E_INVALIDUSEOFNULL|Nieprawidłowe użycie wartości NULL|
|CTL_E_INVALIDFILEFORMAT|Nieprawidłowy format pliku|
|CTL_E_INVALIDPROPERTYVALUE|Nieprawidłowa wartość właściwości|
|CTL_E_INVALIDPROPERTYARRAYINDEX|Nieprawidłowy indeks tablicy właściwości|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|Zestaw nie jest obsługiwane w czasie wykonywania|
|CTL_E_SETNOTSUPPORTED|Nieobsługiwany zestaw (właściwość tylko do odczytu)|
|CTL_E_NEEDPROPERTYARRAYINDEX|Potrzebny indeks tablicy właściwości|
|CTL_E_SETNOTPERMITTED|Zestaw nie jest dozwolone|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|Pobierz nieobsługiwane w czasie wykonywania|
|CTL_E_GETNOTSUPPORTED|Pobieranie nie jest obsługiwany (tylko do zapisu właściwości)|
|CTL_E_PROPERTYNOTFOUND|Nie odnaleziono właściwości|
|CTL_E_INVALIDCLIPBOARDFORMAT|Nieprawidłowy format Schowka|
|CTL_E_INVALIDPICTURE|Nieprawidłowy obraz|
|CTL_E_PRINTERERROR|Błąd drukarki|
|CTL_E_CANTSAVEFILETOTEMP|Nie można zapisać pliku Temp|
|CTL_E_SEARCHTEXTNOTFOUND|Nie można odnaleźć tekstu wyszukiwania|
|CTL_E_REPLACEMENTSTOOLONG|Wymiana za długa|

Jeśli to konieczne, zdefiniować kod błędu niestandardowego w warunku, który nie pasuje do przez jeden z kodów standardowa przy użyciu funkcji makro CUSTOM_CTL_SCODE. Parametr to makro powinna być liczbą całkowitą od 1000 do 32767 (włącznie). Na przykład:

[!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

Jeśli tworzysz formant ActiveX, aby zastąpić istniejącą kontrolkę VBX zdefiniować swoje kody błędów kontrolki ActiveX przy użyciu tych samych wartości numerycznych, używanych przez formant VBX aby upewnić się, że kody błędów są zgodne.

##  <a name="_core_handling_special_keys_in_your_control"></a> Obsługa klawisze specjalne w kontrolce

W niektórych przypadkach możesz chcieć obsługi niektórych kombinacji klawiszy w specjalny sposób; na przykład, Wstaw nowy wiersz po naciśnięciu klawisza ENTER w Tekst wielowierszowy kontrolka box lub przenosić między grupą edycji przypadku steruje kierunkowego naciśnięty Identyfikatora klucza.

Jeśli klasa bazowa kontrolki ActiveX jest `COleControl`, możesz zastąpić [CWnd::PreTranslateMessage](../mfc/reference/cwnd-class.md#pretranslatemessage) może obsługiwać komunikaty zanim kontenera przetwarza je. Korzystając z tej techniki, zawsze zwracają **TRUE** Jeśli obsłużyć komunikat w zastąpienie metody `PreTranslateMessage`.

Poniższy przykład kodu demonstruje sposób możliwości obsługi komunikatów dotyczących klawiszy strzałek.

[!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

Więcej informacji na temat obsługi interfejsów klawiatury dla formantu ActiveX znajduje się w dokumentacji zestawu SDK ActiveX.

##  <a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a> Uzyskiwanie dostępu do formantów okna dialogowego, które są niewidoczne w czasie wykonywania

Można utworzyć kontrolki okna dialogowego, bez interfejsu użytkownika, które są niewidoczne w czasie wykonywania. Jeśli dodasz niewidoczne w czasie wykonywania formantu ActiveX, okno dialogowe i używania [CWnd::GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem) można uzyskać dostęp do formantu, formant nie będą działać poprawnie. Zamiast tego warto z nich korzystać z następujących technik uzyskać obiekt, który reprezentuje kontrolkę:

- Za pomocą elementu członkowskiego zmiennych Kreatora dodawania, wybierz **kontroli zmiennej** , a następnie wybierz identyfikator formantu. Wprowadź nazwę zmiennej elementu członkowskiego, a następnie wybierz klasę otoki formantu jako **— typ formantu**.

     —lub—

- Zadeklaruj zmienną lokalną i podklasy jako elementu okna dialogowego. Wstaw kod, który jest podobny do następującego (`CMyCtrl` jest klasą otoki IDC_MYCTRL1 jest identyfikator formantu):

   [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

