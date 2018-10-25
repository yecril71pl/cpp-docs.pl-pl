---
title: Wybieranie rekordów i operowanie nimi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8cfbeaa1fac2fd9df707dfa9c16ec168d48fc215
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078352"
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

## <a name="see-also"></a>Zobacz też

[ODBC i MFC](../../data/odbc/odbc-and-mfc.md)