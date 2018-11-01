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
ms.openlocfilehash: 5e4610af199f1fd19c1edd71a8fd67bd82ab9a8b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624838"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC: używanie klas baz danych z dokumentami i widokami

Można użyć klas baz danych MFC, z lub bez architektury dokument/widok. Praca z dokumentami i widokami kładzie nacisk na ten temat. Wyjaśniono:

- [Jak napisać aplikację usługi opartej na formularzu](#_core_writing_a_form.2d.based_application) przy użyciu `CRecordView` obiektu jako widok główny dokument.

- [Jak używać zestawu rekordów obiektów w dokumentach i widoki](#_core_using_recordsets_in_documents_and_views).

- [Inne zagadnienia](#_core_other_factors).

Dla rozwiązań alternatywnych, zobacz [MFC: przy użyciu klasy bazy danych bez dokumentów i widoków](../data/mfc-using-database-classes-without-documents-and-views.md).

##  <a name="_core_writing_a_form.2d.based_application"></a> Zapisywanie aplikacji opartej na formularzu

Wiele aplikacji dostęp do danych są oparte na formularzach. Interfejs użytkownika jest formularz zawierający kontrolki, w których użytkownik bada, wprowadza lub dokona edycji danych. Aby na podstawie formularza aplikacji, należy użyć klasy `CRecordView`. Po uruchomieniu Kreatora aplikacji MFC i wybierz **ODBC** typ klienta na **obsługi bazy danych** stronę, projekt używa `CRecordView` dla klasy widoku.

W aplikacji opartej na formularzu, każdy obiekt widoku rekordu przechowuje wskaźnik do `CRecordset` obiektu. Wykazanie pól rekordów (RFX) programu exchange mechanizm wymienia dane między zestawu rekordów a źródłem danych. Dane okna dialogowego programu exchange (DDX) mechanizm wymiany danych między elementy członkowskie danych pola obiektu zestawu rekordów i formantów w formularzu. `CRecordView` udostępnia domyślne funkcje programu obsługi poleceń do nawigowania między rekordami w formularzu.

Do utworzenia aplikacji opartej na formularzu za pomocą Kreatora aplikacji, zobacz [tworzenie aplikacji MFC opartej na formularzach](../mfc/reference/creating-a-forms-based-mfc-application.md) i [obsługi bazy danych, Kreator aplikacji MFC](../mfc/reference/database-support-mfc-application-wizard.md).

Aby uzyskać pełne omówienie formularzy, zobacz [widoków rekordów](../data/record-views-mfc-data-access.md).

##  <a name="_core_using_recordsets_in_documents_and_views"></a> Za pomocą zestawów rekordów w dokumentów i widoków

Wiele prostych aplikacji opartych na formularzach nie ma potrzeby dokumentów. Jeśli aplikacja jest bardziej skomplikowana, prawdopodobnie chcesz użyć dokumentu jako serwer proxy dla bazy danych, przechowywaniu `CDatabase` obiekt, który nawiązuje połączenie ze źródłem danych. Aplikacje oparte na formularzach zazwyczaj przechowują wskaźnik do obiektu zestawu rekordów w widoku. Inne rodzaje aplikacji baz danych przechowywania zestawów rekordów i `CDatabase` obiektów w dokumencie. Poniżej przedstawiono niektóre możliwości używania dokumentów w aplikacjach baz danych:

- Jeśli uzyskujesz dostęp do zestawu rekordów w kontekście lokalnego, należy utworzyć `CRecordset` lokalnie obiektu w funkcji elementów członkowskich, dokumentu lub tego widoku, zgodnie z potrzebami.

   Jako zmienna lokalna w funkcji, należy zadeklarować obiekt zestawu rekordów. Przekazać wartości NULL do konstruktora, który powoduje, że framework do tworzenia i otwierania tymczasowego `CDatabase` obiekt dla Ciebie. Alternatywnie, można przekazać wskaźnik do `CDatabase` obiektu. Użyj zestawu rekordów w obrębie funkcji i pozwól mu automatycznie jest niszczony, kiedy funkcja kończy działanie.

   Jeśli przekazujesz o wartości NULL do Konstruktora zestawu rekordów, środowisko wykorzystuje informacje zwrócone przez zestawu rekordów `GetDefaultConnect` funkcji elementu członkowskiego, aby utworzyć `CDatabase` obiektu, a następnie otwórz go. Implementowanie kreatorów `GetDefaultConnect` dla Ciebie.

- Jeśli uzyskujesz dostęp do zestawu rekordów, w okresie istnienia dokumentu, osadzić jedną lub więcej `CRecordset` obiektów w dokumencie.

   Konstruowania obiektów zestawu rekordów, podczas inicjowania dokumentu lub zgodnie z potrzebami. Można napisać funkcję, która zwraca wskaźnik do zestawu rekordów, jeśli już istnieje lub tworzy i otwiera zestaw rekordów, jeśli jeszcze nie istnieje. Zamknij, usunąć i ponownie utworzyć zestaw rekordów, zgodnie z potrzebami lub wywołać jej `Requery` funkcja elementu członkowskiego, aby odświeżyć rekordy.

- Jeśli uzyskujesz dostęp do źródła danych w okresie istnienia dokumentu, należy osadzić `CDatabase` obiekt lub wskaźnik do przechowywania `CDatabase` obiektu w nim.

   `CDatabase` Zarządza obiekt połączenia ze źródłem danych. Obiekt jest tworzony automatycznie podczas konstruowania dokumentu i wywołania jego `Open` funkcja elementu członkowskiego, jeśli Inicjowanie dokumentu. Podczas tworzenia zestawu rekordów obiektów w dokumencie elementów członkowskich, przekazać wskaźnik do dokumentu `CDatabase` obiektu. Każdy zestaw rekordów skojarzenie ze źródłem danych. Obiekt bazy danych zazwyczaj jest niszczony, kiedy dokument zostanie zamknięty. Obiekty rekordów zwykle są niszczone, podczas zamykania zakresem funkcji.

##  <a name="_core_other_factors"></a> Inne czynniki

Aplikacje oparte na formularzach często nie znają każde użycie dla struktury dokumentu mechanizm serializacji, dzięki czemu możesz chcieć usunąć, wyłączyć lub Zastąp **New** i **Otwórz** poleceń na **Pliku** menu. Zapoznaj się z artykułem [serializacja: serializacja a. Baza danych wejściowych/wyjściowych](../mfc/serialization-serialization-vs-database-input-output.md).

Można także wprowadzić korzystanie z wielu możliwości interfejsu użytkownika, obsługujące platformę. Na przykład, można użyć wielu `CRecordView` obiektów okna dzielącego, otworzyć wiele zestawów rekordów w różnych, wiele okien podrzędnych (MDI) interfejsu dokumencie i tak dalej.

Warto wdrożyć drukowanie niezależnie od rodzaju znajduje się w danym widoku, czy jest ono formularza implementowane za pomocą `CRecordView` lub coś innego. Jak klasy pochodne `CFormView`, `CRecordView` jest obsługuje drukowanie, ale można zastąpić `OnPrint` funkcję elementu członkowskiego, aby zezwolić na drukowanie. Aby uzyskać więcej informacji, zobacz klasy [CFormView](../mfc/reference/cformview-class.md).

Nie można użyć dokumentów i widoków w ogóle. W takim przypadku zobacz [MFC: przy użyciu klasy bazy danych bez dokumentów i widoków](../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="see-also"></a>Zobacz też

[Klas baz danych MFC (.. / data/mfc-database-classes-odbc-and-dao.md)