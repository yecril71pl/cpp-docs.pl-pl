---
title: Pobieranie danych
ms.date: 10/19/2018
helpviewer_keywords:
- data [C++], fetching
- rowsets [C++], fetching
- fetching
- OLE DB consumer templates [C++], fetching data
ms.assetid: b07f747f-9855-4f27-a03d-b1d5b10fa284
ms.openlocfilehash: 441f036d1677806e81bc419ec6a45e810e63a34f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651922"
---
# <a name="fetching-data"></a>Pobieranie danych

Po otwarciu źródła danych, sesji i rowset — obiekty można pobrać danych. W zależności od typu dostępu, którego używasz może być konieczne powiązanie kolumn.

## <a name="to-fetch-data"></a>Można pobrać danych

1. Otwórz zestaw wierszy przy użyciu odpowiedniego **Otwórz** polecenia.

1. Jeśli używasz `CManualAccessor`, powiązanie kolumn danych wyjściowych, jeśli jeszcze tego nie zrobiłeś. Poniższy przykład pochodzi z [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer) próbki. Aby powiązać kolumny, należy wywołać `GetColumnInfo`, a następnie utwórz metody dostępu z powiązaniami, jak pokazano w poniższym przykładzie:

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

1. Zapis **podczas** pętli do pobierania danych. W pętli, wywołaj `MoveNext` aby poszerzyć kursor i przetestować wartość zwracaną względem S_OK, jak pokazano w poniższym przykładzie:

    ```cpp
    while (rs.MoveNext() == S_OK)
    {
        // Add code to fetch data here
        // If you are not using an auto accessor, call rs.GetData()
    }
    ```

1. W ramach **podczas** pętli, możesz pobrać dane według typu dostępu.

   - Jeśli używasz [CAccessor](../../data/oledb/caccessor-class.md) klasy, powinny mieć rekord użytkownika, który zawiera elementy członkowskie danych. Jak pokazano w poniższym przykładzie, aby uzyskać dostęp do danych przy użyciu tych składowych danych:

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members directly. In this case, m_nFooID
            // is declared in a user record that derives from
            // CAccessor
            wsprintf_s("%d", rs.m_nFooID);
        }
        ```

   - Jeśli używasz `CDynamicAccessor` lub `CDynamicParameterAccessor` klasy, możesz pobrać dane, używając dostępu do funkcji `GetValue` i `GetColumn`, jak pokazano w poniższym przykładzie. Jeśli chcesz określić typ danych jest używany, należy użyć `GetType`.

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

   - Jeśli używasz `CManualAccessor`, należy określić własne elementy członkowskie danych, powiązać je samodzielnie i uzyskiwać do nich dostęp bezpośrednio, jak pokazano w poniższym przykładzie:

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members you specified in the calls to
            // AddBindEntry.

            wsprintf_s("%s", szFoo);
        }
        ```

## <a name="see-also"></a>Zobacz także

[Praca z szablonami konsumentów OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)
