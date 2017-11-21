---
title: "MFC: Używanie klas baz danych z dokumentami i widokami | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b63e864b519dd55eedf96d525a25897c81f16ac0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-using-database-classes-with-documents-and-views"></a>MFC: używanie klas baz danych z dokumentami i widokami
Klasy baz danych MFC można użyć z lub bez architektury dokument/widok. Ten temat jest kładzie nacisk Praca z dokumentami i widokami. Objaśniono:  
  
-   [Sposób tworzenia aplikacji opartych na formularzach](#_core_writing_a_form.2d.based_application) przy użyciu `CRecordView` obiektu jako widok główny dokumentu.  
  
-   [Jak używać obiektów zestawu rekordów w dokumentach i widokach](#_core_using_recordsets_in_documents_and_views).  
  
-   [Inne zagadnienia](#_core_other_factors).  
  
 Aby uzyskać opis rozwiązań alternatywnych, zobacz [MFC: przy użyciu klasy bazy danych bez dokumentów i widoków](../data/mfc-using-database-classes-without-documents-and-views.md).  
  
##  <a name="_core_writing_a_form.2d.based_application"></a>Pisanie aplikacji opartych na formularzach  
 Wiele aplikacji dostęp do danych są oparte na formularzach. Interfejs użytkownika jest formularz zawierający kontrolki, w których użytkownik bada, wprowadza lub umożliwia edycję danych. Aby na podstawie formularza aplikacji, należy użyć klasy `CRecordView`. Po uruchomieniu Kreatora aplikacji MFC i wybierz **ODBC** typ klienta na **obsługi bazy danych** strony, projekt korzysta z `CRecordView` w klasie widoku.
  
 W aplikacji opartej na formularzu, każdy obiekt widoku rekordu przechowuje wskaźnik do `CRecordset` obiektu. W ramach pól rekordów (RFX) programu exchange mechanizm wymiany danych między zestawu rekordów i źródła danych. (DDX) mechanizm wymiany danych między elementy członkowskie danych pola obiektu zestawu rekordów i kontrolek w formularzu wymiany danych okna dialogowego. `CRecordView`udostępnia domyślne funkcje programu obsługi poleceń do nawigowania między rekordami w formularzu.  
  
 Aby utworzyć aplikację na podstawie formularzy przy użyciu Kreatora aplikacji, zobacz [tworzenie aplikacji MFC opartej na formularzach](../mfc/reference/creating-a-forms-based-mfc-application.md) i [obsługi bazy danych, Kreator aplikacji MFC](../mfc/reference/database-support-mfc-application-wizard.md).  
  
 Pełne omówienie formularzy, zobacz [widoków rekordów](../data/record-views-mfc-data-access.md).  
  
##  <a name="_core_using_recordsets_in_documents_and_views"></a>Za pomocą zestawów rekordów w dokumentach i widokach  
 Wiele prostych aplikacji opartych na formularzach nie ma potrzeby dokumentów. Jeśli aplikacja jest bardziej złożony, prawdopodobnie chcesz użyć dokumentu jako serwer proxy dla bazy danych, przechowywanie `CDatabase` obiekt, który nawiązuje połączenie ze źródłem danych. Na podstawie formularzy aplikacji są przechowywane zazwyczaj wskaźnik do obiektu zestawu rekordów w widoku. Inne rodzaje aplikacji baz danych magazynu zestawów rekordów i `CDatabase` obiektu w dokumencie. Poniżej przedstawiono niektóre możliwości stosowania dokumentów w aplikacjach baz danych:  
  
-   Jeśli uzyskują dostęp do zestawu rekordów w kontekście lokalnego, należy utworzyć `CRecordset` lokalnie obiektu w funkcji Członkowskich dokumentu lub widok, zgodnie z potrzebami.  
  
     Obiekty zestawów rekordów należy zadeklarować jako zmienną lokalną w funkcji. Przekaż **NULL** konstruktora, co powoduje, że platformę do tworzenia i otwierania tymczasowej `CDatabase` obiekt. Alternatywnie, można przekazać wskaźnika do `CDatabase` obiektu. Użyj zestawu rekordów w ramach funkcji i pozwól mu zostać zniszczone automatycznie, gdy funkcja jest kończona.  
  
     Podczas przekazywania **NULL** do Konstruktora zestawu rekordów platformę używa informacji zwrócony przez zestaw rekordów `GetDefaultConnect` funkcji członkowskiej, aby utworzyć `CDatabase` obiekt, a następnie otwórz go ponownie. Implementowanie kreatorów `GetDefaultConnect` dla Ciebie.  
  
-   Jeśli okres istnienia dokumentu uzyskują dostęp do zestawu rekordów, osadzić co najmniej jeden `CRecordset` obiektów w dokumencie.  
  
     Konstruować obiekty rekordów podczas inicjowania dokumentu lub zgodnie z potrzebami. Można napisać funkcję, która zwraca wskaźnik do zestawu rekordów, jeśli już istnieje lub tworzy i otwiera zestawu rekordów, jeśli go jeszcze nie istnieje. Zamknij, usuwanie i ponownie utworzyć zestaw rekordów, zgodnie z potrzebami lub wywołać jej **Requery** funkcji członkowskiej, aby odświeżyć rekordy.  
  
-   Jeśli okres istnienia dokumentu uzyskują dostęp do źródła danych, osadzić `CDatabase` obiekt lub wskaźnik do przechowywania `CDatabase` obiektu w nim.  
  
     `CDatabase` Zarządza obiekt połączenia ze źródłem danych. Obiekt jest tworzony automatycznie podczas konstruowania dokumentu i wywołania jego **Otwórz** funkcji członkowskiej podczas inicjowania dokumentu. Podczas tworzenia obiektów zestawu rekordów w funkcji Członkowskich dokumentu, przekazać wskaźnik do dokumentu `CDatabase` obiektu. Każdy zestaw rekordów skojarzenie ze źródłem danych. Obiekt bazy danych jest zwykle zniszczone po zamknięciu dokumentu. Obiekty rekordów zwykle zostaną zniszczone podczas ich Zakończ zakres funkcji.  
  
##  <a name="_core_other_factors"></a>Inne czynniki  
 Aplikacje oparte na formularzu często nie znają użycia w ramach mechanizmu serializacji dokumentu, należy usunąć, wyłączyć lub Zastąp `New` i **Otwórz** polecenia w **pliku**menu. Zapoznaj się z artykułem [szeregowanie: vs serializacji. Baza danych wejścia/wyjścia](../mfc/serialization-serialization-vs-database-input-output.md).  
  
 Można także wprowadzić używać wiele możliwości interfejsu użytkownika obsługujące platformę. Na przykład można użyć wielu `CRecordView` obiektów w oknie podziału, Otwórz wiele zestawów rekordów w różnych wielu okien podrzędnych interfejsu (MDI) dokumentu i tak dalej.  
  
 Należy wdrożyć drukowanie niezależnie od znajduje się w widoku, czy formularz jest implementowana przy użyciu `CRecordView` lub inny. Jak pochodną klasy `CFormView`, `CRecordView` jest obsługuje drukowania, ale można zastąpić `OnPrint` funkcji członkowskiej, aby zezwolić na drukowanie. Aby uzyskać więcej informacji, zobacz klasy [CFormView](../mfc/reference/cformview-class.md).  
  
 Nie można używać na wszystkich dokumentów i widoków. W takim przypadku zobacz [MFC: przy użyciu klasy bazy danych bez dokumentów i widoków](../data/mfc-using-database-classes-without-documents-and-views.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasami baz danych MFC (.. / data/mfc-database-classes-odbc-and-dao.md)