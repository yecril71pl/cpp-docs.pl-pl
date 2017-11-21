---
title: "Szablony konsumentów OLE DB (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- databases [C++], OLE DB templates
- OLE DB consumers [C++], data access
- OLE DB consumer templates [C++]
- databases [C++], consumers
ms.assetid: d3e42612-0bc0-4d65-9c32-0e8a7b219e82
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a38c2edeffbdd2c37e69ce0886c24ca0d2f0b68a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ole-db-consumer-templates-c"></a>Szablony konsumentów OLE DB (C++)
Szablony OLE DB konsumenta obsłużyć specyfikacji wersji 2.6 OLE DB. (Szablony OLE DB konsumentów są sprawdzane pod względem OLE DB 2.6, ale nie obsługują każdego interfejsu w specyfikacji.) Szablony konsumentów zminimalizować ilość kodu, który musi być zapisana do zaimplementowania konsumenta OLE DB. Szablony zawierają:  
  
-   Łatwy dostęp do funkcji OLE DB i Łatwa integracja z ATL i MFC.  
  
-   Łatwe powiązanie modelu parametry bazy danych i kolumn.  
  
-   Typy danych natywnych C/C++ Programowanie OLE DB.  
  
 Aby użyć szablonów OLE DB, należy zapoznać się z szablonów języka C++, COM i interfejsy OLE DB. Jeśli nie masz doświadczenia z OLE DB, zobacz [OLE DB Podręcznik programisty](https://msdn.microsoft.com/en-us/library/ms718124.aspx).  
  
 Szablony OLE DB obsługuje istniejący model obiektów OLE DB, a nie dodaje nowy model obiektu. Klasy górnej warstwy w OLE DB szablony konsumentów równoległe składniki specyfikacją OLE DB. Projekt szablony OLE DB konsumenta obejmuje zaawansowane funkcje, takie jak wiele metod dostępu w zestawie wierszy. Korzystanie z szablonów i dziedziczenie wielokrotne sprawia, że biblioteka małych i elastyczne.  
  
## <a name="how-ole-db-consumers-access-data"></a>Jak dostęp do danych OLE DB konsumentów  
 Konsumenci użyć różnych typów obiektów, które są opisane w następujących tematach:  
  
-   [Źródła i sesje danych](../../data/oledb/data-sources-and-sessions.md)  
  
-   [Metody dostępu i zestawy wierszy](../../data/oledb/accessors-and-rowsets.md)  
  
-   [Polecenia i tabele](../../data/oledb/commands-and-tables.md)  
  
-   [Rekordy użytkowników](../../data/oledb/user-records.md)  
  
 Przed konsumenta niczego, najpierw wybierz dostawcę OLE DB odpowiednią dla typu bazy danych potrzebnych do dostępu (na przykład SQL, Oracle, ODBC i MSDS). W tym celu należy zwykle użyć modułu wyliczającego (zobacz [CEnumerator](../../data/oledb/cenumerator-class.md) wymienionych w [źródła i sesje danych](../../data/oledb/data-sources-and-sessions.md)).  
  
 [Obiektu źródła danych](../../data/oledb/data-sources-and-sessions.md) zawiera informacje o połączeniu wymagane do połączenia z określonego źródła danych. Obiekt źródła danych zawiera także informacje dotyczące uwierzytelniania (takich jak nazwy logowania i hasła), który jest używany do zezwolić użytkownikom na dostęp do źródła danych. Obiekt źródła danych nawiązuje połączenie z bazą danych, a następnie tworzy co najmniej jeden obiekt sesji. Każdy [obiektu session](../../data/oledb/data-sources-and-sessions.md) zarządza własną interakcji z bazy danych (czyli kwerend i pobierania danych) i wykonuje te transakcje niezależnie od innych istniejącej sesji.  
  
 Sesja tworzy obiekt zestawu wierszy i polecenia. [Obiektu polecenia](../../data/oledb/commands-and-tables.md) pozwala użytkownikom na interakcję z bazy danych, na przykład za pomocą polecenia SQL. [Obiektu zestawu wierszy](../../data/oledb/accessors-and-rowsets.md) jest zestawem danych za pośrednictwem której można nawigować, jak i w którym można [aktualizowanie, usuwanie i wstawianie wierszy](../../data/oledb/updating-rowsets.md).  
  
 Konsument OLE DB wiąże kolumn w tabelach bazy danych z zmienne lokalne; Aby to zrobić, używa [akcesor](../../data/oledb/accessors-and-rowsets.md), zawierającą mapę sposób przechowywania danych w ramach konsumenta. Mapy składa się z zestawem powiązania między kolumnami tabeli i buforów lokalnego (zmienne) w aplikacji użytkownika.  
  
 Co ważne podczas pracy z konsumentów dotyczy czy Zadeklaruj dwie klasy w konsumenta: [klasy polecenia (lub tabeli)](../../data/oledb/commands-and-tables.md) i [klasy rekordów użytkowników](../../data/oledb/user-records.md). Zestaw wierszy dostępu za pomocą klasy polecenia (lub tabeli), która dziedziczy z klasy metody dostępu i klasy zestawu wierszy. Klasa rekordu użytkownika zawiera mapy powiązanie zestawu wierszy opisany wcześniej.  
  
 Więcej informacji znajduje się w następujących tematach:  
  
-   [Tworzenie konsumenta OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)  
  
-   [OLE DB konsumenta scenariuszach (przykłady)](../../data/oledb/working-with-ole-db-consumer-templates.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie OLE DB](../../data/oledb/ole-db-programming.md)   
 [Dostęp do danych](../data-access-in-cpp.md)   
 [Dokumentacja zestawu SDK OLE DB](https://msdn.microsoft.com/en-us/library/ms722784.aspx)   
 [OLE DB Podręcznik programisty](https://msdn.microsoft.com/en-us/library/ms713643.aspx)