---
title: Dynamiczne powiązanie kolumn w dostawcy
ms.date: 11/04/2016
helpviewer_keywords:
- columns [C++], dynamic column binding
- dynamic column binding
- providers [C++], dynamic column binding
ms.assetid: 45e811e3-f5a7-4627-98cc-bf817c4e556e
ms.openlocfilehash: 3c66cf58ce1f8b83b2b3308c8dabba6cf8cdf0ef
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033855"
---
# <a name="dynamically-binding-columns-in-your-provider"></a>Dynamiczne powiązanie kolumn w dostawcy

Upewnij się, że naprawdę potrzebujesz dynamiczne powiązanie kolumn. Możesz go potrzebować, ponieważ:

- Kolumny zestawu wierszy nie są zdefiniowane w czasie kompilacji.

- Obsługujesz element, na przykład zakładki, która dodaje kolumn.

## <a name="to-implement-dynamic-column-binding"></a>Aby zaimplementować dynamiczne powiązanie kolumn

1. Usuń wszystkie `PROVIDER_COLUMN_MAP`s w kodzie.

1. W rekordzie użytkownika (struktura) dodaj następującą deklarację:

    ```cpp
    static ATLCOLUMNINFO* GetColumnInfo(void* pThis, ULONG* pcCols);
    ```

1. Implementowanie `GetColumnInfo` funkcji. Ta funkcja określa się, jak informacje są przechowywane. Konieczne może być pobieranie właściwości lub inne informacje dla tej funkcji. Możesz chcieć utworzyć makro, podobnie jak [COLUMN_ENTRY](../../data/oledb/column-entry.md) makra, aby dodać własne informacje.

   W poniższym przykładzie przedstawiono `GetColumnInfo` funkcji.

    ```cpp
    // Check the property flag for bookmarks, if it is set, set the zero
    // ordinal entry in the column map with the bookmark information.
    CAgentRowset* pRowset = (CAgentRowset*) pThis;
    CComQIPtr<IRowsetInfo, &IID_IRowsetInfo> spRowsetProps = pRowset;

    CDBPropIDSet set(DBPROPSET_ROWSET);
    set.AddPropertyID(DBPROP_BOOKMARKS);
    DBPROPSET* pPropSet = NULL;
    ULONG ulPropSet = 0;
    HRESULT hr;

    if (spRowsetProps)
       hr = spRowsetProps->GetProperties(1, &set, &ulPropSet, &pPropSet);

    if (pPropSet)
    {
       CComVariant var = pPropSet->rgProperties[0].vValue;
       CoTaskMemFree(pPropSet->rgProperties);
       CoTaskMemFree(pPropSet);

       if (SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE))
       {
          ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD), DBTYPE_BYTES,
             0, 0, GUID_NULL, CAgentMan, dwBookmark, DBCOLUMNFLAGS_ISBOOKMARK)
          ulCols++;
       }
    }

    // Next, set up the other columns.
    ADD_COLUMN_ENTRY(ulCols, OLESTR("Command"), 1, 256, DBTYPE_STR, 0xFF, 0xFF,
       GUID_NULL, CAgentMan, szCommand)
    ulCols++;
    ADD_COLUMN_ENTRY(ulCols, OLESTR("Text"), 2, 256, DBTYPE_STR, 0xFF, 0xFF,
       GUID_NULL, CAgentMan, szText)
    ulCols++;

    ADD_COLUMN_ENTRY(ulCols, OLESTR("Command2"), 3, 256, DBTYPE_STR, 0xFF, 0xFF,
       GUID_NULL, CAgentMan, szCommand2)
    ulCols++;
    ADD_COLUMN_ENTRY(ulCols, OLESTR("Text2"), 4, 256, DBTYPE_STR, 0xFF, 0xFF,
       GUID_NULL, CAgentMan, szText2)
    ulCols++;

    if (pcCols != NULL)
       *pcCols = ulCols;

    return _rgColumns;
    }
    ```

## <a name="see-also"></a>Zobacz także

[Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)