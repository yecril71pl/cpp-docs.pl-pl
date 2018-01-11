---
title: Sekwencja operacji przy tworzeniu aplikacji bazy danych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- applications [MFC], database
- database applications [MFC]
- database applications [MFC], creating
- MFC, database applications
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f3403807e38f59abc68bf93f510476951c5ec8ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="sequence-of-operations-for-creating-database-applications"></a>Sekwencja operacji przy tworzeniu aplikacji bazy danych
W poniższej tabeli przedstawiono roli i roli w ramach w pisania aplikacji bazy danych.  
  
> [!NOTE]
>  Środowiska Visual C++ i kreatorów nie obsługują DAO (mimo że uwzględniono klasy DAO i nadal można ich używać). Firma Microsoft zaleca używanie ODBC dla nowych projektów MFC. Obiekty DAO należy używać tylko w zachowaniu istniejących aplikacji.  
  
### <a name="creating-database-applications"></a>Tworzenie aplikacji bazy danych  
  
|Zadanie|Jak|Jest w ramach|  
|----------|------------|------------------------|  
|Zdecyduj, czy używać klas MFC ODBC i DAO.|Używanie ODBC dla nowych projektów MFC. Użyj DAO tylko do obsługi istniejących aplikacji. Aby uzyskać ogólne informacje, zobacz artykuł [programowania dostępu do danych](../data/data-access-programming-mfc-atl.md).|Platformę udostępnia klasy, które obsługują dostęp do bazy danych.|  
|Utworzyć szkielet aplikacji przy użyciu opcji bazy danych.|Kreator aplikacji MFC. Opcje na stronie obsługi bazy danych. Jeśli wybierzesz opcję, która tworzy widok rekord, również określić:<br /><br /> -Data źródła i nazwę tabeli lub nazwy<br />-Zapytania lub nazw.|Kreator aplikacji MFC tworzy pliki i określa, że obejmuje niezbędne. W zależności od opcji, które określisz pliki mogą zawierać klasy zestawu rekordów.|  
|Projektowanie formularza bazy danych lub formularzy.|Użyj edytora okien dialogowych programu Visual C++ można umieścić kontrolek w oknie dialogowym zasobów szablonu dla klas widoków rekordów.|Kreator aplikacji MFC tworzy zasób szablonu puste okno dialogowe umożliwiające Wypełnij.|  
|Utwórz dodatkowe klasy rekordów widoku i rekordów, zgodnie z potrzebami.|Użyj widoku klasa do tworzenia klas i okno dialogowe Edytor przy projektowaniu widoków.|Widok klas tworzy dodatkowe pliki dla nowych klas.|  
|Tworzenie zestawu rekordów obiektów, zgodnie z potrzebami w kodzie. Użyj każdy zestaw rekordów do modyfikowania rekordów...|Zestawach rekordów są oparte na klasach pochodzących od [crecordset —](../mfc/reference/crecordset-class.md) z kreatorów.|ODBC używa wymiana pól rekordów (RFX) do wymiany danych między bazy danych i elementy członkowskie danych pola w zestawie rekordów. Jeśli używasz widoku rekordu, wymiana danych okna dialogowego (DDX) wymiany danych między zestawu rekordów i formantów w widoku rekordu.|  
|.. lub utworzyć jawne [cdatabase —](../mfc/reference/cdatabase-class.md) w kodzie dla każdej bazy danych, który chcesz otworzyć.|Bazowy obiektów zestawu rekordów w obiektach bazy danych.|Obiekt bazy danych zapewnia interfejs do źródła danych.|  
|Dynamiczne powiązanie kolumn danych do zestawu rekordów.|W ODBC należy dodać kodu do klasy pochodnej rekordów do zarządzania powiązania. Zapoznaj się z artykułem [zestaw rekordów: dynamiczne wiązanie danych kolumn (ODBC)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).||  
  
## <a name="see-also"></a>Zobacz też  
 [Opieranie się na strukturze](../mfc/building-on-the-framework.md)   
 [Sekwencja operacji przy tworzeniu aplikacji MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [Sekwencja operacji przy tworzeniu aplikacji OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [Sekwencja operacji przy tworzeniu kontrolek ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)
