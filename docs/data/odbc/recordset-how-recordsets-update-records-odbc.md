---
title: "Zestaw rekordów: Jak zestawy rekordów aktualizują rekordy (ODBC) | Dokumentacja firmy Microsoft"
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
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e38f2e62e9aa7b01680e9b2fd1e4a540ee552c3c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>Zestaw rekordów: jak zestawy rekordów aktualizują rekordy (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 Oprócz ich możliwości, aby wybrać rekordy ze źródła danych zestawy rekordów (opcjonalnie) zaktualizować lub usunąć wybrane rekordy lub dodawanie nowych rekordów. Trzech czynników ustalić, czy można aktualizować zestaw rekordów: Określa, czy można aktualizować jest połączonego źródła danych, opcje, można określić podczas tworzenia obiektu zestawu rekordów i SQL Server, który jest tworzony.  
  
> [!NOTE]
>  SQL, na którym Twojej `CRecordset` opiera się obiekt może mieć wpływ na czy można aktualizować w zestawie rekordów. Na przykład jeśli Twoje SQL zawiera sprzężenie lub a **GROUP BY** ustawia MFC klauzuli, czy można aktualizować **FALSE**.  
  
> [!NOTE]
>  Ten temat dotyczy obiektów pochodzących od `CRecordset` w wiersz, który zbiorczego pobierania nie została zaimplementowana. Jeśli korzystasz z zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 W tym temacie opisano:  
  
-   [Twoja rola w aktualizowania rekordów](#_core_your_role_in_recordset_updating) i ramach jest dla Ciebie.  
  
-   [Zestaw rekordów jako bufor edycji](#_core_the_edit_buffer) i [różnice między zestawów dynamicznych i migawki](#_core_dynasets_and_snapshots).  
  
 [Zestaw rekordów: Jak AddNew, Edit i usunąć pracy (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) opisuje akcje te funkcje z punktu widzenia zestawu rekordów.  
  
 [Zestaw rekordów: Więcej o aktualizacje (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) kończy wyjaśniający, jak transakcje wpływają na aktualizacje, wpływ aktualizacji Trwa zamykanie zestawu rekordów lub przewijanie i interakcje aktualizacje z aktualizacji innych wątków aktualizacji rekordów Użytkownicy.  
  
##  <a name="_core_your_role_in_recordset_updating"></a>Twoja rola w aktualizowania rekordów  
 W poniższej tabeli przedstawiono roli użytkownika za pomocą zestawów rekordów można dodać, edytować lub usuwać rekordy oraz platformę jest dla Ciebie.  
  
### <a name="recordset-updating-you-and-the-framework"></a>Aktualizowanie zestaw rekordów: Użytkownik i struktura  
  
|Można|Platformę|  
|---------|-------------------|  
|Ustal, czy źródło danych jest można aktualizować (lub appendable).|Dostaw [cdatabase —](../../mfc/reference/cdatabase-class.md) funkcji elementów członkowskich do testowania, czy można aktualizować lub appendability źródła danych.|  
|Otwórz nadaje się do aktualizacji zestawu rekordów (dowolnego typu).||  
|Określić, czy zestaw rekordów jest nadaje się do aktualizacji, wywołując `CRecordset` aktualizacji funkcji, takich jak `CanUpdate` lub `CanAppend`.||  
|Wywołanie funkcji Członkowskich do dodawania, edytowania i usuwania rekordów zestawu rekordów.|Zarządza mechanika wymiany danych między obiektu zestawu rekordów a źródłem danych.|  
|Opcjonalnie użyj transakcji, aby kontrolować proces aktualizacji.|Dostaw `CDatabase` funkcji elementów członkowskich do obsługi transakcji.|  
  
 Aby uzyskać więcej informacji na temat transakcji, zobacz [transakcja (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="_core_the_edit_buffer"></a>Bufor edycji  
 Podjęta zbiorczo, elementy członkowskie danych pola rekordów służyć jako bufor edycji, który zawiera jeden rekord — bieżącego rekordu. Operacje aktualizacji stosowanie tego buforu do obsługi bieżącego rekordu.  
  
-   Po dodaniu rekordu buforu edycji jest używany do tworzenia nowego rekordu. Po dodaniu rekordu rekordu, który został wcześniej bieżącego staje się bieżącym ponownie.  
  
-   Po zaktualizowaniu buforu (Edytuj) rekord Edycja służy do Ustaw elementy członkowskie danych pola zestawu rekordów do nowej wartości. Po zakończeniu aktualizowania zaktualizowany rekord jest wciąż aktualne.  
  
 Podczas wywoływania [AddNew](../../mfc/reference/crecordset-class.md#addnew) lub [Edytuj](../../mfc/reference/crecordset-class.md#edit), są przechowywane bieżącego rekordu, więc można go przywrócić później w razie potrzeby. Podczas wywoływania [usunąć](../../mfc/reference/crecordset-class.md#delete), bieżący rekord nie jest przechowywana, ale zostaną oznaczone jako usunięte i należy przewiń do innego rekordu.  
  
> [!NOTE]
>  Bufor edycji pełni żadnej roli w usuwania rekordów. Usunięcie bieżącego rekordu rekord jest oznaczone jako usunięte, a zestaw rekordów nie znajduje się "na"rekordu do momentu przewiń do innego rekordu.  
  
##  <a name="_core_dynasets_and_snapshots"></a>Zestawy dynamiczne i migawki  
 [Zestawy dynamiczne](../../data/odbc/dynaset.md) odświeżyć zawartość rekordu przewijania w rekordzie. [Migawki](../../data/odbc/snapshot.md) są statyczne oświadczenia rekordów, więc zawartość rekordu nie są odświeżane, chyba że wywołujesz [Requery](../../mfc/reference/crecordset-class.md#requery). Aby korzystać z funkcji z zestawów dynamicznych, jest możliwe za pośrednictwem sterownika ODBC zgodny odpowiedniego poziomu obsługi interfejsu API ODBC. Aby uzyskać więcej informacji, zobacz [ODBC](../../data/odbc/odbc-basics.md) i [dynamiczny](../../data/odbc/dynaset.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: jak działają funkcje AddNew, Edit i Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)