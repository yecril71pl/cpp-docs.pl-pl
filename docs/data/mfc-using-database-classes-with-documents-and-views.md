---
title: 'MFC: używanie klas baz danych z dokumentami i widokami'
ms.date: 11/04/2016
helpviewer_keywords:
- documents [C++], database applications
- recordsets [C++], documents and views
- CRecordView class, using in database forms
- views [C++], database applications
- forms [C++], database applications
- record views [C++], form-based applications
- document/view architecture [C++], in databases
- database applications [C++], forms
- database classes [C++], MFC
- ODBC recordsets [C++], documents and views
- ODBC [C++], forms
ms.assetid: 83979974-fc63-46ac-b162-e8403a572e2c
ms.openlocfilehash: 9e071e0cc25492073cd74ed517284476b6e49ef8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368905"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC: używanie klas baz danych z dokumentami i widokami

Można użyć klas bazy danych MFC z architekturą dokumentu/widoku lub bez niej. W tym temacie podkreślono pracę z dokumentami i widokami. Wyjaśnia:

- [Jak napisać aplikację opartą na formularzach](#_core_writing_a_form.2d.based_application) `CRecordView` przy użyciu obiektu jako widoku głównego w dokumencie.

- [Jak używać obiektów programu recordset w dokumentach i widokach](#_core_using_recordsets_in_documents_and_views).

- [Inne względy](#_core_other_factors).

Aby uzyskać alternatywy, zobacz [MFC: Using Database Classes Without Documents and Views](../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="writing-a-form-based-application"></a><a name="_core_writing_a_form.2d.based_application"></a>Pisanie aplikacji opartej na formularzach

Wiele aplikacji dostępu do danych są oparte na formularzach. Interfejs użytkownika jest formularzem zawierającym formanty, w których użytkownik sprawdza, wprowadza lub edytuje dane. Aby nawiązać formularz zgłoszeniowy, użyj klasy `CRecordView`. Po uruchomieniu Kreatora aplikacji MFC i wybierz typ klienta **ODBC** na `CRecordView` stronie Obsługa bazy **danych,** projekt używa dla klasy widoku.

W aplikacji opartej na formularzach każdy obiekt `CRecordset` widoku rekordu przechowuje wskaźnik do obiektu. Mechanizm wymiany pól rekordów (RFX) (Framework) wymienia dane między zestawem rekordów a źródłem danych. Mechanizm wymiany danych dialogowych (DDX) wymienia dane między elementami elementów członkowskich pola obiektu zestaw rekordów a formantami w formularzu. `CRecordView`udostępnia również domyślne funkcje obsługi poleceń do nawigowania od rekordu do rekordu w formularzu.

Aby utworzyć aplikację opartą na formularzach za pomocą kreatora aplikacji, zobacz Tworzenie aplikacji MFC i obsługi bazy danych [opartych na formularzach,](../mfc/reference/creating-a-forms-based-mfc-application.md) [Kreator aplikacji MFC](../mfc/reference/database-support-mfc-application-wizard.md).

Aby uzyskać pełną dyskusję na temat formularzy, zobacz [Rejestrowanie widoków](../data/record-views-mfc-data-access.md).

## <a name="using-recordsets-in-documents-and-views"></a><a name="_core_using_recordsets_in_documents_and_views"></a>Używanie rekordów w dokumentach i widokach

Wiele prostych aplikacji opartych na formularzach nie potrzebuje dokumentów. Jeśli aplikacja jest bardziej złożona, prawdopodobnie chcesz użyć dokumentu jako serwera `CDatabase` proxy dla bazy danych, przechowując obiekt, który łączy się ze źródłem danych. Aplikacje oparte na formularzach zwykle przechowują wskaźnik do obiektu pliku recordset w widoku. Inne rodzaje aplikacji bazy danych `CDatabase` przechowują zestawy rekordów i obiekt w dokumencie. Oto kilka możliwości korzystania z dokumentów w aplikacjach bazy danych:

- Jeśli uzyskujesz dostęp do zestawu rekordów `CRecordset` w kontekście lokalnym, utwórz obiekt lokalnie w funkcjach członkowskich dokumentu lub widoku, zgodnie z potrzebami.

   Deklarowanie obiektu pliku recordset jako zmiennej lokalnej w funkcji. Przekaż NULL do konstruktora, co powoduje, `CDatabase` że struktura do tworzenia i otwierania obiektu tymczasowego dla Ciebie. Alternatywnie należy przekazać wskaźnik `CDatabase` do obiektu. Użyj pliku recordset w ramach funkcji i niech zostanie on zniszczony automatycznie po zamknięciu funkcji.

   Po przegłosowaniu null do konstruktora tablicy rekordów, struktura `GetDefaultConnect` używa informacji `CDatabase` zwracanych przez funkcję elementu członkowskiego pliku recordset, aby utworzyć obiekt i otworzyć go. Kreatorzy implementują `GetDefaultConnect` dla Ciebie.

- Jeśli uzyskujesz dostęp do zestawu rekordów w okresie istnienia `CRecordset` dokumentu, osadź jeden lub więcej obiektów w dokumencie.

   Konstruuj obiekty pliku recordset podczas inicjowania dokumentu lub w razie potrzeby. Można napisać funkcję, która zwraca wskaźnik do pliku recordset, jeśli już istnieje lub konstrukcje i otwiera plik recordset, jeśli jeszcze nie istnieje. Zamknij, usuń i ponownie stwórz go w `Requery` razie potrzeby lub wywołaj jego funkcję elementu członkowskiego, aby odświeżyć rekordy.

- Jeśli uzyskujesz dostęp do źródła danych w okresie istnienia `CDatabase` dokumentu, osadź obiekt `CDatabase` lub zapisz wskaźnik do obiektu w nim.

   Obiekt `CDatabase` zarządza połączeniem ze źródłem danych. Obiekt jest konstruowany automatycznie podczas budowy dokumentu `Open` i wywołanie jego funkcji elementu członkowskiego podczas inicjowania dokumentu. Podczas konstruowania obiektów pliku recordset w funkcjach elementów `CDatabase` członkowskich dokumentu, należy przekazać wskaźnik do obiektu dokumentu. To kojarzy każdy zestaw rekordów z jego źródłem danych. Obiekt bazy danych jest zwykle niszczony po zamknięciu dokumentu. Obiekty pliku recordset są zazwyczaj niszczone po zamknięciu zakresu funkcji.

## <a name="other-factors"></a><a name="_core_other_factors"></a>Inne czynniki

Aplikacje oparte na formularzach często nie mają żadnego zastosowania dla mechanizmu serializacji dokumentów w ramach, więc można usunąć, wyłączyć lub zastąpić polecenia **Nowe** i **Otwórz** w menu **Plik.** Zobacz artykuł [Serializacja: Serializacja a wejście/wyjście bazy danych](../mfc/serialization-serialization-vs-database-input-output.md).

Można również skorzystać z wielu możliwości interfejsu użytkownika, które mogą obsługiwać struktury. Na przykład można użyć `CRecordView` wielu obiektów w oknie rozdzielacza, otworzyć wiele zestawów rekordów w różnych oknach podrzędnych interfejsu wielu dokumentów (MDI) i tak dalej.

Można zaimplementować drukowanie, co jest w twoim widoku, czy jest to formularz zaimplementowany z `CRecordView` lub coś innego. Jako klasy uzyskane `CFormView` `CRecordView` z , nie obsługuje drukowania, `OnPrint` ale można zastąpić funkcję elementu członkowskiego, aby umożliwić drukowanie. Aby uzyskać więcej informacji, zobacz klasę [CFormView](../mfc/reference/cformview-class.md).

Nie chcesz w ogóle używać dokumentów i widoków. W takim przypadku zobacz [MFC: Korzystanie z klas bazy danych bez dokumentów i widoków](../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="see-also"></a>Zobacz też

[Klasy bazy danych MFC](../data/mfc-database-classes-odbc-and-dao.md)
