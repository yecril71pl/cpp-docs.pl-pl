---
title: "Tworzenie konsumenta bez użycia kreatora | Dokumentacja firmy Microsoft"
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
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a61de0a4621f6f9387da23093f9f450749129ac3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>Tworzenie konsumenta bez użycia kreatora
W poniższym przykładzie założono do istniejącego projektu ATL dodajesz Obsługa konsumenta OLE DB. Jeśli chcesz dodać obsługę konsumenta OLE DB do aplikacji MFC, należy uruchomić Kreator aplikacji MFC, która tworzy niezbędne pomocy technicznej i wywołuje MFC procedury niezbędne do wykonywania aplikacji.  
  
 Aby dodać obsługę konsumenta OLE DB bez użycia OLE DB Kreator konsumenta ATL:  
  
-   W pliku Stdafx.h Dołącz następujące `#include` instrukcji:  
  
    ```  
    #include <atlbase.h>  
    #include <atldbcli.h>  
    #include <atldbsch.h> // if you are using schema templates  
    ```  
  
 Programowo konsumenta przeważnie wykonuje następujące kolejność operacji:  
  
-   Tworzenie klasy rekordu użytkownika, który wiąże kolumn do zmiennych lokalnych. W tym przykładzie `CMyTableNameAccessor` jest klasy rekordów użytkowników (zobacz [rekordów użytkowników](../../data/oledb/user-records.md)). Ta klasa zawiera mapowania kolumn i parametr mapy. Deklaruje element członkowski danych klasy rekordu użytkownika, dla każdego pola, które określisz na mapie kolumny; dla każdego z tych elementów członkowskich danych deklarować także członkiem danych stanu i długość elementu członkowskiego danych. Aby uzyskać więcej informacji, zobacz [elementy członkowskie dotyczących stanu pola w metodach dostępu Wizard-Generated](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).  
  
    > [!NOTE]
    >  Jeśli piszesz własne konsumenta, zmiennych danych musi występować przed zmienne stanu i długości.  
  
-   Utworzenie wystąpienia źródła danych i sesji. Jakiego typu metody dostępu i zestawu wierszy zdecydować, a następnie utworzyć wystąpienia przy użyciu zestawu wierszy [CCommand](../../data/oledb/ccommand-class.md) lub [CTable](../../data/oledb/ctable-class.md):  
  
    ```  
    CDataSource ds;  
    CSession ss;  
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>  
    ```  
  
-   Wywołanie **CoInitialize** zainicjować modelu COM. Zazwyczaj jest to główny kodu. Na przykład:  
  
    ```  
    HRESULT hr = CoInitialize(NULL);  
    ```  
  
-   Wywołanie [CDataSource::Open](../../data/oledb/cdatasource-open.md) lub jednego z jego zmiany.  
  
-   Otwórz połączenie ze źródłem danych, otwórz sesję i otwórz zainicjować zestawu wierszy (i jeśli polecenie również wykonać go):  
  
    ```  
    hr = ds.Open();  
    hr = ss.Open(ds);  
    hr = rs.Open();            // (Open also executes the command)  
    ```  
  
-   Opcjonalnie wierszy zestaw właściwości za pomocą `CDBPropSet::AddProperty` i przekazać je jako parametr `rs.Open`. Na przykład, jak to zrobić, zobacz GetRowsetProperties w [metody Consumer Wizard-Generated](../../data/oledb/consumer-wizard-generated-methods.md).  
  
-   Można teraz używać zestawu wierszy pobierania/operacje na danych.  
  
-   Po zakończeniu aplikacji, zamknij połączenie sesji i zestawu wierszy:  
  
    ```  
    rs.Close();  
    ss.Close();  
    ds.Close();  
    ```  
  
     Jeśli używane są polecenia, można wywołać `ReleaseCommand` po **Zamknij**. Przykładowy kod w [CCommand::Close](../../data/oledb/ccommand-close.md) pokazuje sposób wywoływania **Zamknij** i `ReleaseCommand`.  
  
-   Wywołanie **CoUnInitialize** do uninitialize modelu COM. Zazwyczaj jest to główny kodu.  
  
    ```  
    CoUninitialize();  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie konsumenta OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)