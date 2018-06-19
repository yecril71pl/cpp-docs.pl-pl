---
title: Pobieranie danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data [C++], fetching
- rowsets [C++], fetching
- fetching
- OLE DB consumer templates [C++], fetching data
ms.assetid: b07f747f-9855-4f27-a03d-b1d5b10fa284
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ab03da7c303552a715c6766af7829e74025866ed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101204"
---
# <a name="fetching-data"></a>Pobieranie danych
Po otwarciu źródła danych, sesji i rowset — obiekty można pobrać danych. W zależności od typu dostępu, którego używasz może być konieczne powiązać kolumny.  
  
### <a name="to-fetch-data"></a>Można pobrać danych  
  
1.  Otwórz wierszy za pomocą odpowiedniej **Otwórz** polecenia.  
  
2.  Jeśli używasz `CManualAccessor`, powiązanie kolumn danych wyjściowych, jeśli nie ma jeszcze zrobione. Aby powiązać kolumny, należy wywołać `GetColumnInfo`, a następnie utwórz metody dostępu z powiązaniami, jak pokazano w poniższym przykładzie:  
  
    ```  
    // From the DBViewer Sample CDBTreeView::OnQueryEdit  
    // Get the column information  
    ULONG ulColumns       = 0;  
    DBCOLUMNINFO* pColumnInfo  = NULL;  
    LPOLESTR pStrings      = NULL;  
    if (rs.GetColumnInfo(&ulColumns, &pColumnInfo, &pStrings) != S_OK)  
        ThrowMyOLEDBException(rs.m_pRowset, IID_IColumnsInfo);  
    struct MYBIND* pBind = new MYBIND[ulColumns];  
    rs.CreateAccessor(ulColumns, &pBind[0], sizeof(MYBIND)*ulColumns);  
    for (ULONG l=0; l<ulColumns; l++)  
    rs.AddBindEntry(l+1, DBTYPE_STR, sizeof(TCHAR)*40, &pBind[l].szValue, NULL, &pBind[l].dwStatus);  
    rs.Bind();  
    ```  
  
3.  Zapis `while` pętli do pobierania danych. W pętli, wywołaj `MoveNext` wyprzedzeniem kursor i przetestować wartości zwracanej przed S_OK, jak pokazano w poniższym przykładzie:  
  
    ```  
    while (rs.MoveNext() == S_OK)  
    {  
        // Add code to fetch data here  
        // If you are not using an auto accessor, call rs.GetData()  
    }  
    ```  
  
4.  W ramach `while` pętli, można pobrać danych zgodnie z danego typu metody dostępu.  
  
    -   Jeśli używasz [CAccessor](../../data/oledb/caccessor-class.md) klasy, powinien mieć rekord użytkownika, który zawiera elementy członkowskie danych. Aby dostęp do danych przy użyciu tych elementów członkowskich danych, jak pokazano w poniższym przykładzie:  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the data members directly. In this case, m_nFooID  
            // is declared in a user record that derives from  
            // CAccessor  
            wsprintf_s("%d", rs.m_nFooID);   
        }  
        ```  
  
    -   Jeśli używasz `CDynamicAccessor` lub `CDynamicParameterAccessor` klasy, można pobrać danych za pomocą funkcji podczas uzyskiwania dostępu do `GetValue` i `GetColumn`, jak pokazano w poniższym przykładzie. Jeśli chcesz określić typ danych są używane, należy użyć `GetType`.  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the dynamic accessor functions to retrieve your data.  
  
            ULONG ulColumns = rs.GetColumnCount();  
            for (ULONG i=0; i<ulColumns; i++)  
            {  
                rs.GetValue(i);  
            }  
        }  
        ```  
  
    -   Jeśli używasz `CManualAccessor`, należy określić własne elementy członkowskie danych, powiązać samodzielnie i uzyskiwać do nich dostęp, jak pokazano w poniższym przykładzie:  
  
        ```  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the data members you specified in the calls to  
            // AddBindEntry.  
  
            wsprintf_s("%s", szFoo);  
        }  
        ```  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z szablonami konsumentów OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)