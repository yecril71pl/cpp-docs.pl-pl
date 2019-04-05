---
title: 'Zestaw rekordów: Ponowne wysyłanie zapytania do zestawu rekordów (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
ms.openlocfilehash: 7edc1c04da617f96165b25a47ce169b266ae0003
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024598"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>Zestaw rekordów: Ponowne wysyłanie zapytania do zestawu rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie wyjaśniono, jak obiekty zestawów rekordów umożliwia requery (oznacza to, Odśwież) z bazy danych i warto to zrobić za pomocą [Requery](../../mfc/reference/crecordset-class.md#requery) funkcja elementu członkowskiego.

Ponowne wysyłanie zapytania do zestawu rekordów głównej przyczyny są:

- Przenieś rekordów na bieżąco pod kątem rekordów dodanych przez Ciebie lub przez innych użytkowników i rekordy zostały usunięte przez innych użytkowników (te, które możesz usunąć są odzwierciedlone w zestawie danych).

- Odśwież zestaw rekordów, w zależności od zmieniających się wartości parametrów.

##  <a name="_core_bringing_the_recordset_up_to_date"></a> Dzięki temu zestaw rekordów w górę do daty

Często warto Requery — obiekt zestawu rekordów przełoży się na bieżąco. W środowisku wielodostępnym bazy danych innych użytkownicy mogą wprowadzać zmiany w danych, w czasie trwania rekordów. Aby uzyskać więcej informacji na temat po rekordów odzwierciedla zmiany dokonane przez innych użytkowników i kiedy zestawy rekordów innych użytkowników będą odzwierciedlać wprowadzone zmiany, zobacz [zestaw rekordów: Jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) i [dynamiczny](../../data/odbc/dynaset.md).

##  <a name="_core_requerying_based_on_new_parameters"></a> Ponowne wysyłanie zapytania na podstawie nowych parametrów

Innym często — i są równie ważne — użycie [Requery](../../mfc/reference/crecordset-class.md#requery) , należy wybrać nowy zestaw rekordów, w zależności od zmieniających się wartości parametrów.

> [!TIP]
>  Prędkość wysyłania zapytań jest prawdopodobnie znacznie szybsze, jeśli wywołasz `Requery` zmieniającymi się wartości parametrów niż Jeśli wywołujesz `Open` ponownie.

##  <a name="_core_requerying_dynasets_vs.._snapshots"></a> Ponowne wysyłanie zapytania zestawów dynamicznych programu vs. Migawki

Ponieważ zestawów dynamicznych są przeznaczone do wyświetlania zestawu rekordów z danymi dynamicznymi aktualne, ma zostać ponowiona zestawów dynamicznych, często, jeśli chcesz odzwierciedlić dodatki innych użytkowników. Migawki, z drugiej strony są przydatne, ponieważ możesz bezpiecznie polegać na ich zawartości statycznej podczas przygotowania raportów, obliczeń i tak dalej. Jednak czasami warto requery również migawki. W środowisku wielodostępnym dane migawki mogą utracić synchronizację ze źródłem danych, jak inni użytkownicy zmiany bazy danych.

#### <a name="to-requery-a-recordset-object"></a>Aby Requery — obiekty zestawów rekordów

1. Wywołaj [Requery](../../mfc/reference/crecordset-class.md#requery) funkcja elementu członkowskiego obiektu.

Alternatywnie można zamknąć i otworzyć oryginalny zestaw rekordów przez użytkownika. W obu przypadkach nowy zestaw rekordów reprezentuje bieżący stan źródła danych.

Aby uzyskać przykład, zobacz [widoków rekordów: Wypełnianie pola listy z drugiego zestawu rekordów](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

> [!TIP]
>  Aby zoptymalizować `Requery` wydajność, unikanie zmieniania zestawu rekordów [filtru](../../data/odbc/recordset-filtering-records-odbc.md) lub [sortowania](../../data/odbc/recordset-sorting-records-odbc.md). Zmień wartość w parametrze przed wywołaniem `Requery`.

Jeśli `Requery` wywołanie zakończy się niepowodzeniem, możesz ponowić próbę wywołania; w przeciwnym razie aplikacja powinna zakończyć działanie zostanie wyłączone poprawnie. Wywołanie `Requery` lub `Open` może zakończyć się niepowodzeniem dla każdego z kilku powodów. Być może występuje błąd sieciowy; Możesz również podczas wywołania po wydaniu istniejących danych, ale zanim nowe dane są uzyskiwane, inny użytkownik może uzyskać wyłącznego dostępu; lub można go usunąć tabeli, od którego zależy rekordów.

## <a name="see-also"></a>Zobacz także

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: Dynamically Binding Data Columns (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Zestaw rekordów: Tworzenie i zamykanie zestawów rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)