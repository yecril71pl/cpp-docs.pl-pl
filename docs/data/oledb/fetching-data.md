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
ms.openlocfilehash: 05cfcb59100f1778b0266636fb3930fd9489e917
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067080"
---
# <a name="fetching-data"></a>Pobieranie danych

Po otwarciu źródła danych, sesji i rowset — obiekty można pobrać danych. W zależności od typu dostępu, którego używasz może być konieczne powiązanie kolumn.  
  
### <a name="to-fetch-data"></a>Można pobrać danych  
  
1. Otwórz zestaw wierszy przy użyciu odpowiedniego **Otwórz** polecenia.  
  
1. Jeśli używasz `CManualAccessor`, powiąż kolumny wyjściowe, jeśli nie zostały już wykonane. Aby powiązać kolumny, należy wywołać `GetColumnInfo`, a następnie utwórz metody dostępu z powiązaniami, jak pokazano w poniższym przykładzie:  
  
    ```cpp  
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
  
1. Zapis `while` pętli do pobierania danych. W pętli, wywołaj `MoveNext` aby poszerzyć kursor i przetestować wartość zwracaną względem S_OK, jak pokazano w poniższym przykładzie:  
  
    ```cpp  
    while (rs.MoveNext() == S_OK)  
    {  
        // Add code to fetch data here  
        // If you are not using an auto accessor, call rs.GetData()  
    }  
    ```  
  
1. W ramach `while` pętli, możesz pobrać dane według typu dostępu.  
  
    -   Jeśli używasz [CAccessor](../../data/oledb/caccessor-class.md) klasy, powinny mieć rekord użytkownika, który zawiera elementy członkowskie danych. Jak pokazano w poniższym przykładzie, aby uzyskać dostęp do danych przy użyciu tych składowych danych:  
  
        ```cpp  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the data members directly. In this case, m_nFooID  
            // is declared in a user record that derives from  
            // CAccessor  
            wsprintf_s("%d", rs.m_nFooID);   
        }  
        ```  
  
    -   Jeśli używasz `CDynamicAccessor` lub `CDynamicParameterAccessor` klasy, możesz pobrać dane, używając dostępu do funkcji `GetValue` i `GetColumn`, jak pokazano w poniższym przykładzie. Jeśli chcesz określić typ danych używasz, należy użyć `GetType`.  
  
        ```cpp  
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
  
    -   Jeśli używasz `CManualAccessor`, należy określić własne elementy członkowskie danych, powiązać je samodzielnie i uzyskiwać do nich dostęp bezpośrednio, jak pokazano w poniższym przykładzie:  
  
        ```cpp  
        while (rs.MoveNext() == S_OK)  
        {  
            // Use the data members you specified in the calls to  
            // AddBindEntry.  
  
            wsprintf_s("%s", szFoo);  
        }  
        ```  
  
## <a name="see-also"></a>Zobacz też  

[Praca z szablonami konsumentów OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)