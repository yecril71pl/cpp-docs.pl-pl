---
title: 'Zestaw rekordów: ponowne wysyłanie zapytania do zestawu rekordów (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
ms.openlocfilehash: cdae28f81eebe8427bc829072e0d9a83c6ec1722
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366948"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>Zestaw rekordów: ponowne wysyłanie zapytania do zestawu rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie wyjaśniono, jak można użyć obiektu pliku recordset do ponownego zapytania (czyli odświeżania) się z bazy danych i kiedy można to zrobić za pomocą funkcji elementu członkowskiego [Odśwież.](../../mfc/reference/crecordset-class.md#requery)

Główne powody ponownego przeszywania a recordset są:

- Aktualizuj go w odniesieniu do rekordów dodanych przez Użytkownika lub innych użytkowników oraz rekordów usuniętych przez innych użytkowników (te, które usuwasz, są już odzwierciedlone w uliczce).

- Odświeżaj tablicę rekordów na podstawie zmieniających się wartości parametrów.

## <a name="bringing-the-recordset-up-to-date"></a><a name="_core_bringing_the_recordset_up_to_date"></a>Doprowadzenie do aktualności recordset

Często warto ponownie podzesliwać obiekt pliku recordset, aby go aktualizować. W środowisku bazy danych dla wielu użytkowników inni użytkownicy mogą wprowadzać zmiany w danych w okresie użytkowania zbioru rekordów. Aby uzyskać więcej informacji o tym, kiedy zestaw rekordów odzwierciedla zmiany wprowadzone przez innych użytkowników i kiedy zestawy rekordów innych użytkowników odzwierciedlają zmiany, zobacz [Zestaw rekordów: Jak zestawy rekordów aktualizacji (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) i [Dynaset](../../data/odbc/dynaset.md).

## <a name="requerying-based-on-new-parameters"></a><a name="_core_requerying_based_on_new_parameters"></a>Ponowne tworzenie kwerend na podstawie nowych parametrów

Innym częstym — i równie ważnym — użyciem [kwerendy jest wybranie](../../mfc/reference/crecordset-class.md#requery) nowego zestawu rekordów na podstawie zmieniających się wartości parametrów.

> [!TIP]
> Szybkość kwerendy jest prawdopodobnie znacznie `Requery` szybsza, jeśli wywołasz ze zmieniającymi się wartościami parametrów niż jeśli wywołasz `Open` ponownie.

## <a name="requerying-dynasets-vs-snapshots"></a><a name="_core_requerying_dynasets_vs.._snapshots"></a>Ponowne podnajmowanie dynasetów a migawek

Ponieważ zestawy dynasetów są przeznaczone do prezentowania zestawu rekordów z dynamicznymi danymi up-to-date, chcesz często podzespować zestawy dynasets, jeśli chcesz odzwierciedlić dodatki innych użytkowników. Migawki, z drugiej strony, są przydatne, ponieważ można bezpiecznie polegać na ich zawartości statycznej podczas przygotowywania raportów, obliczania sum i tak dalej. Mimo to czasami warto również ponownie podzesliwać migawkę. W środowisku wielodojowym dane migawki mogą utracić synchronizację ze źródłem danych, ponieważ inni użytkownicy zmieniają bazę danych.

#### <a name="to-requery-a-recordset-object"></a>Aby ponownie podylić obiekt a recordset

1. Wywołanie funkcji elementu członkowskiego [kwerendy.](../../mfc/reference/crecordset-class.md#requery)

Alternatywnie można zamknąć i ponownie otworzyć oryginalny rekord. W obu przypadkach nowy zestaw rekordów reprezentuje bieżący stan źródła danych.

Na przykład zobacz [Widoki rekordów: Wypełnianie pola listy z drugiego zestawie rekordów](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

> [!TIP]
> Aby zoptymalizować `Requery` wydajność, należy unikać zmiany [filtru](../../data/odbc/recordset-filtering-records-odbc.md) lub [sortowania](../../data/odbc/recordset-sorting-records-odbc.md)pliku recordset . Zmień tylko wartość parametru przed wywołaniem `Requery`.

Jeśli `Requery` połączenie nie powiedzie się, można ponowić próbę wywołania; w przeciwnym razie aplikacja powinna zakończyć się bezpiecznie. Wywołanie `Requery` lub `Open` może zakończyć się niepowodzeniem z wielu powodów. Być może wystąpi błąd sieci; lub, podczas połączenia, po zwolnieniu istniejących danych, ale przed uzyskaniem nowych danych, inny użytkownik może uzyskać wyłączny dostęp; lub tabela, od której zależy twój rekord, może zostać usunięta.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: dynamiczne powiązanie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Zestaw rekordów: tworzenie i zamykanie zestawów rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)
