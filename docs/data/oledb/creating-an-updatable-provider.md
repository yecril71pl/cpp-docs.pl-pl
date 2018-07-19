---
title: Tworzenie aktualizowalnego dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cbcd69168b70e8d85bf2b90c3f456f79cd1c228c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954587"
---
# <a name="creating-an-updatable-provider"></a>Tworzenie aktualizowalnego dostawcy

Visual C++ obsługuje aktualizowalni dostawcy lub dostawców, które można zaktualizować (zapisu) do magazynu danych. W tym temacie omówiono sposób tworzenia aktualizowalni dostawcy za pomocą szablonów OLE DB.  
  
 W tym temacie założono, że rozpoczynasz korzystanie z dostawcy wymagającego. Istnieją dwa kroki, aby tworzenie aktualizowalnego dostawcy. Należy najpierw zdecyduj, jak dostawca wprowadzi zmiany w przechowalni danych; ściślej mówiąc czy zmiany mają być wykonywane od razu lub odroczone do czasu wydano polecenie aktualizacji. Sekcja "[tworzenie aktualizowalnego dostawcy](#vchowmakingprovidersupdatable)" opisano zmiany i ustawienia, które należy wykonać w kodzie dostawcy.  
  
 Następnie należy musi upewnij się, że Twój dostawca zawiera wszystkie funkcje do obsługi wszystkich danych, które użytkownik może zażądać jej. Jeśli użytkownik chce, aby zaktualizować magazynu danych, dostawca musi zawierać kod, który utrzymuje danych do magazynu danych. Na przykład może użyć biblioteki wykonawczej języka C lub MFC do wykonywania takich operacji na źródle danych. Sekcję "[zapisywania źródła danych](#vchowwritingtothedatasource)" opis zapisu w źródle danych, przeciwdziałania `NULL` wartości domyślne i Ustaw flagi kolumny.  
  
> [!NOTE]
>  UpdatePV jest przykładem aktualizowalnego dostawcy. UpdatePV jest taka sama, jak MyProv, ale z obsługą nadaje się do aktualizacji.  
  
##  <a name="vchowmakingprovidersupdatable"></a> Tworzenie aktualizowalnego dostawcy  

 Klucz w tworzenie aktualizowalnego dostawcy jest zrozumienie, jakie operacje ma dostawcy do wykonania w magazynie danych oraz sposób dostawcy w celu przeprowadzania tych operacji. W szczególności poważnym problemem jest, czy aktualizacje do magazynu danych mają być wykonywane od razu lub odroczone (wsadowe) do momentu wydano polecenie aktualizacji.  
  
 Należy najpierw określić, czy chcesz dziedziczyć `IRowsetChangeImpl` lub `IRowsetUpdateImpl` w swojej klasy zestawu wierszy. W zależności od tego, który z nich wybierzesz do zaimplementowania, będzie mieć wpływ na funkcjonalność z trzech metod: `SetData`, `InsertRows`, i `DeleteRows`.  
  
- Jeśli dziedziczą z [irowsetchangeimpl —](../../data/oledb/irowsetchangeimpl-class.md), wywoływanie tych trzech metod natychmiast zmienia się z magazynem danych.  
  
- Jeśli dziedziczą z [irowsetupdateimpl —](../../data/oledb/irowsetupdateimpl-class.md), metody Odrocz zmiany w magazynie danych, dopóki nie zostanie wywołana `Update`, `GetOriginalData`, lub `Undo`. Jeśli aktualizacja obejmuje kilka zmian, są wykonywane w trybie wsadowym (Zauważ, że przetwarzanie wsadowe zmiany można dodać pamięć znaczne obciążenie).  
  
 Należy pamiętać, że `IRowsetUpdateImpl` pochodzi od klasy `IRowsetChangeImpl`. W efekcie `IRowsetUpdateImpl` zapewnia zmienić możliwości, a także możliwości usługi batch.  
  
#### <a name="to-support-updatability-in-your-provider"></a>Do obsługi aktualizacji w dostawcy  
  
1. W klasie wierszy dziedziczyć `IRowsetChangeImpl` lub `IRowsetUpdateImpl`. Te klasy oferują interfejsy odpowiednie zmiany do magazynu danych:  
  
     **Dodawanie IRowsetChange**  
  
     Dodaj `IRowsetChangeImpl` na swój łańcuch dziedziczenia, za pomocą tego formularza:  
  
    ```  
    IRowsetChangeImpl< rowset-name, storage-name >  
    ```  
  
     Również dodać `COM_INTERFACE_ENTRY(IRowsetChange)` do `BEGIN_COM_MAP` sekcji klasy zestawu wierszy.  
  
     **Dodawanie IRowsetUpdate**  
  
     Dodaj `IRowsetUpdate` na swój łańcuch dziedziczenia, za pomocą tego formularza:  
  
    ```  
    IRowsetUpdateImpl< rowset-name, storage>  
    ```  
  
    > [!NOTE]
    >  Należy usunąć `IRowsetChangeImpl` wiersz z swój łańcuch dziedziczenia. To jeden wyjątek od dyrektywy wcześniej wspomniano, musi zawierać kod `IRowsetChangeImpl`.  
  
