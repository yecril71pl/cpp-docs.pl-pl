---
title: "Zestaw rekordów: Ponowne wysyłanie zapytania do zestawu rekordów (ODBC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1445273d29fc521b24fbf04ffc5abec1fadd4e59
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-requerying-a-recordset-odbc"></a>Zestaw rekordów: ponowne wysyłanie zapytania do zestawu rekordów (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 W tym temacie wyjaśniono, jak można obiekty zestawów rekordów requery (to znaczy Odśwież) z bazy danych i chcesz to zrobić z [Requery](../../mfc/reference/crecordset-class.md#requery) funkcję elementu członkowskiego.  
  
 Główne powody ponowne wysyłanie zapytania do zestawu rekordów są:  
  
-   Przełącz rekordów aktualne względem dodane przez użytkownika lub przez innych użytkowników rekordów i rekordy zostały usunięte przez innych użytkowników (te, które należy usunąć są już uwzględnione w zestawie danych).  
  
-   Odśwież zestawu rekordów opartego na zmianę wartości parametru.  
  
##  <a name="_core_bringing_the_recordset_up_to_date"></a>Przywracanie w górę rekordów do daty  
 Często warto requery nazwę obiektu zestawu rekordów, aby przenieść ją do aktualne. W środowisku wielodostępnym bazy danych innych użytkownicy mogą wprowadzać zmiany do danych w okresie obowiązywania zestawu rekordów. Aby uzyskać więcej informacji na temat po zestawu rekordów odzwierciedla zmiany wprowadzone przez innych użytkowników i gdy inni użytkownicy zestawów rekordów odzwierciedlać wprowadzone zmiany, zobacz [zestaw rekordów: jak zestawy rekordów aktualizacji rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) i [dynamiczny](../../data/odbc/dynaset.md).  
  
##  <a name="_core_requerying_based_on_new_parameters"></a>Ponowne wysyłanie zapytania na podstawie nowych parametrów  
 Inny częste — i równie ważne — użycie [Requery](../../mfc/reference/crecordset-class.md#requery) , należy wybrać nowy zestaw rekordów w oparciu o zmiany wartości parametrów.  
  
> [!TIP]
>  Szybkość zapytania jest prawdopodobnie znacznie szybsze, jeśli wywołujesz **Requery** ze zmianą wartości parametrów niż Jeśli wywołujesz **Otwórz** ponownie.  
  
##  <a name="_core_requerying_dynasets_vs.._snapshots"></a>Ponowne wysyłanie zapytania vs zestawów dynamicznych. Migawki  
 Zestawy dynamiczne są przeznaczone do wyświetlania zestawu rekordów z danymi dynamicznymi aktualne, chcesz requery zestawów dynamicznych często, jeśli chcesz odzwierciedlić dodatki do innych użytkowników. Migawki, z drugiej strony są przydatne, ponieważ można bezpiecznie polegać na ich zawartości statycznej podczas przygotowania raportów, obliczeń i tak dalej. Nadal czasami może być requery również migawki. W środowisku wielodostępnym migawki danych może spowodować utratę synchronizacji ze źródłem danych w innych użytkowników zmiany bazy danych.  
  
#### <a name="to-requery-a-recordset-object"></a>Aby requery obiekty zestawów rekordów  
  
1.  Wywołanie [Requery](../../mfc/reference/crecordset-class.md#requery) funkcji członkowskiej klasy obiektu.  
  
 Alternatywnie możesz zamknąć i ponownie otworzyć oryginalny zestaw rekordów. W obu przypadkach nowych rekordów reprezentuje bieżący stan źródła danych.  
  
 Na przykład zobacz [widoków rekordów: wypełnianie pola listy z drugiego zestawu wierszy](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).  
  
> [!TIP]
>  Aby zoptymalizować **Requery** wydajności, należy unikać zmiany w zestawie rekordów [filtru](../../data/odbc/recordset-filtering-records-odbc.md) lub [sortowania](../../data/odbc/recordset-sorting-records-odbc.md). Zmień wartość w parametru przed wywołaniem **Requery**.  
  
 Jeśli **Requery** wywołanie się nie powiedzie, można ponowić próby połączenia; w przeciwnym razie aplikacji należy zakończyć bezpiecznie zamknąć. Wywołanie **Requery** lub **Otwórz** może zakończyć się niepowodzeniem dla każdego z kilku powodów. Być może występuje błąd sieciowy; lub podczas wywołania po wydaniu istniejących danych, ale przed nowe dane są uzyskiwane, inny użytkownik może uzyskać wyłączny dostęp; lub można go usunąć tabeli, od którego zależy zestawu rekordów.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: Dynamiczne wiązanie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)   
 [Zestaw rekordów: tworzenie i zamykanie zestawów rekordów (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)