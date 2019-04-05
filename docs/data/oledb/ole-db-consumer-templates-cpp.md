---
title: Szablony konsumentów OLE DB (C++)
ms.date: 10/22/2018
helpviewer_keywords:
- databases [C++], OLE DB templates
- OLE DB consumers [C++], data access
- OLE DB consumer templates [C++]
- databases [C++], consumers
ms.assetid: d3e42612-0bc0-4d65-9c32-0e8a7b219e82
ms.openlocfilehash: d2697c955d2063bb075e06536b083c0b138aa4ac
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031962"
---
# <a name="ole-db-consumer-templates-c"></a>Szablony konsumentów OLE DB (C++)

Szablony OLE DB konsumenta obsługuje specyfikację wersji 2.6 OLE DB. (Szablony OLE DB odbiorcy są sprawdzane pod względem OLE DB 2.6, ale nie obsługują każdego interfejsu w specyfikacji.) Szablony konsumentów zminimalizować ilość kodu, który trzeba napisać, aby zaimplementować konsumenta OLE DB. Szablony umożliwiają:

- Łatwy dostęp do funkcji OLE DB i łatwą integrację z ATL i MFC.

- Model proste powiązanie dla kolumny i parametry bazy danych.

- Natywne typy danych języka C/C++ do programowania OLE DB.

Aby użyć szablonów OLE DB, należy zapoznać się z szablonów języka C++, COM i interfejsy OLE DB. Jeśli nie znasz OLE DB, zobacz [Microsoft OLE DB sterownik programu SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server).

Szablony OLE DB obsługuje istniejący model obiektów OLE DB, a nie dodaje nowy model obiektu. Klasy górnej warstwy w OLE DB szablonami konsumentów równoległe składniki zdefiniowane w specyfikacji OLE DB. Projekt szablony OLE DB konsumenta obejmuje zaawansowane funkcje, takie jak wielu metod dostępu w zestawie wierszy. Korzystanie z szablonów i wielokrotne dziedziczenie sprawia, że biblioteka małe i elastyczne.

## <a name="how-ole-db-consumers-access-data"></a>Jak dostęp do danych OLE DB konsumentów

Użytkownicy korzystają z różnych typów obiektów, które są opisane w następujących tematach:

- [Źródła i sesje danych](../../data/oledb/data-sources-and-sessions.md)

- [Metody dostępu i zestawy wierszy](../../data/oledb/accessors-and-rowsets.md)

- [Polecenia i tabele](../../data/oledb/commands-and-tables.md)

- [Rekordy użytkownika](../../data/oledb/user-records.md)

Przed konsumenta niczego, najpierw należy wybrać dostawcy OLE DB, która jest odpowiednia dla typu bazy danych, potrzebne do dostępu (na przykład SQL, Oracle, ODBC i MSDS). Aby to zrobić, zazwyczaj używa się moduł wyliczający (zobacz [CEnumerator](../../data/oledb/cenumerator-class.md) zgodnie z opisem w [źródła i sesje danych](../../data/oledb/data-sources-and-sessions.md)).

[Obiektu źródła danych](../../data/oledb/data-sources-and-sessions.md) udostępnia informacje o połączeniu, wymagane do połączenia z określonego źródła danych. Obiekt źródła danych zawiera także informacje dotyczące uwierzytelniania (np. nazwy logowania i hasła), który jest używany, aby zezwolić użytkownikom na dostęp do źródła danych. Obiekt źródła danych nawiązuje połączenie z bazą danych, a następnie tworzy jeden lub więcej obiektów sesji. Każdy [obiektu session](../../data/oledb/data-sources-and-sessions.md) zarządza własną interakcji z bazą danych (czyli zapytań i pobierania danych) i wykonuje te transakcje niezależnie od innych istniejących sesji.

Sesja tworzy obiekty wierszy i polecenia. [Obiektu polecenia](../../data/oledb/commands-and-tables.md) pozwala użytkownikom na korzystanie z bazy danych, na przykład za pomocą polecenia SQL. [Obiektu zestawu wierszy](../../data/oledb/accessors-and-rowsets.md) to zestaw danych za pomocą której można przejść, jak i w którym możesz [aktualizowanie, usuwanie i wstawianie wierszy](../../data/oledb/updating-rowsets.md).

Konsumenta OLE DB wiąże kolumn w tabelach bazy danych ze zmiennymi lokalnymi; Aby to zrobić, używa [akcesor](../../data/oledb/accessors-and-rowsets.md), która zawiera mapę przechowywania danych w ramach konsumenta. Mapa zawiera zestaw powiązań między kolumnami tabeli i lokalne buforów (zmienne) w aplikacji klienta.

Jedną z bardzo ważnym pojęciem podczas pracy z odbiorców jest zadeklarowana dwóch klas w odbiorcy: [klasy polecenie (lub tabeli)](../../data/oledb/commands-and-tables.md) i [klasy rekordów użytkowników](../../data/oledb/user-records.md). Zestaw wierszy jest dostęp za pośrednictwem klasy polecenie (lub tabeli), która dziedziczy z klasy metody dostępu i klasy zestawu wierszy. Klasa rekordu użytkownika zawiera mapę powiązania zestawu wierszy opisany wcześniej.

Więcej informacji znajduje się w następujących tematach:

- [Tworzenie konsumenta OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)

- [OLE DB konsumenta scenariuszach (przykłady)](../../data/oledb/working-with-ole-db-consumer-templates.md)

## <a name="see-also"></a>Zobacz także

[Programowanie OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Dostęp do danych](../data-access-in-cpp.md)<br/>
[Dokumentacja zestawu SDK usługi OLE DB](/previous-versions/windows/desktop/ms722784(v=vs.85))<br/>
[Sterownik OLE DB firmy Microsoft dla programu SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server)
