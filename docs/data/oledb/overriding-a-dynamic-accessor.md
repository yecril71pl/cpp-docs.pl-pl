---
title: Zastępowanie dynamicznej metody dostępu
ms.date: 10/19/2018
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
- overriding, dynamic accessors
ms.assetid: cbefd156-6da5-490d-b795-c2d7d874f7ce
ms.openlocfilehash: d46531f2d4075df98081886dfdfd1f2cf65d9948
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209849"
---
# <a name="overriding-a-dynamic-accessor"></a>Zastępowanie dynamicznej metody dostępu

W przypadku korzystania z dynamicznego akcesora, takiego jak `CDynamicAccessor`, polecenie `Open` Metoda automatycznie tworzy metodę dostępu dla Ciebie na podstawie informacji o kolumnie otwartego zestawu wierszy. Można zastąpić dynamiczną metodę dostępu, aby dokładnie kontrolować sposób powiązania kolumn.

Aby zastąpić dynamiczną metodę dostępu, należy przekazać **wartość false** jako ostatni parametr do metody `CCommand::Open`. Uniemożliwia to `Open` automatyczne tworzenie metody dostępu. Następnie można wywoływać `GetColumnInfo` i wywoływać `AddBindEntry` dla każdej kolumny, która ma zostać powiązana. Poniższy kod pokazuje, jak to zrobić:

```cpp
USES_CONVERSION;
double   dblProductID;

CCommand<CDynamicAccessor> product;
// Open the table, passing false to prevent automatic binding
product.Open(session, _T("Select * FROM Products"), NULL, NULL, DBGUID_DEFAULT, false);


ULONG         nColumns;
DBCOLUMNINFO*   pColumnInfo;
// Get the column information from the opened rowset.
product.GetColumnInfo(&nColumns, &pColumnInfo);

// Bind the product ID as a double.
pColumnInfo[0].wType          = DBTYPE_R8;
pColumnInfo[0].ulColumnSize = 8;
product.AddBindEntry(pColumnInfo[0]);

// Bind the product name as it is.
product.AddBindEntry(pColumnInfo[1]);

// Bind the reorder level as a string.
pColumnInfo[8].wType          = DBTYPE_STR;
pColumnInfo[8].ulColumnSize = 10;
product.AddBindEntry(pColumnInfo[8]);

// You have finished specifying the bindings. Go ahead and bind.
product.Bind();
// Free the memory for the column information that was retrieved in
// previous call to GetColumnInfo.
CoTaskMemFree(pColumnInfo);


char*   pszProductName;
char*   pszReorderLevel;
bool   bRC;

// Loop through the records tracing out the information.
while (product.MoveNext() == S_OK)
{
   bRC = product.GetValue(1, &dblProductID);
   pszProductName   = (char*)product.GetValue(2);
   pszReorderLevel  = (char*)product.GetValue(9);

   ATLTRACE(_T("Override = %lf \"%s\" \"%s\"\n"), dblProductID,
      A2T(pszProductName), A2T(pszReorderLevel));
}
```

## <a name="see-also"></a>Zobacz też

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)
