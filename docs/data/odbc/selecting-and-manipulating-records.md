---
title: Wybieranie rekordów i operowanie nimi
ms.date: 05/09/2019
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
ms.openlocfilehash: 596ee602b5358fbd854888f43f21748fd4d85b7a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212709"
---
# <a name="selecting-and-manipulating-records"></a>Wybieranie rekordów i operowanie nimi

> [!NOTE]
> Kreator użytkownika ODBC MFC nie jest dostępny w programie Visual Studio 2019 i nowszych. Nadal można utworzyć konsumenta ręcznie.

Zwykle w przypadku wybrania rekordów ze źródła danych przy użyciu instrukcji **SELECT** języka SQL otrzymasz zestaw wyników, który jest zestawem rekordów z tabeli lub zapytania. Przy użyciu klas baz danych, należy użyć obiektu zestawu rekordów, aby wybrać zestaw wyników i uzyskać do niego dostęp. Jest to obiekt klasy specyficznej dla aplikacji, który pochodzi od klasy [CRecordset](../../mfc/reference/crecordset-class.md). Podczas definiowania klasy zestawu rekordów należy określić źródło danych, z którym ma zostać skojarzone, tabelę, która ma być używana, oraz kolumn tabeli. Kreator aplikacji MFC lub **Dodaj klasę** (zgodnie z opisem w temacie [Dodawanie użytkownika MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) tworzy klasę z połączeniem z określonym źródłem danych. Kreatorzy zapisują funkcję członkowską [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) klasy `CRecordset`, aby zwrócić nazwę tabeli.

Przy użyciu obiektu [CRecordset](../../mfc/reference/crecordset-class.md) w czasie wykonywania można wykonać następujące działania:

- Sprawdzanie pól danych bieżącego rekordu.

- Filtrowanie lub sortowanie zestawu rekordów.

- Dostosuj domyślną instrukcję **SELECT** języka SQL.

- Przewiń wybrane rekordy.

- Dodawanie, aktualizowanie i usuwanie rekordów (Jeśli zarówno źródło danych, jak i zestaw rekordów są aktualizowalne).

- Sprawdź, czy zestaw rekordów umożliwia wykonywanie zapytań i Odświeżanie zawartości zestawu rekordów.

Po zakończeniu korzystania z obiektu recordset, można go zamknąć i zniszczyć. Aby uzyskać więcej informacji o zestawach rekordów, zobacz [zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md).

## <a name="see-also"></a>Zobacz też

[ODBC i MFC](../../data/odbc/odbc-and-mfc.md)
