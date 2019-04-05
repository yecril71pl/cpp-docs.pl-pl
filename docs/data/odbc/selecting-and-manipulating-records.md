---
title: Wybieranie rekordów i operowanie nimi
ms.date: 11/04/2016
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
ms.openlocfilehash: fa8b63dab24c921804c474df73f6b6da192a4cd8
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027496"
---
# <a name="selecting-and-manipulating-records"></a>Wybieranie rekordów i operowanie nimi

Zwykle po wybraniu rekordów ze źródła danych przy użyciu języka SQL **wybierz** instrukcji, otrzymasz zestaw wyników, czyli zestaw rekordów z tabeli lub zapytanie. Z klasami bazy danych obiekt zestawu rekordów jest używany do wybierz i dostępu do zestawu wyników. To jest obiekt klasy specyficzne dla aplikacji, która pochodzi od klasy [CRecordset](../../mfc/reference/crecordset-class.md). Podczas definiowania klasy zestawu rekordów, należy określić źródło danych, aby skojarzyć ją z, tabeli, aby używać i kolumn tabeli. Kreator aplikacji MFC lub **Dodaj klasę** (zgodnie z opisem w [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) tworzy klasę z połączeniem z określonego źródła danych. Kreatorzy zapisu [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) funkcji składowej klasy typu `CRecordset` aby zwrócić nazwę tabeli. Aby uzyskać więcej informacji na temat za pomocą kreatorów, aby utworzyć zestaw rekordów klasy, zobacz [obsługi bazy danych, Kreator aplikacji MFC](../../mfc/reference/database-support-mfc-application-wizard.md) i [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

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