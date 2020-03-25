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
ms.openlocfilehash: b7cf40ca3b0c8e415368772063aee61008a52764
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212787"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>Zestaw rekordów: ponowne wysyłanie zapytania do zestawu rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

W tym temacie wyjaśniono, jak można użyć obiektu zestawu rekordów, aby ponownie wykonać kwerendę (czyli odświeżyć) z bazy danych i kiedy można to zrobić za pomocą funkcji członkowskiej [PonówKwerendę](../../mfc/reference/crecordset-class.md#requery) .

Główne przyczyny przeszukiwania zestawu rekordów są następujące:

- Wprowadź aktualność zestawu rekordów w odniesieniu do rekordów dodanych przez użytkownika lub innych użytkowników i rekordów usuniętych przez innych użytkowników (te, które zostały usunięte, zostały już odzwierciedlone w zestawie rekordów).

- Odśwież zestaw rekordów na podstawie zmiany wartości parametrów.

##  <a name="bringing-the-recordset-up-to-date"></a><a name="_core_bringing_the_recordset_up_to_date"></a>Zapewnianie aktualności zestawu rekordów

Często należy ponownie utworzyć kwerendę obiektu zestawu rekordów, aby przywrócić jego aktualność. W środowisku bazy danych o różnych użytkownikach inni użytkownicy mogą wprowadzać zmiany w danych w czasie trwania zestawu rekordów. Aby uzyskać więcej informacji na temat tego, kiedy zestaw rekordów odzwierciedla zmiany wprowadzone przez innych użytkowników i czy zestawy rekordów innych użytkowników odzwierciedlają zmiany, zobacz [zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) i [dynamiczny](../../data/odbc/dynaset.md).

##  <a name="requerying-based-on-new-parameters"></a><a name="_core_requerying_based_on_new_parameters"></a>Przeszukiwanie w oparciu o nowe parametry

Inna częstość — i równie ważne — użycie [kwerendy](../../mfc/reference/crecordset-class.md#requery) polega na wybraniu nowego zestawu rekordów na podstawie zmiany wartości parametrów.

> [!TIP]
>  Szybkość zapytania jest prawdopodobnie znacznie szybsza w przypadku wywołania `Requery` ze zmianami wartości parametrów niż w przypadku ponownego wywołania `Open`.

##  <a name="requerying-dynasets-vs-snapshots"></a><a name="_core_requerying_dynasets_vs.._snapshots"></a>Przeszukiwanie zestawów dynamicznych i migawek

Ze względu na to, że zestawy dynamiczne są przeznaczone do prezentowania zestawu rekordów z dynamicznymi danymi, należy często ponowić częstość, jeśli chcesz odzwierciedlić dodatki innych użytkowników. Z drugiej strony migawki są przydatne, ponieważ można bezpiecznie polegać na ich zawartości statycznej podczas przygotowywania raportów, obliczania sum itd. Mimo to czasami warto chcieć ponowić migawkę migawki. W środowisku wielodostępnym dane migawek mogą utracić synchronizację ze źródłem danych, gdy inni użytkownicy zmienią bazę danych.

#### <a name="to-requery-a-recordset-object"></a>Aby ponowić kwerendę obiektu zestawu rekordów

1. Wywołaj funkcję elementu członkowskiego [PonówKwerendę](../../mfc/reference/crecordset-class.md#requery) obiektu.

Alternatywnie można zamknąć i ponownie otworzyć oryginalny zestaw rekordów. W obu przypadkach nowy zestaw rekordów reprezentuje bieżący stan źródła danych.

Aby zapoznać się z przykładem, zobacz [widok rekordu: wypełnianie pola listy z drugiego zestawu rekordów](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

> [!TIP]
>  Aby zoptymalizować wydajność `Requery`, należy unikać zmiany [filtru](../../data/odbc/recordset-filtering-records-odbc.md) lub [sortowania](../../data/odbc/recordset-sorting-records-odbc.md)zestawu rekordów. Przed wywołaniem `Requery`Zmień wartość parametru.

Jeśli wywołanie `Requery` nie powiedzie się, można ponowić próbę wywołania; w przeciwnym razie aplikacja powinna być bezproblemowo zakończona. Wywołanie `Requery` lub `Open` może zakończyć się niepowodzeniem z jednej z kilku przyczyn. Prawdopodobnie wystąpi błąd sieciowy; lub, w trakcie wywołania, po wydaniu istniejących danych, ale przed uzyskaniem nowych danych, inny użytkownik może uzyskać wyłączny dostęp; lub tabeli, od której zależy zestaw rekordów, można usunąć.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: dynamiczne powiązanie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Zestaw rekordów: tworzenie i zamykanie zestawów rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)