2.  Dodaj następujący element do mapy COM (`BEGIN_COM_MAP ... END_COM_MAP`):  
  
    |W przypadku zastosowania|Dodaj do mapy COM|  
    |----------------------|--------------------|  
    |`IRowsetChangeImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)`|  
    |`IRowsetUpdateImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)COM_INTERFACE_ENTRY(IRowsetUpdate)`|  
  
3.  W poleceniu, Dodaj następujący element do mapy zestaw właściwości (`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`):  
  
    |W przypadku zastosowania|Dodaj do mapy zestaw właściwości|  
    |----------------------|-----------------------------|  
    |`IRowsetChangeImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`|  
    |`IRowsetUpdateImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)`|  
  
4.  Na mapie zestaw właściwości należy także uwzględnić wszystkie z następujących ustawień, w jakiej występują poniżej:  
  
    ```  
    PROPERTY_INFO_ENTRY_VALUE(UPDATABILITY, DBPROPVAL_UP_CHANGE |   
      DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)  
    PROPERTY_INFO_ENTRY_VALUE(CHANGEINSERTEDROWS, VARIANT_TRUE)  
    PROPERTY_INFO_ENTRY_VALUE(IMMOBILEROWS, VARIANT_TRUE)  
  
    PROPERTY_INFO_ENTRY_EX(OWNINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OWNUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OTHERINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OTHERUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(REMOVEDELETED, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_FALSE, 0)  
    ```  
  
     Można znaleźć wartości użyte w tych wywołań makra, wyszukując w Atldb.h identyfikatory właściwości i wartości (jeśli Atldb.h różni się od dokumentacji online, Atldb.h zastępuje dokumentacji).  
  
    > [!NOTE]
    >  Wiele `VARIANT_FALSE` i `VARIANT_TRUE` ustawienia są wymagane przez Szablony OLE DB; specyfikacji OLE DB mówi ich odczytu/zapisu, ale szablony OLE DB może obsługiwać tylko jedną wartość.  
  
     **W przypadku zaimplementowania irowsetchangeimpl —**  
  
     W przypadku zaimplementowania `IRowsetChangeImpl`, należy ustawić następujące właściwości w dostawcy usługi. Te właściwości są używane głównie do żądania interfejsów za pośrednictwem `ICommandProperties::SetProperties`.  
  
    - `DBPROP_IRowsetChange`: Ustawienie tym automatycznie ustawia `DBPROP_IRowsetChange`.  
  
    - `DBPROP_UPDATABILITY`: Maska bitowa określenie obsługiwanych metod na `IRowsetChange`: `SetData`, `DeleteRows`, lub `InsertRow`.  
  
    - `DBPROP_CHANGEINSERTEDROWS`: Konsument może wywołać `IRowsetChange::DeleteRows` lub `SetData` dla nowo wstawione wiersze.  
  
    - `DBPROP_IMMOBILEROWS`: Zestaw wierszy nie mogli zmienić kolejności wstawionych lub zaktualizowanych wierszy.  
  
     **W przypadku zaimplementowania irowsetupdateimpl —**  
  
     W przypadku zaimplementowania `IRowsetUpdateImpl`, należy ustawić następujące właściwości w dostawcy usługi dodatkowo z ustawieniem dla wszystkich właściwości `IRowsetChangeImpl` wymienionych powyżej:  
  
    - `DBPROP_IRowsetUpdate`.  
  
    - `DBPROP_OWNINSERT`: Musi być READ_ONLY i VARIANT_TRUE.  
  
    - `DBPROP_OWNUPDATEDELETE`: Musi być READ_ONLY i VARIANT_TRUE.  
  
    - `DBPROP_OTHERINSERT`: Musi być READ_ONLY i VARIANT_TRUE.  
  
    - `DBPROP_OTHERUPDATEDELETE`: Musi być READ_ONLY i VARIANT_TRUE.  
  
    - `DBPROP_REMOVEDELETED`: Musi być READ_ONLY i VARIANT_TRUE.  
  
    - `DBPROP_MAXPENDINGROWS`.  
  
        > [!NOTE]
        >  Jeśli obsługujesz powiadomienia, może również być pewne inne właściwości, jak również; zobacz sekcję dotyczącą `IRowsetNotifyCP` dla tej listy.  
  
##  <a name="vchowwritingtothedatasource"></a> Zapisywanie do źródła danych  
 Aby zapoznać się ze źródła danych, należy wywołać `Execute` funkcji. Aby zapisać źródła danych, należy wywołać `FlushData` funkcji. (W ogólnym sensie opróżnienie oznacza, że aby zapisać zmiany wprowadzone do tabeli lub indeksu na dysku).  

