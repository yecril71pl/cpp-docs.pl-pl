---
title: Pobieranie danych
ms.date: 10/19/2018
helpviewer_keywords:
- data [C++], fetching
- rowsets [C++], fetching
- fetching
- OLE DB consumer templates [C++], fetching data
ms.assetid: b07f747f-9855-4f27-a03d-b1d5b10fa284
ms.openlocfilehash: 919eb059f5d3f29d491bf7a6598b0c77163bd783
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184647"
---
# <a name="fetching-data"></a>Pobieranie danych

Po otwarciu źródła danych, sesji i obiektów zestawu wierszy można pobrać dane. W zależności od typu używanego akcesora może być konieczne powiązanie kolumn.

## <a name="to-fetch-data"></a>Aby pobrać dane

1. Otwórz zestaw wierszy przy użyciu odpowiedniego polecenia **Otwórz** .

1. Jeśli używasz programu `CManualAccessor` , powiąż kolumny wyjściowe, jeśli jeszcze nie zostało to zrobione. Poniższy przykład jest pobierany z przykładu [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer) . Aby powiązać kolumny, należy wywołać metodę `GetColumnInfo` , a następnie utworzyć metodę dostępu przy użyciu powiązań, jak pokazano w poniższym przykładzie:

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

1. Napisz **`while`** pętlę, aby pobrać dane. W pętli Zadzwoń `MoveNext` do następnego kursora i przetestuj wartość zwracaną względem S_OK, jak pokazano w następującym przykładzie:

    ```cpp
    while (rs.MoveNext() == S_OK)
    {
        // Add code to fetch data here
        // If you are not using an auto accessor, call rs.GetData()
    }
    ```

1. W ramach **`while`** pętli można pobrać dane zgodnie z typem metody dostępu.

   - W przypadku używania klasy [CAccessor](../../data/oledb/caccessor-class.md) należy mieć rekord użytkownika zawierający elementy członkowskie danych. Dostęp do danych można uzyskać przy użyciu tych elementów członkowskich danych, jak pokazano w następującym przykładzie:

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members directly. In this case, m_nFooID
            // is declared in a user record that derives from
            // CAccessor
            wsprintf_s("%d", rs.m_nFooID);
        }
        ```

   - Jeśli używasz `CDynamicAccessor` `CDynamicParameterAccessor` klasy or, możesz pobrać dane przy użyciu funkcji dostępu `GetValue` i `GetColumn` , jak pokazano w poniższym przykładzie. Jeśli chcesz określić typ używanych danych, użyj polecenia `GetType` .

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

   - Jeśli używasz `CManualAccessor` , musisz określić własnych członków danych, powiązać je samodzielnie i uzyskać dostęp do nich bezpośrednio, jak pokazano w następującym przykładzie:

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
