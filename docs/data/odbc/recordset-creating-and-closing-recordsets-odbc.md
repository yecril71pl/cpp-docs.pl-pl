---
title: 'Zestaw rekordów: Tworzenie i zamykanie zestawów rekordów (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
ms.openlocfilehash: 5d5dae5bc766c0cfc31b4fb76f7fe104be0dbd74
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041270"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>Zestaw rekordów: Tworzenie i zamykanie zestawów rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

Aby użyć zestawu rekordów, konstruowania obiektu zestawu rekordów, a następnie wywołać jej `Open` funkcja elementu członkowskiego do uruchamiania kwerend w zestawie rekordów i wybierania rekordów. Po zakończeniu za pomocą zestawu rekordów, zamknij i zniszcz obiekt.

W tym temacie opisano:

- [Kiedy i jak można utworzyć obiektu zestawu rekordów](#_core_creating_recordsets_at_run_time).

- [Kiedy i jak zakwalifikować się zachowanie zestawu rekordów, parametryzacja, filtrowanie, sortowanie i blokowanie go](#_core_setting_recordset_options).

- [Kiedy i jak zamykać obiekty zestawów rekordów](#_core_closing_a_recordset).

##  <a name="_core_creating_recordsets_at_run_time"></a> Tworzenie zestawów rekordów w czasie wykonywania

Zanim będzie można utworzyć zestawu rekordów obiektów w programie klasy specyficzne dla aplikacji zestawu rekordów jest zazwyczaj zapisu. Aby uzyskać więcej informacji dotyczących tego kroku wstępnych, zobacz [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Otwórz obiekt dynamiczny lub, gdy trzeba wybrać rekordy ze źródła danych. Typ obiektu do utworzenia zależy od tego, co należy zrobić z danymi w aplikacji i na jakie sterownika ODBC obsługuje. Aby uzyskać więcej informacji, zobacz [dynamiczny](../../data/odbc/dynaset.md) i [migawki](../../data/odbc/snapshot.md).

#### <a name="to-open-a-recordset"></a>Aby otworzyć zestawu rekordów

1. Utworzyć obiekt usługi `CRecordset`-klasy pochodnej.

   Można skonstruować obiekt na stosie, lub na ramce stosu funkcji.

1. Opcjonalnie zmodyfikuj domyślne zachowanie zestawu rekordów. Opcje dostępne w temacie [Ustawianie opcji rekordów](#_core_setting_recordset_options).

1. Wywołanie obiektu [Otwórz](../../mfc/reference/crecordset-class.md#open) funkcja elementu członkowskiego.

W konstruktorze, należy przekazać wskaźnik do `CDatabase` obiektu lub przekazać wartości NULL, aby użyć obiektu tymczasowej bazy danych, który konstruuje platformę i zostanie otwarta na podstawie parametrów połączenia, zwracany przez [getdefaultconnect —](../../mfc/reference/crecordset-class.md#getdefaultconnect) funkcja elementu członkowskiego. `CDatabase` Obiekt może być podłączony do źródła danych.

Wywołanie `Open` używa języka SQL, aby wybrać rekordy ze źródła danych. Pierwszy rekord zaznaczone (jeśli istnieje) jest bieżącego rekordu. Wartości pól danego rekordu są przechowywane w elementy członkowskie danych pola obiektu zestawu rekordów. Jeśli wybrano wszystkie rekordy, zarówno `IsBOF` i `IsEOF` funkcje Członkowskie zwracają 0.

W swojej [Otwórz](../../mfc/reference/crecordset-class.md#open) wywołania, można:

- Określ, czy zestaw rekordów jest dynamiczny lub migawki. Zestawy rekordów jako migawki domyślnie otwierane przez. Lub można określić zestaw rekordów tylko do przodu, który zezwala na tylko do przodu przewijania, do jednego rekordu w danym momencie.

   Używa domyślnie domyślny typ przechowywane w zestawie rekordów `CRecordset` element członkowski danych `m_nDefaultType`. Kreatorzy napisać kod, aby zainicjować `m_nDefaultType` do typu zestawu rekordów, możesz wybrać w kreatorze. Zamiast przyjmuje ustawienie domyślne, można zastąpić innego typu zestawu rekordów.

- Określ ciąg znaków, aby zastąpić domyślny kod SQL **wybierz** instrukcję, która tworzy zestaw rekordów.

- Określ, czy zestaw rekordów jest tylko do odczytu lub tylko do dołączania. Zestawy rekordów Zezwalaj na pełne, aktualizowanie domyślnie, ale, można ograniczyć do dodawania nowych rekordów tylko lub może nie zezwalaj na wszystkie aktualizacje.

Poniższy przykład pokazuje, jak otworzyć migawkę służącą tylko do odczytu obiektu klasy `CStudentSet`, klasy specyficzne dla aplikacji:

```cpp
// Construct the snapshot object
CStudentSet rsStudent( NULL );
// Set options if desired, then open the recordset
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))
    return FALSE;
// Use the snapshot to operate on its records...
```

Po wywołaniu metody `Open`, użyj członków funkcje i dane Członkowskie obiektu, aby pracować z rekordami. W niektórych przypadkach możesz chcieć Requery — ani nie odświeżaj zestawu rekordów, aby uwzględnić zmiany, które wystąpiły w źródle danych. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: Ponowne wysyłanie zapytania do zestawu rekordów (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).

> [!TIP]
>  Ciąg parametrów połączenia, używane podczas programowania może nie być ten sam ciąg połączenia, który ostatecznej użytkownicy potrzebują. Aby poznać, w związku z tym uogólnianie aplikacji, zobacz [źródła danych: Zarządzanie połączeniami (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md).

##  <a name="_core_setting_recordset_options"></a> Ustawianie opcji zestawu rekordów

Po utworzenia obiektu zestawu rekordów, ale przed wywołaniem `Open` do wybierania rekordów, warto ustawić kilka opcji do sterowania zachowaniem zestawu rekordów. Dla wszystkich zestawów rekordów możesz wykonywać następujące czynności:

- Określ [filtru](../../data/odbc/recordset-filtering-records-odbc.md) ogranicza wybór rekordów.

- Określ [sortowania](../../data/odbc/recordset-sorting-records-odbc.md) kolejność rekordów.

- Określ [parametry](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) , można wybrać rekordy przy użyciu informacji uzyskanych lub obliczane w czasie wykonywania.

Jeśli warunki są odpowiednie, można też ustawić następujące opcje:

- Jeśli zestaw rekordów można aktualizować i obsługuje opcje blokowania, podaj [blokowania](../../data/odbc/recordset-locking-records-odbc.md) metody stosowane przy aktualizacjach.

> [!NOTE]
>  Aby wpłynąć na wybór rekordów, należy ustawić te opcje przed wywołaniem `Open` funkcja elementu członkowskiego.

##  <a name="_core_closing_a_recordset"></a> Zamykanie zestawu rekordów

Po zakończeniu wprowadzania zmian przy użyciu rekordów, należy ją usunąć i cofanie przydziału pamięci.

#### <a name="to-close-a-recordset"></a>Aby zamknąć zestawu rekordów

1. Wywoływanie jej [Zamknij](../../mfc/reference/crecordset-class.md#close) funkcja elementu członkowskiego.

1. Zniszczenie obiektu zestawu rekordów.

   Jeżeli zadeklarowano na ramce stosu funkcji, obiekt jest niszczony automatycznie, gdy obiekt wykracza poza zakres. W przeciwnym razie użyj **Usuń** operatora.

`Close` zwalnia zestawu rekordów `HSTMT` obsługi. Go nie niszczy obiektów C++.

## <a name="see-also"></a>Zobacz także

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: Przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)<br/>
[Zestaw rekordów: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)