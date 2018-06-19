---
title: 'Zestaw rekordów: Tworzenie i zamykanie zestawów rekordów (ODBC) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bbf020e12151e666aa8f88098865b1624403b828
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092105"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>Zestaw rekordów: tworzenie i zamykanie zestawów rekordów (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 Aby użyć zestawu rekordów, konstruowania obiektu zestawu rekordów, a następnie wywołać jej **Otwórz** funkcji członkowskiej, aby uruchomić zapytanie zestawu rekordów i wybrać rekordy. Po zakończeniu pracy z zestawu rekordów, zamknij i zniszczenia obiektu.  
  
 W tym temacie opisano:  
  
-   [Kiedy i jak można utworzyć obiektu zestawu rekordów](#_core_creating_recordsets_at_run_time).  
  
-   [Kiedy i jak może kwalifikować się zachowanie w zestawie rekordów parametryzacja, filtrowanie, sortowanie i blokowanie go](#_core_setting_recordset_options).  
  
-   [Kiedy i jak zamykać obiekty zestawów rekordów](#_core_closing_a_recordset).  
  
##  <a name="_core_creating_recordsets_at_run_time"></a> Tworzenie zestawów rekordów w czasie wykonywania  
 Przed przystąpieniem do tworzenia rekordów obiektów w programie zwykle zapisu klasy specyficzne dla aplikacji zestawu rekordów. Aby uzyskać więcej informacji dotyczących tego kroku wstępnych, zobacz [Dodawanie konsumenta MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).  
  
 Otwórz obiekt dynamiczny lub gdy musisz wybrać rekordy ze źródła danych. Typ obiektu do utworzenia zależy od tego, co należy zrobić z danych w aplikacji i obsługuje jakie sterownik ODBC. Aby uzyskać więcej informacji, zobacz [dynamiczny](../../data/odbc/dynaset.md) i [migawki](../../data/odbc/snapshot.md).  
  
#### <a name="to-open-a-recordset"></a>Aby otworzyć zestaw rekordów  
  
1.  Utworzenia obiektu z `CRecordset`-klasy.  
  
     Można utworzyć obiektu na stercie lub ramki stosu funkcji.  
  
2.  Opcjonalnie można zmodyfikować domyślne zachowanie zestawu rekordów. Dostępne opcje dla [Ustawianie opcji rekordów](#_core_setting_recordset_options).  
  
3.  Wywołanie obiektu [Otwórz](../../mfc/reference/crecordset-class.md#open) funkcję elementu członkowskiego.  
  
 W konstruktorze, Przekaż wskaźnik do `CDatabase` obiekt lub Przekaż **NULL** do używania tymczasowej obiektu bazy danych, w ramach tworzy i otwiera oparte na zwrócony przez ciąg połączenia [GetDefaultConnect ](../../mfc/reference/crecordset-class.md#getdefaultconnect) funkcję elementu członkowskiego. `CDatabase` Obiekt może być już połączony ze źródłem danych.  
  
 Wywołanie **Otwórz** używa SQL, aby wybrać rekordy ze źródła danych. Pierwszy rekord wybrane (jeśli istnieje) jest bieżącego rekordu. Wartości pól danego rekordu są przechowywane w elementy członkowskie danych pola obiektu zestawu rekordów. Jeśli wybrano rekordy, zarówno `IsBOF` i `IsEOF` Członkowskie zwracają wartość 0.  
  
 W Twojej [Otwórz](../../mfc/reference/crecordset-class.md#open) wywołanie, można wykonywać następujące czynności:  
  
-   Określ, czy zestaw rekordów jest dynamiczny lub migawki. Zestawy rekordów otwórz jako migawki domyślnie. Lub możesz określić zestaw rekordów tylko do przodu, dzięki czemu tylko do przodu przewijanie w jednym rekordzie naraz.  
  
     Zestaw rekordów używa domyślnie przechowywane w domyślnym typem `CRecordset` element członkowski danych **m_nDefaultType**. Kreatorzy napisać kod, aby zainicjować **m_nDefaultType** do typu zestawu rekordów, możesz wybrać w kreatorze. Zamiast akceptowanie to ustawienie domyślne, można użyć innego typu zestawu rekordów.  
  
-   Podaj ciąg, aby zastąpić domyślną SQL **wybierz** instrukcji, która tworzy zestaw rekordów.  
  
-   Określ, czy zestaw rekordów jest tylko do odczytu lub tylko do dołączenia. Zestawy rekordów Zezwalaj pełnej aktualizacji domyślnie, ale który można ograniczyć do dodawania nowych rekordów tylko lub można uniemożliwić wszystkie aktualizacje.  
  
 Poniższy przykład pokazuje, jak można otworzyć obiektu migawki tylko do odczytu klasy `CStudentSet`, klasy specyficzne dla aplikacji:  
  
```  
// Construct the snapshot object  
CStudentSet rsStudent( NULL );  
// Set options if desired, then open the recordset  
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))  
    return FALSE;  
// Use the snapshot to operate on its records...  
```  
  
 Po wywołaniu metody **Otwórz**, pracować z rekordów za pomocą elementu członkowskiego funkcji i danych elementów członkowskich obiektu. W niektórych przypadkach można requery lub Odśwież zestaw rekordów, aby uwzględnić zmiany, które wystąpiły w źródle danych. Aby uzyskać więcej informacji, zobacz [zestaw rekordów: ponowne wysyłanie zapytania do zestawu rekordów (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).  
  
> [!TIP]
>  Ciąg połączenia, używanego podczas tworzenia może nie być tego samego ciąg połączenia, który ostatecznego użytkownicy potrzebują. Aby poznać, w związku z tym uogólnianie aplikacji, zobacz [źródła danych: Zarządzanie połączeniami (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md).  
  
##  <a name="_core_setting_recordset_options"></a> Ustawianie opcji zestawu rekordów  
 Po utworzenia obiektu zestawu rekordów, ale przed wywołaniem **Otwórz** aby wybrać rekordy, można ustawić niektóre opcje kontroli zachowania w zestawie rekordów. Dla wszystkich zestawów rekordów można:  
  
-   Określ [filtru](../../data/odbc/recordset-filtering-records-odbc.md) Aby ograniczyć wybór rekordów.  
  
-   Określ [sortowania](../../data/odbc/recordset-sorting-records-odbc.md) kolejności rekordów.  
  
-   Określ [parametry](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) , można wybrać rekordów przy użyciu informacji uzyskanych lub obliczane w czasie wykonywania.  
  
 Można też ustawić następującą opcję, jeśli warunki są prawidłowe:  
  
-   Zestaw rekordów można aktualizować i obsługuje opcje blokowania, określić [blokowania](../../data/odbc/recordset-locking-records-odbc.md) metodę używaną do aktualizacji.  
  
> [!NOTE]
>  Wpływ na wybór rekordów, należy skonfigurować te opcje przed wywołaniem **Otwórz** funkcję elementu członkowskiego.  
  
##  <a name="_core_closing_a_recordset"></a> Zamykanie zestawu rekordów  
 Po zakończeniu pracy z zestawu rekordów, należy usunąć ją i cofnięcie przydziału pamięci.  
  
#### <a name="to-close-a-recordset"></a>Aby zamknąć zestawu rekordów  
  
1.  Wywołaj jego [Zamknij](../../mfc/reference/crecordset-class.md#close) funkcję elementu członkowskiego.  
  
2.  Zniszczenie obiektu zestawu rekordów.  
  
     Jeżeli zadeklarowano na ramki stosu funkcji, obiekt zostanie zniszczony automatycznie, gdy obiekt wykracza poza zakres. W przeciwnym razie użyj **usunąć** operatora.  
  
 **Zamknij** zwalnia zestawu rekordów **HSTMT** obsługi. Nie niszczy obiektu języka C++.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: Przewijanie (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)   
 [Zestaw rekordów: dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)