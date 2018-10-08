---
title: Sekwencja operacji przy tworzeniu aplikacji bazy danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 483a36f62a147d9b71a489c2f611fc45c1b7fa54
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860735"
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>Sekwencja operacji przy tworzeniu aplikacji bazy danych

W poniższej tabeli przedstawiono usługi roli i roli struktury w pisaniu aplikacji baz danych.

> [!NOTE]
>  Środowiska Visual C++ i kreatory nie obsługują DAO (mimo że uwzględniono klas DAO i nadal można użyć). Firma Microsoft zaleca używanie ODBC dla nowych projektów MFC. DAO należy używać tylko w zachowaniu istniejących aplikacji.

### <a name="creating-database-applications"></a>Tworzenie aplikacji bazy danych

|Zadanie|Możesz zrobić|Struktura jest|
|----------|------------|------------------------|
|Zdecyduj, czy używać klas MFC ODBC i DAO.|Używanie ODBC dla nowych projektów MFC. Tylko po to, aby zachować istniejące aplikacje, należy użyć DAO. Aby uzyskać ogólne informacje, zobacz artykuł [programowanie dostępu do danych](../data/data-access-programming-mfc-atl.md).|Struktura dostarcza klas, które obsługują dostęp do bazy danych.|
|Tworzenie szkieletu aplikacji przy użyciu opcji bazy danych.|Uruchom Kreatora aplikacji MFC. Wybierz opcje na stronie Obsługa bazy danych. Jeśli zostanie wybrana opcja, która tworzy widoku rekordu, również określić:<br /><br />-Nazwa źródła i tabela data lub nazwy<br />-Zapytania lub nazw.|Kreator aplikacji MFC tworzy pliki i określa, że obejmuje niezbędne. W zależności od opcji, które określisz pliki może zawierać klasę zestawu rekordów.|
|Projektowanie bazy danych formularza lub formularzy.|Użyj edytora okien dialogowych Visual C++ do umieszczenia kontrolek na zasoby szablonu okna dialogowego dla klas widoków rekordów.|Kreator aplikacji MFC tworzy zasób szablonu pustego okna dialogowego należy wypełnić.|
|Tworzenie dodatkowych rekordów klasy widoku i zestawu rekordów, zgodnie z potrzebami.|Widok klas umożliwia tworzenie klas i oknie dialogowym projektowanie widoków w edytorze.|Widok klasy tworzy dodatkowe pliki dla nowych klas.|
|Tworzenie zestawu rekordów obiektów, zgodnie z potrzebami w kodzie. Każdy zestaw rekordów należy używać do manipulowania rekordów...|Twoje zestawy rekordów są oparte na klasach pochodzących od [CRecordset](../mfc/reference/crecordset-class.md) za pomocą kreatorów.|ODBC używa wymiana pól rekordów (RFX) do wymiany danych między bazą danych i elementy członkowskie danych pola w zestawie rekordów. Jeśli używasz widoku rekordu wymiana danych okna dialogowego (DDX) wymianę danych między zestawu rekordów i kontrolek w widoku rekordu.|
|.. .lub Utwórz jawną [CDatabase](../mfc/reference/cdatabase-class.md) w kodzie dla każdej bazy danych, który chcesz otworzyć.|Bazowy obiektów zestaw rekordów w obiektach bazy danych.|Obiekt bazy danych udostępnia interfejs dla źródła danych.|
|Dynamiczne powiązanie kolumn danych do zestawu rekordów.|W ODBC należy dodać kod do klasy pochodnej rekordów do zarządzania wiązanie. Zapoznaj się z artykułem [zestaw rekordów: dynamiczne powiązanie danych kolumn (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||

## <a name="see-also"></a>Zobacz też

[Opieranie się na strukturze](../mfc/building-on-the-framework.md)<br/>
[Sekwencja operacji przy tworzeniu aplikacji MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[Sekwencja operacji przy tworzeniu aplikacji OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[Sekwencja operacji przy tworzeniu kontrolek ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)
