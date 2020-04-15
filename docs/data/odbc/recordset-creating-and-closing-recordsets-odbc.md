---
title: 'Zestaw rekordów: tworzenie i zamykanie zestawów rekordów (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
ms.openlocfilehash: 41b1c11e2c820b6e5777e1af426c5e1253ed5468
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367074"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>Zestaw rekordów: tworzenie i zamykanie zestawów rekordów (ODBC)

> [!NOTE]
> Kreator konsumenta odbc MFC nie jest dostępny w programie Visual Studio 2019 i nowszych. Nadal można utworzyć konsumenta ręcznie.

Ten temat dotyczy klas MFC ODBC.

Aby użyć pliku recordset, należy skonstruować `Open` obiekt pliku recordset, a następnie wywołać jego funkcję elementu członkowskiego, aby uruchomić kwerendę i wybrać rekordy. Po zakończeniu z recordset, zamknij i zniszcz obiekt.

W tym temacie wyjaśniono:

- [Kiedy i jak utworzyć obiekt akcesu .](#_core_creating_recordsets_at_run_time)

- [Kiedy i jak można zakwalifikować zachowanie tablicy rekordów, parametryzując, filtrując, sortując lub blokując go.](#_core_setting_recordset_options)

- [Kiedy i jak zamknąć obiekt pliku recordset](#_core_closing_a_recordset).

## <a name="creating-recordsets-at-run-time"></a><a name="_core_creating_recordsets_at_run_time"></a>Tworzenie zestawy rekordów w czasie wykonywania

Przed utworzeniem obiektów pliku recordset w programie zazwyczaj należy napisać klasy programu recordset specyficzne dla aplikacji. Aby uzyskać więcej informacji na temat tego kroku [wstępnego, zobacz Dodawanie konsumenta odbc MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Otwórz obiekt dynaset lub migawka, gdy trzeba wybrać rekordy ze źródła danych. Typ obiektu do utworzenia zależy od tego, co należy zrobić z danymi w aplikacji i od tego, co obsługuje sterownik ODBC. Aby uzyskać więcej informacji, zobacz [Dynaset](../../data/odbc/dynaset.md) i [Migawka](../../data/odbc/snapshot.md).

#### <a name="to-open-a-recordset"></a>Aby otworzyć a recordset

1. Konstruuj `CRecordset`obiekt klasy pochodnej.

   Obiekt można skonstruować na stercie lub na ramce stosu funkcji.

1. Opcjonalnie zmodyfikuj domyślne zachowanie zestawu rekordów. Aby uzyskać dostępne opcje, zobacz [Ustawianie opcji nastawki rekordów](#_core_setting_recordset_options).

1. Wywołanie funkcji [otwartego](../../mfc/reference/crecordset-class.md#open) elementu członkowskiego obiektu.

W konstruktorze przekaż wskaźnik `CDatabase` do obiektu lub przekaż NULL, aby użyć tymczasowego obiektu bazy danych, który struktura konstruuje i otwiera na podstawie ciągu połączenia zwróconego przez funkcję elementu członkowskiego [GetDefaultConnect.](../../mfc/reference/crecordset-class.md#getdefaultconnect) Obiekt `CDatabase` może być już połączony ze źródłem danych.

Wywołanie `Open` użycia sql do wybierania rekordów ze źródła danych. Pierwszym wybranym rekordem (jeśli istnieje) jest bieżący rekord. Wartości pól tego rekordu są przechowywane w członkach danych pola obiektu zestaw rekordów. Jeśli wybrano dowolne rekordy, funkcje `IsBOF` i `IsEOF` elementy członkowskie zwracają 0.

W [otwartym](../../mfc/reference/crecordset-class.md#open) połączeniu możesz:

- Określ, czy zestaw rekordów jest dynaset lub migawki. Zestawy rekordów są domyślnie otwierane jako migawki. Można też określić rekord tylko do przodu, który umożliwia tylko przewijanie do przodu, jeden rekord naraz.

   Domyślnie zestaw rekordów używa domyślnego typu `CRecordset` przechowywanego w człostawowym `m_nDefaultType`danych . Kreatorzy zapisują kod, aby `m_nDefaultType` zainicjować do typu wpisu menedżera rekordów wybranego w kreatorze. Zamiast akceptować tę wartość domyślną, można zastąpić inny typ pliku recordset.

- Określ ciąg, który zastąpi domyślną instrukcję SQL **SELECT,** którą konstruuje zestawie rekordów.

- Określ, czy plik recordset jest tylko do odczytu lub tylko do dołączania. Zestawy rekordów domyślnie zezwalają na pełną aktualizację, ale można ograniczyć to tylko do dodawania nowych rekordów lub nie zezwalać na wszystkie aktualizacje.

W poniższym przykładzie pokazano, jak otworzyć `CStudentSet`obiekt migawki tylko do odczytu klasy , klasa specyficzna dla aplikacji:

```cpp
// Construct the snapshot object
CStudentSet rsStudent( NULL );
// Set options if desired, then open the recordset
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))
    return FALSE;
// Use the snapshot to operate on its records...
```

Po wywołaniu `Open`użyj funkcji członkowskich i elementów członkowskich danych obiektu do pracy z rekordami. W niektórych przypadkach można ponownie podzesliwać lub odświeżyć zestaw rekordów, aby uwzględnić zmiany, które wystąpiły w źródle danych. Aby uzyskać więcej informacji, zobacz [Recordset: Requerying a Recordset (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).

> [!TIP]
> Ciąg połączenia używany podczas tworzenia może nie być tym samym ciągiem połączenia, którego potrzebują użytkownicy. Aby uzyskać pomysły dotyczące uogólniania aplikacji w tym zakresie, zobacz [Źródło danych: Zarządzanie połączeniami (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md).

## <a name="setting-recordset-options"></a><a name="_core_setting_recordset_options"></a>Ustawianie opcji ustawienia akcesu

Po skonstruowaniu obiektu zestawu rekordów, ale przed wywołaniem `Open` wybierania rekordów, można ustawić niektóre opcje, aby kontrolować zachowanie zestawu rekordów. W przypadku wszystkich rekordów można:

- Określ [filtr,](../../data/odbc/recordset-filtering-records-odbc.md) aby ograniczyć wybór rekordu.

- Określ kolejność [sortowania](../../data/odbc/recordset-sorting-records-odbc.md) rekordów.

- Określ [parametry,](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) aby można było wybrać rekordy przy użyciu informacji uzyskanych lub obliczonych w czasie wykonywania.

Można również ustawić następującą opcję, jeśli warunki są odpowiednie:

- Jeśli zestaw rekordów jest aktualizowany i obsługuje opcje blokowania, określ metodę [blokowania](../../data/odbc/recordset-locking-records-odbc.md) używaną do aktualizacji.

> [!NOTE]
> Aby wpłynąć na wybór rekordu, należy `Open` ustawić te opcje przed wywołaniem funkcji elementu członkowskiego.

## <a name="closing-a-recordset"></a><a name="_core_closing_a_recordset"></a>Zamykanie a Recordset

Po zakończeniu z a recordset, należy usunąć go i rozliczyć alokacji jego pamięci.

#### <a name="to-close-a-recordset"></a>Aby zamknąć rekord

1. Wywołanie jego [Zamknij](../../mfc/reference/crecordset-class.md#close) funkcji elementu członkowskiego.

1. Zniszcz obiekt akcesu.

   Jeśli zadeklarowano go w ramce stosu funkcji, obiekt jest niszczony automatycznie, gdy obiekt wykracza poza zakres. W przeciwnym razie użyj operatora **usuwania.**

`Close`zwalnia `HSTMT` uchwyt nazeli. Nie niszczy obiektu C++.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)<br/>
[Zestaw rekordów: dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
