---
title: 'Kontrolki ActiveX MFC: Tematy zaawansowane'
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
ms.openlocfilehash: e0daabf3d236eb7038f22c54ea76d616baf613a0
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096003"
---
# <a name="mfc-activex-controls-advanced-topics"></a>Kontrolki ActiveX MFC: Tematy zaawansowane

W tym artykule omówiono zaawansowane tematy związane z tworzeniem formantów ActiveX. Należą do nich następujące elementy:

- [Korzystanie z klas baz danych w kontrolkach ActiveX](#_core_using_database_classes_in_activex_controls)

- [Implementowanie właściwości sparametryzowanej](#_core_implementing_a_parameterized_property)

- [Obsługa błędów w kontrolce ActiveX](#_core_handling_errors_in_your_activex_control)

- [Obsługa kluczy specjalnych w formancie](#_core_handling_special_keys_in_your_control)

- [Dostęp do kontrolek okna dialogowego, które są niewidoczne w czasie wykonywania](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [kontrolki ActiveX](activex-controls.md).

##  <a name="_core_using_database_classes_in_activex_controls"></a>Korzystanie z klas baz danych w kontrolkach ActiveX

Ponieważ klasy kontrolek ActiveX są częścią biblioteki klas, można zastosować te same procedury i reguły służące do używania klas baz danych w standardowej aplikacji MFC do tworzenia formantów ActiveX korzystających z klas baz danych MFC.

Ogólne omówienie klas baz danych MFC zawiera temat [klasy baz danych MFC (DAO i ODBC)](../data/mfc-database-classes-odbc-and-dao.md). W tym artykule wprowadzono klasy MFC ODBC oraz klasy MFC DAO i kierują do nich więcej szczegółów.

> [!NOTE]
>   Obiekty DAO są obsługiwane przez pakiet Office 2013. Element DAO 3,6 jest wersją ostateczną i jest uznawany za przestarzały. Środowisko i C++ kreatory wizualne nie obsługują obiektów DAO (mimo że klasy DAO są dołączone i nadal można ich używać). Firma Microsoft zaleca korzystanie z [szablonów OLE DB](../data/oledb/ole-db-programming.md) lub [ODBC oraz MFC](../data/odbc/odbc-and-mfc.md) dla nowych projektów. Obiektów DAO należy używać tylko w przypadku zarządzania istniejącymi aplikacjami.

##  <a name="_core_implementing_a_parameterized_property"></a>Implementowanie właściwości sparametryzowanej

Właściwość sparametryzowane (czasami nazywana tablicą właściwości) to metoda ujawniania jednorodnej kolekcji wartości jako pojedynczej właściwości formantu. Na przykład można użyć właściwości sparametryzowanej do udostępnienia tablicy lub słownika jako właściwości. W Visual Basic, taka właściwość jest dostępna przy użyciu notacji tablicy:

[!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

Użyj Kreatora dodawania właściwości, aby zaimplementować Właściwość sparametryzowanej. Kreator dodawania właściwości implementuje właściwość, dodając parę funkcji get/set, które umożliwiają użytkownikowi kontroli dostęp do właściwości przy użyciu powyższej notacji lub w standardowy sposób.

Podobnie jak metody i właściwości, właściwości sparametryzowane mają również limit liczby dozwolonych parametrów. W przypadku właściwości sparametryzowanej limit wynosi 15 parametrów (z jednym parametrem zastrzeżonym do przechowywania wartości właściwości).

Poniższa procedura dodaje właściwość sparametryzowanej o nazwie Array, do której można uzyskać dostęp jako dwuwymiarową tablicę liczb całkowitych.

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>Aby dodać właściwość sparametryzowane przy użyciu Kreatora dodawania właściwości

1. Załaduj projekt kontrolki.

1. W Widok klasy rozwiń węzeł Biblioteka formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu dla formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj** , a następnie kliknij przycisk **Dodaj właściwość**.

1. W polu **Nazwa właściwości** wpisz `Array`.

1. W polu **Typ właściwości** wybierz pozycję **krótkie**.

1. W obszarze Typ **implementacji** kliknij pozycję **Pobierz/ustaw metody**.

1. W polach **pobieranie** i **Ustawianie** funkcji wpisz unikatowe nazwy dla funkcji Pobierz i ustaw lub zaakceptuj nazwy domyślne.

9. Dodaj parametr o nazwie *Row* (typ *Short*), używając kontrolek **Nazwa parametru** i **Typ parametru** .

10. Dodaj drugi parametr o nazwie *Column* (typ *Short*).

11. Kliknij przycisk **Zakończ**.

### <a name="changes-made-by-the-add-property-wizard"></a>Zmiany wprowadzone przez Kreatora dodawania właściwości

Po dodaniu właściwości niestandardowej Kreator dodawania właściwości wprowadza zmiany do nagłówka klasy kontrolki (. H) i implementację (. CPP).

Do klasy Control dodawane są następujące wiersze. Plik H:

[!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

Ten kod deklaruje dwie funkcje `GetArray` o `SetArray` nazwie i zezwala użytkownikowi na żądanie określonego wiersza i kolumny podczas uzyskiwania dostępu do właściwości.

Ponadto Kreator dodawania właściwości dodaje następujące wiersze do mapy wysyłania kontrolki, która znajduje się w implementacji klasy formantów (. CPP):

[!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

Na koniec implementacje `GetArray` funkcji i `SetArray` są dodawane na końcu. Plik CPP. W większości przypadków zmodyfikujesz funkcję Get, aby zwracała wartość właściwości. Funkcja Set zwykle zawiera kod, który powinien zostać wykonany, przed lub po zmianie właściwości.

Aby ta właściwość była użyteczna, można zadeklarować dwuwymiarową zmienną elementu członkowskiego tablicy w klasie kontrolki typu **Short**, aby przechowywać wartości dla właściwości sparametryzowanej. Następnie można zmodyfikować funkcję Get, aby zwracała wartość przechowywaną w prawidłowym wierszu i kolumnie, zgodnie z parametrami, i zmodyfikować funkcję Set, aby zaktualizować wartość przywoływaną przez parametry wiersza i kolumny.

##  <a name="_core_handling_errors_in_your_activex_control"></a>Obsługa błędów w kontrolce ActiveX

Jeśli w kontrolce wystąpią błędy, może być konieczne zgłoszenie błędu do kontenera kontroli. Istnieją dwie metody raportowania błędów w zależności od sytuacji, w której występuje błąd. Jeśli błąd występuje w funkcji get lub set lub w implementacji metody automatyzacji OLE, formant powinien wywołać [COleControl:: ThrowError](../mfc/reference/colecontrol-class.md#throwerror), który sygnalizuje użytkownikowi kontroli, że wystąpił błąd. Jeśli błąd występuje w dowolnym innym czasie, formant powinien wywołać metodę [COleControl:: FireError —](../mfc/reference/colecontrol-class.md#fireerror), która wyzwala zdarzenie błędu giełdowego.

Aby wskazać rodzaj błędu, który wystąpił, formant musi przekazać kod błędu do `ThrowError` lub. `FireError` Kod błędu to kod stanu OLE, który ma wartość 32-bitową. Jeśli to możliwe, wybierz kod błędu z standardowego zestawu kodów zdefiniowanych w OLECTL. H plik nagłówkowy. Poniższa tabela zawiera podsumowanie tych kodów.

### <a name="activex-control-error-codes"></a>Kody błędów kontrolki ActiveX

|Błąd|Opis|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|Niedozwolone wywołanie funkcji|
|CTL_E_OVERFLOW|Przepływ|
|CTL_E_OUTOFMEMORY|Za mało pamięci|
|CTL_E_DIVISIONBYZERO|Dzielenie przez zero|
|CTL_E_OUTOFSTRINGSPACE|Za mało miejsca na ciąg|
|CTL_E_OUTOFSTACKSPACE|Za mało miejsca na stosie|
|CTL_E_BADFILENAMEORNUMBER|Zła nazwa lub numer pliku|
|CTL_E_FILENOTFOUND|Nie znaleziono pliku|
|CTL_E_BADFILEMODE|Zły tryb pliku|
|CTL_E_FILEALREADYOPEN|Plik jest już otwarty|
|CTL_E_DEVICEIOERROR|Błąd We/Wy urządzenia|
|CTL_E_FILEALREADYEXISTS|Plik już istnieje|
|CTL_E_BADRECORDLENGTH|Zła długość rekordu|
|CTL_E_DISKFULL|Dysk zapełniony|
|CTL_E_BADRECORDNUMBER|Zły numer rekordu|
|CTL_E_BADFILENAME|Zła nazwa pliku|
|CTL_E_TOOMANYFILES|Za dużo plików|
|CTL_E_DEVICEUNAVAILABLE|Urządzenie niedostępne|
|CTL_E_PERMISSIONDENIED|Odmowa uprawnień|
|CTL_E_DISKNOTREADY|Dysk nie jest gotowy|
|CTL_E_PATHFILEACCESSERROR|Błąd dostępu do ścieżki/pliku|
|CTL_E_PATHNOTFOUND|Nie można odnaleźć ścieżki|
|CTL_E_INVALIDPATTERNSTRING|Nieprawidłowy ciąg wzorca|
|CTL_E_INVALIDUSEOFNULL|Nieprawidłowe użycie wartości NULL|
|CTL_E_INVALIDFILEFORMAT|Nieprawidłowy format pliku|
|CTL_E_INVALIDPROPERTYVALUE|Nieprawidłowa wartość właściwości|
|CTL_E_INVALIDPROPERTYARRAYINDEX|Nieprawidłowy indeks tablicy właściwości|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|Zestaw nie jest obsługiwany w czasie wykonywania|
|CTL_E_SETNOTSUPPORTED|Zestaw nie jest obsługiwany (właściwość tylko do odczytu)|
|CTL_E_NEEDPROPERTYARRAYINDEX|Potrzebny indeks tablicy właściwości|
|CTL_E_SETNOTPERMITTED|Zestaw nie jest dozwolony|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|Pobieranie nie jest obsługiwane w czasie wykonywania|
|CTL_E_GETNOTSUPPORTED|Pobieranie nie jest obsługiwane (właściwość tylko do zapisu)|
|CTL_E_PROPERTYNOTFOUND|Nie odnaleziono właściwości|
|CTL_E_INVALIDCLIPBOARDFORMAT|Nieprawidłowy format schowka|
|CTL_E_INVALIDPICTURE|Nieprawidłowy obraz|
|CTL_E_PRINTERERROR|Błąd drukarki|
|CTL_E_CANTSAVEFILETOTEMP|Nie można zapisać pliku do katalogu TEMP|
|CTL_E_SEARCHTEXTNOTFOUND|Nie znaleziono szukanego tekstu|
|CTL_E_REPLACEMENTSTOOLONG|Zamienniki są za długie|

W razie potrzeby użyj makra CUSTOM_CTL_SCODE, aby zdefiniować niestandardowy kod błędu dla warunku, który nie jest objęty jednym z standardowych kodów. Parametr dla tego makra powinien być liczbą całkowitą z przedziału od 1000 do 32767 włącznie. Na przykład:

[!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

Jeśli tworzysz formant ActiveX, aby zastąpić istniejący formant VBX, zdefiniuj kody błędów kontrolki ActiveX z tymi samymi wartościami liczbowymi, które są używane przez kontrolkę VBX, aby upewnić się, że kody błędów są zgodne.

##  <a name="_core_handling_special_keys_in_your_control"></a>Obsługa kluczy specjalnych w formancie

W niektórych przypadkach możesz chcieć obsłużyć Niektóre kombinacje klawiszy w specjalny sposób; na przykład Wstaw nowy wiersz po naciśnięciu klawisza ENTER w wielowierszowym formancie pola tekstowego lub przechodzenie między grupą kontrolek edycji po naciśnięciu klawisza kierunkowego.

Jeśli klasą bazową kontrolki ActiveX jest `COleControl`, można przesłonić [CWnd::P retranslatemessage](../mfc/reference/cwnd-class.md#pretranslatemessage) do obsługi komunikatów przed ich przetworzeniem przez kontener. W przypadku korzystania z tej techniki zawsze zwraca **wartość true** , jeśli wiadomość została przesłonięta `PreTranslateMessage`.

Poniższy przykład kodu ilustruje możliwy sposób obsługi wszelkich komunikatów związanych z kluczami kierunkowymi.

[!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

Więcej informacji o obsłudze interfejsów klawiatury dla kontrolki ActiveX znajduje się w dokumentacji zestawu SDK ActiveX.

##  <a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a>Dostęp do kontrolek okna dialogowego, które są niewidoczne w czasie wykonywania

Można utworzyć kontrolki okna dialogowego, które nie mają interfejsu użytkownika i są niewidoczne w czasie wykonywania. W przypadku dodania niewidocznej kontrolki ActiveX w czasie wykonywania do okna dialogowego i używania [CWnd:: GetDlgItem](../mfc/reference/cwnd-class.md#getdlgitem) w celu uzyskania dostępu do kontrolki formant nie będzie działać prawidłowo. Zamiast tego należy użyć jednej z następujących metod, aby uzyskać obiekt, który reprezentuje kontrolkę:

- Za pomocą Kreatora dodawania zmiennej składowej wybierz pozycję **sterowanie zmienna** , a następnie wybierz identyfikator kontrolki. Wprowadź nazwę zmiennej składowej i wybierz klasę otoki kontrolki jako **Typ formantu**.

     —lub—

- Zadeklaruj zmienną lokalną i podklasę jako element okna dialogowego. Wstaw kod, który przypomina następujący (`CMyCtrl` jest klasą otoki, IDC_MYCTRL1 jest identyfikatorem kontrolki):

   [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>Zobacz także

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)
