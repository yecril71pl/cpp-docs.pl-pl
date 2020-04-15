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
ms.openlocfilehash: c5e3be3915a0707f8df17d3c9ebe2eb0e4f623b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364639"
---
# <a name="mfc-activex-controls-advanced-topics"></a>Kontrolki ActiveX MFC: tematy zaawansowane

W tym artykule omówiono zaawansowane tematy związane z tworzeniem formantów ActiveX. Należą do nich:

- [Używanie klas bazy danych w formantych ActiveX](#_core_using_database_classes_in_activex_controls)

- [Implementowanie właściwości sparametryzowanej](#_core_implementing_a_parameterized_property)

- [Obsługa błędów w kontroli ActiveX](#_core_handling_errors_in_your_activex_control)

- [Obsługa kluczy specjalnych w stercie](#_core_handling_special_keys_in_your_control)

- [Uzyskiwanie dostępu do kontrolek dialogowych, które są niewidoczne w czasie wykonywania](#_core_accessing_dialog_controls_that_are_invisible_at_run_time)

>[!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [ActiveX Controls](activex-controls.md).

## <a name="using-database-classes-in-activex-controls"></a><a name="_core_using_database_classes_in_activex_controls"></a>Używanie klas bazy danych w formantych ActiveX

Ponieważ klasy kontroli ActiveX są częścią biblioteki klas, można zastosować te same procedury i reguły dotyczące używania klas bazy danych w standardowej aplikacji MFC do tworzenia formantów ActiveX, które używają klas bazy danych MFC.

Aby uzyskać ogólny przegląd klas bazy danych MFC, zobacz [Klasy bazy danych MFC (DAO i ODBC)](../data/mfc-database-classes-odbc-and-dao.md). W tym artykule przedstawiono zarówno klasy Odbc MFC i MFC DAO klas i kieruje do więcej szczegółów na obu.

> [!NOTE]
> DAO jest obsługiwany przez pakiet Office 2013. DAO 3.6 jest ostateczną wersją i jest uważana za przestarzałą. Środowisko Visual C++ i kreatory nie obsługują DAO (chociaż klasy DAO są uwzględniane i nadal można ich używać). Firma Microsoft zaleca używanie [szablonów ole db](../data/oledb/ole-db-programming.md) lub [ODBC i MFC](../data/odbc/odbc-and-mfc.md) dla nowych projektów. Dao należy używać tylko w utrzymaniu istniejących aplikacji.

## <a name="implementing-a-parameterized-property"></a><a name="_core_implementing_a_parameterized_property"></a>Implementowanie właściwości sparametryzowanej

Właściwość sparametryzowana (czasami nazywana tablicą właściwości) jest metodą ujawniania jednorodnej kolekcji wartości jako pojedynczej właściwości formantu. Na przykład można użyć właściwości sparametryzowane, aby udostępnić tablicy lub słownika jako właściwość. W języku Visual Basic taka właściwość jest dostępna przy użyciu notacji tablicy:

[!code-vb[NVC_MFC_AxVb#1](../mfc/codesnippet/visualbasic/mfc-activex-controls-advanced-topics_1.vb)]

Kreator dodawania właściwości służy do implementowania właściwości sparametryzowanej. Kreator dodawania właściwości implementuje właściwość, dodając parę funkcji Get/Set, które umożliwiają użytkownikowi sterującemu dostęp do właściwości przy użyciu powyższego notacji lub w standardowy sposób.

Podobnie jak metody i właściwości, sparametryzowane właściwości mają również limit liczby dozwolonych parametrów. W przypadku właściwości sparametryzowanych limit wynosi 15 parametrów (z jednym parametrem zarezerwowanym do przechowywania wartości właściwości).

Poniższa procedura dodaje sparametryzowaną właściwość o nazwie Array, do której można uzyskać dostęp jako dwuwymiarowa tablica liczby całkowitej.

#### <a name="to-add-a-parameterized-property-using-the-add-property-wizard"></a>Aby dodać właściwość sparametryzowaną za pomocą Kreatora dodawania właściwości

1. Załaduj projekt formantu.

1. W widoku klasy rozwiń węzeł biblioteki formantu.

1. Kliknij prawym przyciskiem myszy węzeł interfejsu formantu (drugi węzeł węzła biblioteki), aby otworzyć menu skrótów.

1. W menu skrótów kliknij polecenie **Dodaj,** a następnie kliknij pozycję **Dodaj właściwość**.

1. W polu **Nazwa** właściwości `Array`wpisz .

1. W polu **Typ właściwości** wybierz **krótki**.

1. W przypadku typu **implementacji** kliknij pozycję **Pobierz/Ustaw metody**.

1. W polach **Pobierz funkcję** i **Ustaw funkcję** wpisz unikatowe nazwy funkcji Pobierz i Ustaw lub zaakceptuj nazwy domyślne.

1. Dodaj parametr, nazywany *wierszem* (typ *krótki),* używając kontrolek **Nazwa parametru** i **Typ parametru.**

1. Dodaj drugi parametr o nazwie *kolumna* (typ *krótki*).

1. Kliknij przycisk **Zakończ**.

### <a name="changes-made-by-the-add-property-wizard"></a>Zmiany wprowadzone przez Kreatora dodawania właściwości

Po dodaniu właściwości niestandardowej Kreator dodawania właściwości wprowadza zmiany w nagłówku klasy formantu (. H) i wdrożenie (. CPP).

Następujące wiersze są dodawane do klasy kontrolnej . Plik H:

[!code-cpp[NVC_MFC_AxUI#35](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_2.h)]

Ten kod deklaruje dwie `GetArray` `SetArray` funkcje wywoływane i które umożliwiają użytkownikowi żądanie określonego wiersza i kolumny podczas uzyskiwania dostępu do właściwości.

Ponadto Kreator dodawania właściwości dodaje następujące wiersze do mapy wysyłki formantu, znajdującej się w implementacji klasy kontrolnej (. CPP):

[!code-cpp[NVC_MFC_AxUI#36](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_3.cpp)]

Na koniec implementacje `GetArray` funkcji `SetArray` i funkcji są dodawane na końcu . CPP. W większości przypadków zmodyfikujesz Get funkcji, aby zwrócić wartość właściwości. Funkcja Set zwykle zawiera kod, który powinien zostać wykonany przed lub po zmianie właściwości.

Dla tej właściwości, które mają być przydatne, można zadeklarować dwuwymiarową zmienną elementu członkowskiego tablicy w klasie formantu typu **short**, do przechowywania wartości dla właściwości sparametryzowanej. Następnie można zmodyfikować Funkcję Pobierz, aby zwrócić wartość przechowywaną w odpowiednim wierszu i kolumnie, jak wskazują parametry, i zmodyfikować funkcję Ustaw, aby zaktualizować wartość, do której odwołują się parametry wiersza i kolumny.

## <a name="handling-errors-in-your-activex-control"></a><a name="_core_handling_errors_in_your_activex_control"></a>Obsługa błędów w kontroli ActiveX

Jeśli wystąpią warunki błędu w formancie, może być konieczne zgłoszenie błędu do kontenera formantu. Istnieją dwie metody raportowania błędów, w zależności od sytuacji, w której występuje błąd. Jeśli błąd występuje w ramach właściwości Get lub Set funkcji lub w ramach implementacji ole automation metody, formant powinien wywołać [COleControl::ThrowError](../mfc/reference/colecontrol-class.md#throwerror), który sygnalizuje użytkownikowi sterującemu, że wystąpił błąd. Jeśli błąd występuje w dowolnym innym czasie, formant powinien wywołać [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror), który uruchamia zdarzenie błąd czas.

Aby wskazać rodzaj błędu, który wystąpił, formant musi `ThrowError` `FireError`przekazać kod błędu do lub . Kod błędu to kod stanu OLE, który ma wartość 32-bitową. Jeśli to możliwe, wybierz kod błędu ze standardowego zestawu kodów zdefiniowanych w OLECTL. H. W poniższej tabeli podsumowano te kody.

### <a name="activex-control-error-codes"></a>Kody błędów kontroli ActiveX

|Błąd|Opis|
|-----------|-----------------|
|CTL_E_ILLEGALFUNCTIONCALL|Nielegalne wywołanie funkcji|
|CTL_E_OVERFLOW|Przepełnienie|
|CTL_E_OUTOFMEMORY|Brak pamięci|
|CTL_E_DIVISIONBYZERO|Podział przez zero|
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
|CTL_E_BADRECORDNUMBER|Nieprawidłowa liczba rekordów|
|CTL_E_BADFILENAME|Zła nazwa pliku|
|CTL_E_TOOMANYFILES|Za dużo plików|
|CTL_E_DEVICEUNAVAILABLE|Urządzenie niedostępne|
|CTL_E_PERMISSIONDENIED|Odmowa uprawnień|
|CTL_E_DISKNOTREADY|Dysk nie jest gotowy|
|CTL_E_PATHFILEACCESSERROR|Błąd dostępu do ścieżki/pliku|
|CTL_E_PATHNOTFOUND|Nie można odnaleźć ścieżki|
|CTL_E_INVALIDPATTERNSTRING|Nieprawidłowy ciąg wzoru|
|CTL_E_INVALIDUSEOFNULL|Nieprawidłowe użycie wartości NULL|
|CTL_E_INVALIDFILEFORMAT|Nieprawidłowy format pliku|
|CTL_E_INVALIDPROPERTYVALUE|Nieprawidłowa wartość właściwości|
|CTL_E_INVALIDPROPERTYARRAYINDEX|Nieprawidłowy indeks tablicy właściwości|
|CTL_E_SETNOTSUPPORTEDATRUNTIME|Zestaw nie jest obsługiwany w czasie wykonywania|
|CTL_E_SETNOTSUPPORTED|Zestaw nie jest obsługiwany (właściwość tylko do odczytu)|
|CTL_E_NEEDPROPERTYARRAYINDEX|Potrzebny indeks tablicy właściwości|
|CTL_E_SETNOTPERMITTED|Zestaw niedozwolony|
|CTL_E_GETNOTSUPPORTEDATRUNTIME|Nie można uzyskać obsługi w czasie wykonywania|
|CTL_E_GETNOTSUPPORTED|Get not supported (właściwość tylko do zapisu)|
|CTL_E_PROPERTYNOTFOUND|Nie odnaleziono właściwości|
|CTL_E_INVALIDCLIPBOARDFORMAT|Nieprawidłowy format schowka|
|CTL_E_INVALIDPICTURE|Nieprawidłowy obraz|
|CTL_E_PRINTERERROR|Błąd drukarki|
|CTL_E_CANTSAVEFILETOTEMP|Nie można zapisać pliku w temp|
|CTL_E_SEARCHTEXTNOTFOUND|Nie znaleziono tekstu wyszukiwania|
|CTL_E_REPLACEMENTSTOOLONG|Zbyt długie wymiany|

W razie potrzeby użyj makra CUSTOM_CTL_SCODE, aby zdefiniować niestandardowy kod błędu dla warunku, który nie jest objęty jednym ze standardowych kodów. Parametr dla tego makra powinien być liczeniem całkowitym między 1000 i 32767 włącznie. Przykład:

[!code-cpp[NVC_MFC_AxUI#37](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_4.cpp)]

W przypadku tworzenia formantu ActiveX w celu zastąpienia istniejącego formantu VBX należy zdefiniować kody błędów sterowania ActiveX z tymi samymi wartościami liczbowymi, których używa kontrolka VBX, aby upewnić się, że kody błędów są zgodne.

## <a name="handling-special-keys-in-the-control"></a><a name="_core_handling_special_keys_in_your_control"></a>Obsługa kluczy specjalnych w stercie

W niektórych przypadkach można obsługiwać niektóre kombinacje klawiszy w sposób szczególny; na przykład wstaw nowy wiersz po naciśnięciu klawisza ENTER w wielowierszowym formancie pola tekstowego lub przesuń między grupą formantów edycji po naciśnięciu identyfikatora klucza kierunkowego.

Jeśli klasą podstawową formantu ActiveX jest `COleControl`, można zastąpić [CWnd::PreTranslateMessage](../mfc/reference/cwnd-class.md#pretranslatemessage) do obsługi wiadomości, zanim kontener je przetwarza. Korzystając z tej techniki, zawsze **zwracaj wartość PRAWDA,** `PreTranslateMessage`jeśli obsługujesz wiadomość w zastąpieniu .

Poniższy przykład kodu pokazuje możliwy sposób obsługi wiadomości związanych z klawiszy kierunkowych.

[!code-cpp[NVC_MFC_AxUI#38](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_5.cpp)]

Aby uzyskać więcej informacji na temat obsługi interfejsów klawiatury dla formantu ActiveX, zobacz dokumentację activex SDK.

## <a name="accessing-dialog-controls-that-are-invisible-at-run-time"></a><a name="_core_accessing_dialog_controls_that_are_invisible_at_run_time"></a>Uzyskiwanie dostępu do kontrolek dialogowych, które są niewidoczne w czasie wykonywania

Można utworzyć formanty okna dialogowego, które nie mają interfejsu użytkownika i są niewidoczne w czasie wykonywania. Jeśli dodasz niewidoczny formant ActiveX w czasie wykonywania do okna dialogowego i użyjesz [CWnd::GetDlgItem,](../mfc/reference/cwnd-class.md#getdlgitem) aby uzyskać dostęp do formantu, formant nie będzie działać poprawnie. Zamiast tego należy użyć jednej z następujących technik, aby uzyskać obiekt, który reprezentuje formant:

- Za pomocą Kreatora dodawania zmiennych elementu członkowskiego wybierz pozycję **Zmienna sterująca,** a następnie wybierz identyfikator formantu. Wprowadź nazwę zmiennej element członkowski i wybierz klasę otoki formantu jako **typ formantu**.

     — lub —

- Deklaruj zmienną lokalną i podklasę jako element okna dialogowego. Wstaw kod, który`CMyCtrl` przypomina następujące ( jest klasą otoki, IDC_MYCTRL1 jest identyfikatorem formantu):

   [!code-cpp[NVC_MFC_AxCont#19](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-topics_6.cpp)]

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)
