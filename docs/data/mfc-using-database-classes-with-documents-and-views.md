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
ms.openlocfilehash: e2b073b20b9518667b43c30e7ee3199a84a3ad38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213385"
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC: używanie klas baz danych z dokumentami i widokami

Można użyć klas baz danych MFC z lub bez architektury dokumentu/widoku. Ten temat kładzie nacisk na pracę z dokumentami i widokami. Wyjaśniono:

- [Jak napisać aplikację opartą na formularzu](#_core_writing_a_form.2d.based_application) przy użyciu obiektu `CRecordView` jako głównego widoku dokumentu.

- [Jak używać obiektów zestawu rekordów w dokumentach i widokach](#_core_using_recordsets_in_documents_and_views).

- [Inne zagadnienia](#_core_other_factors).

Aby zapoznać się z alternatywami, zobacz [MFC: używanie klas baz danych bez dokumentów i widoków](../data/mfc-using-database-classes-without-documents-and-views.md).

##  <a name="writing-a-form-based-application"></a><a name="_core_writing_a_form.2d.based_application"></a>Pisanie aplikacji opartej na formularzach

Wiele aplikacji dostępu do danych jest opartych na formularzach. Interfejs użytkownika jest formularz zawierający kontrolki, w których użytkownik bada, wprowadza lub edytuje dane. Aby utworzyć aplikację na podstawie, użyj klasy `CRecordView`. Po uruchomieniu Kreatora aplikacji MFC i wybraniu opcji Typ klienta **ODBC** na stronie **Obsługa bazy danych** projekt używa `CRecordView` dla klasy widoku.

W aplikacji opartej na formularzach każdy obiekt widoku rekordu przechowuje wskaźnik do obiektu `CRecordset`. Mechanizm wymiany pól rekordów (RFX) struktury wymienia dane między zestawem rekordów a źródłem danych. Mechanizm wymiany danych okna dialogowego (DDX) wymienia dane między elementami członkowskimi danych pola obiektu zestawu rekordów i kontrolkami w formularzu. `CRecordView` udostępnia również domyślne funkcje programu obsługi poleceń umożliwiające przechodzenie z rekordu do rekordu w formularzu.

Aby utworzyć aplikację opartą na formularzach za pomocą Kreatora aplikacji, zobacz [Tworzenie aplikacji MFC opartej na formularzach](../mfc/reference/creating-a-forms-based-mfc-application.md) i [bazy danych, Kreatora aplikacji MFC](../mfc/reference/database-support-mfc-application-wizard.md).

Aby uzyskać pełną dyskusję na temat formularzy, zobacz [widoki rekordów](../data/record-views-mfc-data-access.md).

##  <a name="using-recordsets-in-documents-and-views"></a><a name="_core_using_recordsets_in_documents_and_views"></a>Używanie zestawów rekordów w dokumentach i widokach

Wiele prostych aplikacji opartych na formularzach nie wymaga dokumentów. Jeśli aplikacja jest bardziej złożona, prawdopodobnie chcesz użyć dokumentu jako serwera proxy dla bazy danych, przechowując `CDatabase` obiektu, który nawiązuje połączenie ze źródłem danych. Aplikacje oparte na formularzach zwykle przechowują wskaźnik do obiektu zestawu rekordów w widoku. Inne rodzaje aplikacji baz danych przechowują zestawy rekordów i `CDatabase` obiektów w dokumencie. Poniżej przedstawiono niektóre możliwości używania dokumentów w aplikacjach baz danych:

- Jeśli uzyskujesz dostęp do zestawu rekordów w kontekście lokalnym, Utwórz obiekt `CRecordset` lokalnie w funkcjach członkowskich dokumentu lub widoku, zgodnie z wymaganiami.

   Zadeklaruj obiekt zestawu rekordów jako zmienną lokalną w funkcji. Przekaż wartość NULL do konstruktora, co powoduje, że struktura tworzy i otwiera tymczasowy obiekt `CDatabase`. Alternatywnie Przekaż wskaźnik do `CDatabase` obiektu. Użyj zestawu rekordów w funkcji i pozwól, aby został zniszczony automatycznie po zamknięciu funkcji.

   W przypadku przekazania wartości NULL do konstruktora zestawu rekordów, struktura używa informacji zwracanych przez `GetDefaultConnect` funkcji członkowskiej zestawu rekordów, aby utworzyć obiekt `CDatabase` i otworzyć go. Kreatory implementują `GetDefaultConnect`.

- Jeśli uzyskujesz dostęp do zestawu rekordów w trakcie okresu istnienia dokumentu, Osadź co najmniej jeden `CRecordset` obiektów w dokumencie.

   Konstruowanie obiektów zestawu rekordów po zainicjowaniu dokumentu lub w razie potrzeby. Można napisać funkcję, która zwraca wskaźnik do zestawu rekordów, jeśli już istnieje lub konstruuje i otworzy zestaw rekordów, jeśli jeszcze nie istnieje. Zamknij, Usuń i ponownie Utwórz zestaw rekordów w razie potrzeby lub wywołaj jego `Requery` funkcję członkowską, aby odświeżyć rekordy.

- Jeśli uzyskujesz dostęp do źródła danych w trakcie okresu istnienia dokumentu, Osadź obiekt `CDatabase` lub Zapisz wskaźnik do obiektu `CDatabase`.

   Obiekt `CDatabase` zarządza połączeniem ze źródłem danych. Obiekt jest tworzony automatycznie podczas tworzenia dokumentu i wywołuje jego funkcję członkowską `Open` po zainicjowaniu dokumentu. Podczas konstruowania obiektów zestawu rekordów w funkcjach składowych dokumentu można przekazać wskaźnik do obiektu `CDatabase` dokumentu. Kojarzy każdy zestaw rekordów ze źródłem danych. Obiekt bazy danych jest zwykle niszczony, gdy dokument zostanie zamknięty. Obiekty zestawu rekordów są zwykle niszczone, gdy opuszczają zakres funkcji.

##  <a name="other-factors"></a><a name="_core_other_factors"></a>Inne czynniki

Aplikacje oparte na formularzach często nie mają zastosowania do mechanizmu serializacji dokumentu struktury, dlatego warto usunąć, wyłączyć lub zastąpić **nowe** i **otwarte** polecenia w menu **plik** . Zobacz serializacji artykułu [: serializacji a dane wejściowe/wyjściowe bazy danych](../mfc/serialization-serialization-vs-database-input-output.md).

Warto również użyć wielu możliwości interfejsu użytkownika, które mogą być obsługiwane przez platformę. Na przykład można użyć wielu obiektów `CRecordView` w oknie rozdzielacza, otworzyć wiele zestawów rekordów w różnych oknach podrzędnych interfejsu wielu dokumentów (MDI) i tak dalej.

Możesz chcieć zaimplementować drukowanie dowolnego elementu w Twoim widoku, niezależnie od tego, czy jest to formularz zaimplementowany przy użyciu `CRecordView`, czy innego. Ponieważ klasy pochodne `CFormView`, `CRecordView` nie obsługują drukowania, ale można przesłonić funkcję elementu członkowskiego `OnPrint`, aby umożliwić drukowanie. Aby uzyskać więcej informacji, zobacz Klasa [CFormView](../mfc/reference/cformview-class.md).

Możesz nie chcieć używać dokumentów i widoków. W takim przypadku zobacz [MFC: używanie klas baz danych bez dokumentów i widoków](../data/mfc-using-database-classes-without-documents-and-views.md).

## <a name="see-also"></a>Zobacz też

[Klasy bazy danych MFC](../data/mfc-database-classes-odbc-and-dao.md)
