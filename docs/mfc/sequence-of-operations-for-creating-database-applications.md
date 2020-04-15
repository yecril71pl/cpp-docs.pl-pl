---
title: Sekwencja operacji przy tworzeniu aplikacji bazy danych
ms.date: 11/04/2016
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
ms.openlocfilehash: c393269d6af108ee82786e9d59f81aad11428157
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372773"
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>Sekwencja operacji przy tworzeniu aplikacji bazy danych

W poniższej tabeli przedstawiono rolę i rolę struktury w pisaniu aplikacji bazy danych.

> [!NOTE]
> Środowisko Visual C++ i kreatory nie obsługują DAO (chociaż klasy DAO są uwzględniane i nadal można ich używać). Firma Microsoft zaleca używanie odbc dla nowych projektów MFC. Dao należy używać tylko w utrzymaniu istniejących aplikacji.

### <a name="creating-database-applications"></a>Tworzenie aplikacji bazy danych

|Zadanie|Nie można|Ramy te nie|
|----------|------------|------------------------|
|Zdecyduj, czy mają być używane klasy Odbc lub DAO.|Użyj ODBC dla nowych projektów MFC. Dao służy tylko do obsługi istniejących aplikacji. Aby uzyskać ogólne informacje, zobacz artykuł [Programowanie dostępu do danych](../data/data-access-programming-mfc-atl.md).|Struktura dostarcza klas, które obsługują dostęp do bazy danych.|
|Utwórz aplikację szkielet z opcjami bazy danych.|Uruchom Kreatora aplikacji MFC. Wybierz opcje na stronie Pomoc techniczna bazy danych. Jeśli wybierzesz opcję, która tworzy widok rekordu, należy również określić:<br /><br />- Nazwa lub nazwy źródła danych i tabeli<br />- Nazwa kwerendy lub nazwy.|Kreator aplikacji MFC tworzy pliki i określa niezbędne pliki. W zależności od określonych opcji pliki mogą zawierać klasę pliku recordset.|
|Zaprojektuj formularz bazy danych lub formularze.|Użyj edytora okien dialogowych języka Visual C++, aby umieścić formanty w zasobach szablonu okna dialogowego dla klas widoku rekordów.|Kreator aplikacji MFC tworzy pusty zasób szablonu okna dialogowego do wypełnienia.|
|W razie potrzeby utwórz dodatkowe klasy widoku rekordów i grupy rekordów.|Użyj widoku klasy, aby utworzyć klasy i edytor dialogów do projektowania widoków.|Widok klasy tworzy dodatkowe pliki dla nowych klas.|
|Utwórz obiekty pliku recordset zgodnie z potrzebami w kodzie. Każdy z nich służy do manipulowania rekordami...|Zestawy rekordów są oparte na klasach pochodzących z [CRecordset](../mfc/reference/crecordset-class.md) z kreatorami.|ODBC używa wymiany pól rekordów (RFX) do wymiany danych między bazą danych a członkami danych pól zbioru rekordów. Jeśli używasz widoku rekordów, wymiana danych dialogowych (DDX) wymienia dane między zestawem rekordów a formantami w widoku rekordów.|
|... lub utworzyć jawne [CDatabase](../mfc/reference/cdatabase-class.md) w kodzie dla każdej bazy danych, którą chcesz otworzyć.|Oprzeć obiekty pliku recordset na obiektach bazy danych.|Obiekt bazy danych udostępnia interfejs do źródła danych.|
|Dynamicznie powiąż kolumny danych z zestawem rekordów.|W ODBC dodaj kod do klasy pochodnej pliku recordset, aby zarządzać powiązaniem. Zobacz artykuł [Zestaw rekordów: Dynamicznie wiążące kolumny danych (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||

## <a name="see-also"></a>Zobacz też

[Opieranie się na strukturze](../mfc/building-on-the-framework.md)<br/>
[Sekwencja operacji przy tworzeniu aplikacji MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[Sekwencja operacji przy tworzeniu aplikacji OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[Sekwencja operacji przy tworzeniu kontrolek ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)
