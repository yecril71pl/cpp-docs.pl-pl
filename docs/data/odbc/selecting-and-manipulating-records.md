---
title: Wybieranie rekordów i operowanie nimi
ms.date: 05/09/2019
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
ms.openlocfilehash: 745c0c35e42426242d92d720d5dcd3de631fb17b
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707807"
---
# <a name="selecting-and-manipulating-records"></a>Wybieranie rekordów i operowanie nimi

> [!NOTE] 
> Kreator konsumenta interfejsu ODBC MFC nie jest dostępne w programie Visual Studio 2019 r i nowszych wersjach. Nadal można utworzyć odbiorcę ręcznie.

Zwykle po wybraniu rekordów ze źródła danych przy użyciu języka SQL **wybierz** instrukcji, otrzymasz zestaw wyników, czyli zestaw rekordów z tabeli lub zapytanie. Z klasami bazy danych obiekt zestawu rekordów jest używany do wybierz i dostępu do zestawu wyników. To jest obiekt klasy specyficzne dla aplikacji, która pochodzi od klasy [CRecordset](../../mfc/reference/crecordset-class.md). Podczas definiowania klasy zestawu rekordów, należy określić źródło danych, aby skojarzyć ją z, tabeli, aby używać i kolumn tabeli. Kreator aplikacji MFC lub **Dodaj klasę** (zgodnie z opisem w [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) tworzy klasę z połączeniem z określonego źródła danych. Kreatorzy zapisu [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) funkcji składowej klasy typu `CRecordset` aby zwrócić nazwę tabeli.

Za pomocą [CRecordset](../../mfc/reference/crecordset-class.md) obiektu w czasie wykonywania, możesz:

- Sprawdź pola danych bieżącego rekordu.

- Filtrować i sortować zestawu rekordów.

- Dostosuj domyślny kod SQL **wybierz** instrukcji.

- Przewiń wybrane rekordy.

- Dodawanie, aktualizowanie lub usuwanie rekordów (Jeśli źródło danych i zestaw rekordów można aktualizować).

- Sprawdź, czy zestaw rekordów umożliwia ponowne wysyłanie zapytania, a następnie Odśwież zawartość w zestawie rekordów.

Po zakończeniu korzystania z obiektu zestawu rekordów, zamknij i zniszcz go. Aby uzyskać więcej informacji na temat zestawów rekordów, zobacz [zestawu rekordów (ODBC)](../../data/odbc/recordset-odbc.md).

## <a name="see-also"></a>Zobacz także

[ODBC i MFC](../../data/odbc/odbc-and-mfc.md)