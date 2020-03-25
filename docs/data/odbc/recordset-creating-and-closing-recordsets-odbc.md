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
ms.openlocfilehash: 155b51debfb6eacd3cbdd3293875274ca2dc4ab5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212982"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>Zestaw rekordów: tworzenie i zamykanie zestawów rekordów (ODBC)

> [!NOTE]
> Kreator użytkownika ODBC MFC nie jest dostępny w programie Visual Studio 2019 i nowszych. Nadal można utworzyć konsumenta ręcznie.

Ten temat dotyczy klas MFC ODBC.

Aby użyć zestawu rekordów, Utwórz obiekt zestawu rekordów, a następnie Wywołaj jego `Open` funkcję członkowską, aby uruchomić zapytanie zestawu rekordów i wybrać pozycję rekordy. Po zakończeniu pracy z zestawem rekordów Zamknij i zniszcz obiekt.

W tym temacie objaśniono:

- [Kiedy i jak utworzyć obiekt zestawu rekordów](#_core_creating_recordsets_at_run_time).

- [Kiedy i jak można zakwalifikować działanie zestawu rekordów przez parametryzacja, filtrowanie, sortowanie lub blokowanie](#_core_setting_recordset_options).

- [Kiedy i jak zamknąć obiekt zestawu rekordów](#_core_closing_a_recordset).

##  <a name="creating-recordsets-at-run-time"></a><a name="_core_creating_recordsets_at_run_time"></a>Tworzenie zestawów rekordów w czasie wykonywania

Przed utworzeniem obiektów zestawu rekordów w programie zazwyczaj należy napisać klasy zestawu rekordów specyficzne dla aplikacji. Aby uzyskać więcej informacji o tym kroku wstępnym, zobacz [Dodawanie użytkownika MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Otwórz obiekt dynamiczny lub migawek, gdy musisz wybrać rekordy ze źródła danych. Typ tworzonego obiektu zależy od tego, co należy zrobić z danymi w aplikacji, oraz od tego, co obsługuje sterownik ODBC. Aby uzyskać więcej informacji, zobacz [zestaw dynamiczny](../../data/odbc/dynaset.md) i [migawka](../../data/odbc/snapshot.md).

#### <a name="to-open-a-recordset"></a>Aby otworzyć zestaw rekordów

1. Konstruowanie obiektu klasy pochodnej `CRecordset`.

   Można skonstruować obiekt na stercie lub w ramce stosu funkcji.

1. Opcjonalnie zmodyfikuj domyślne zachowanie zestawu rekordów. Aby uzyskać dostęp do dostępnych opcji, zobacz [Ustawianie opcji zestawu rekordów](#_core_setting_recordset_options).

1. Wywołaj funkcję [otwierającego](../../mfc/reference/crecordset-class.md#open) elementu członkowskiego obiektu.

W konstruktorze Przekaż wskaźnik do obiektu `CDatabase` lub przekaż wartość NULL, aby użyć obiektu tymczasowej bazy danych, który jest konstrukcja i otwierany przez platformę na podstawie parametrów połączenia zwracanych przez funkcję członkowską [GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) . Obiekt `CDatabase` może już być połączony ze źródłem danych.

Wywołanie `Open` używa języka SQL do wybierania rekordów ze źródła danych. Pierwszy wybrany rekord (jeśli istnieje) jest bieżącym rekordem. Wartości pól tego rekordu są przechowywane w elementach członkowskich danych pola obiektu recordset. W przypadku wybrania dowolnego rekordu zarówno funkcje członkowskie `IsBOF`, jak i `IsEOF` zwracają 0.

W [otwartym](../../mfc/reference/crecordset-class.md#open) wywołaniu można:

- Określ, czy zestaw rekordów jest typu dynamiczny, czy migawką. Domyślnie zestawy rekordów są otwierane jako migawki. Lub można określić zestaw rekordów tylko do przodu, który umożliwia przewijanie tylko do przodu, po jednym rekordzie.

   Domyślnie zestaw rekordów używa typu domyślnego przechowywanego w `m_nDefaultType`składowej danych `CRecordset`. Kreatorzy zapisują kod w celu zainicjowania `m_nDefaultType` do typu zestawu rekordów wybranego w kreatorze. Zamiast zaakceptowania tego ustawienia domyślnego można zastąpić inny typ zestawu rekordów.

- Określ ciąg, który ma zastąpić domyślną instrukcję **SELECT** języka SQL, którą tworzy zestaw rekordów.

- Określ, czy zestaw rekordów jest tylko do odczytu, czy tylko do dołączania. Zestawy rekordów domyślnie zezwalają na pełne aktualizowanie, ale można ograniczyć Dodawanie tylko nowych rekordów lub uniemożliwić wszystkie aktualizacje.

Poniższy przykład pokazuje, jak otworzyć obiekt migawki tylko do odczytu klasy `CStudentSet`, klasy specyficznej dla aplikacji:

```cpp
// Construct the snapshot object
CStudentSet rsStudent( NULL );
// Set options if desired, then open the recordset
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))
    return FALSE;
// Use the snapshot to operate on its records...
```

Po wywołaniu `Open`Użyj funkcji elementów członkowskich i elementów członkowskich danych obiektu do pracy z rekordami. W niektórych przypadkach może być konieczne ponowne wykonanie kwerendy lub odświeżenie zestawu rekordów w celu uwzględnienia zmian, które wystąpiły w źródle danych. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: przeszukiwanie zestawu rekordów (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).

> [!TIP]
>  Ciąg połączenia używany podczas opracowywania może nie być tym samym ciągiem połączenia, który jest wymagany przez użytkowników. Aby poznać pomysły dotyczące uogólniania aplikacji w tym zakresie, zobacz [Źródło danych: Zarządzanie połączeniami (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md).

##  <a name="setting-recordset-options"></a><a name="_core_setting_recordset_options"></a>Ustawianie opcji zestawu rekordów

Po utworzeniu obiektu zestawu rekordów, ale przed wywołaniem `Open` w celu wybrania rekordów, można ustawić pewne opcje sterujące zachowaniem zestawu rekordów. Dla wszystkich zestawów rekordów można:

- Określ [Filtr](../../data/odbc/recordset-filtering-records-odbc.md) , aby ograniczyć wybór rekordu.

- Określ kolejność [sortowania](../../data/odbc/recordset-sorting-records-odbc.md) rekordów.

- Określ [Parametry](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) , aby można było wybierać rekordy przy użyciu informacji uzyskanych lub obliczanych w czasie wykonywania.

Możesz również ustawić następującą opcję, jeśli warunki są prawidłowe:

- Jeśli zestaw rekordów jest aktualizowalny i obsługuje opcje blokowania, Określ metodę [blokowania](../../data/odbc/recordset-locking-records-odbc.md) używaną dla aktualizacji.

> [!NOTE]
>  Aby mieć wpływ na wybór rekordów, należy ustawić te opcje przed wywołaniem funkcji składowej `Open`.

##  <a name="closing-a-recordset"></a><a name="_core_closing_a_recordset"></a>Zamykanie zestawu rekordów

Po zakończeniu pracy z zestawem rekordów należy usunąć go i cofnąć jego ilość.

#### <a name="to-close-a-recordset"></a>Aby zamknąć zestaw rekordów

1. Wywoływanie funkcji [zamykającej](../../mfc/reference/crecordset-class.md#close) elementu członkowskiego.

1. Zniszcz obiekt zestawu rekordów.

   Jeśli zadeklarowano ją w ramce stosu funkcji, obiekt zostanie zniszczony automatycznie, gdy obiekt wykracza poza zakres. W przeciwnym razie użyj operatora **delete** .

`Close` zwalnia uchwytu `HSTMT` zestawu rekordów. Nie niszczy C++ obiektu.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Zestaw rekordów: przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)<br/>
[Zestaw rekordów: dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
