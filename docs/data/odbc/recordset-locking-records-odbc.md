---
title: 'Zestaw rekordów: Blokowanie rekordów (ODBC) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- locks [C++], recordsets
- optimistic locking
- pessimistic locking in ODBC
- recordsets [C++], locking records
- optimistic locking, ODBC
- ODBC recordsets [C++], locking records
- data [C++], locking
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 51c84014786b8c27def7a568b85da316079c2bc1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066334"
---
# <a name="recordset-locking-records-odbc"></a>Zestaw rekordów: blokowanie rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie opisano:

- [Rodzaje dostępnych blokowanie rekordów](#_core_record.2d.locking_modes).

- [Jak zablokować rekordów rekordów podczas aktualizacji](#_core_locking_records_in_your_recordset).

Gdy używasz zestawu rekordów próbę zaktualizowania rekordu w źródle danych aplikacji można zablokować rekordu, więc żaden inny użytkownik może zaktualizować rekord, w tym samym czasie. Stan rekordu, który został zaktualizowany przez dwóch użytkowników, w tym samym czasie jest niezdefiniowana, chyba że system może zagwarantować, że dwóch użytkowników nie można zaktualizować rekord jednocześnie.

> [!NOTE]
>  Ten temat dotyczy obiektów pochodzących od `CRecordset` w wierszu zbiorczego, które podczas pobierania nie została zaimplementowana. Jeśli udało Ci się wdrożyć zbiorcze pobieranie z wiersza, niektóre informacje nie ma zastosowania. Na przykład nie można wywołać `Edit` i `Update` funkcji elementów członkowskich. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="_core_record.2d.locking_modes"></a> Tryby blokowania rekordów

Klasy bazy danych Podaj dwie [blokowanie rekordów tryby](../../mfc/reference/crecordset-class.md#setlockingmode):

- Optymistyczne blokowanie (domyślnie)

- Pesymistycznego blokowania

Trwa aktualizowanie rekordu odbywa się w trzech krokach:

1. Rozpocznij operację, wywołując [Edytuj](../../mfc/reference/crecordset-class.md#edit) funkcja elementu członkowskiego.

1. Możesz zmienić odpowiednie pola bieżącego rekordu.

1. Możesz zakończyć operację — i zwykle Zatwierdzanie aktualizacji — przez wywołanie metody [aktualizacji](../../mfc/reference/crecordset-class.md#update) funkcja elementu członkowskiego.

Optymistyczne blokowanie blokuje rekord w źródle danych tylko w trakcie `Update` wywołania. Jeśli używasz optymistyczne blokowanie w środowisku wielodostępnym, aplikacja powinna obsługiwać `Update` stanu błędu. Pesymistycznego blokowania blokuje rekord, tak szybko, jak należy wywołać `Edit` i nie zwalnia je do momentu wywołania `Update` (błędy są oznaczone za pomocą `CDBException` mechanizmu, a nie przez wartość FALSE, zwracany przez `Update`). Pesymistycznego blokowania ma potencjalne zmniejszenie wydajności dla innych użytkowników, ponieważ równoczesnego dostępu do tego samego rekordu może być konieczne poczekanie, aż do zakończenia aplikacji `Update` procesu.

##  <a name="_core_locking_records_in_your_recordset"></a> Blokowanie rekordów w twoim zestawie rekordów

Jeśli chcesz zmienić obiektem rekordem [tryb blokowania](#_core_record.2d.locking_modes) niż domyślne, należy zmienić tryb przed wywołaniem `Edit`.

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>Aby zmienić bieżący tryb blokowanie rekordów

1. Wywołaj [SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode) funkcji członkowskiej, określając opcję `CRecordset::pessimistic` lub `CRecordset::optimistic`.

Nowy tryb blokowania pozostaje, dopóki ponownie zmienić lub zestawu rekordów jest zamknięty.

> [!NOTE]
>  Sterowniki ODBC relatywnie mało obecnie obsługuje pesymistycznego blokowania.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: wykonywanie sprzężenia (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[Zestaw rekordów: dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)