---
title: Dynamicznie Określanie kolumn zwracanych do konsumenta | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/26/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- bookmarks [C++], dynamically determining columns
- dynamically determining columns [C++]
ms.assetid: 58522b7a-894e-4b7d-a605-f80e900a7f5f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a2149c50f4dc8880e20bff2401adf0db46ad6588
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216503"
---
# <a name="dynamically-determining-columns-returned-to-the-consumer"></a>Dynamicznie określanie kolumn zwracanych do konsumenta

Makra PROVIDER_COLUMN_ENTRY zwykle obsłużyć `IColumnsInfo::GetColumnsInfo` wywołania. Jednak ponieważ konsumenta wybrać korzystanie z zakładek, dostawca musi mieć możliwość zmiany kolumn zwrócone w zależności od tego, czy użytkownik poprosi o podanie zakładki.

Do obsługi `IColumnsInfo::GetColumnsInfo` wywołania, Usuń PROVIDER_COLUMN_MAP, który definiuje funkcję `GetColumnInfo`, z `CAgentMan` użytkownika rekord w CustomRS.h i zastąp go własną definicję `GetColumnInfo` funkcji:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.H
class CAgentMan
{
public:
   DWORD dwBookmark;
   TCHAR szCommand[256];
   TCHAR szText[256];
   TCHAR szCommand2[256];
   TCHAR szText2[256];
  
   static ATLCOLUMNINFO* GetColumnInfo(void* pThis, ULONG* pcCols);
   bool operator==(const CAgentMan& am)
   {
      return (lstrcmpi(szCommand, am.szCommand) == 0);
   }
};
```

Następnie należy zaimplementować `GetColumnInfo` działa w programach *niestandardowe*RS.cpp, jak pokazano w poniższym kodzie.

`GetColumnInfo` najpierw sprawdza, czy właściwość OLE DB `DBPROP_BOOKMARKS` jest ustawiona. Pobrać właściwości, `GetColumnInfo` używa wskaźnika (`pRowset`) do obiektu zestawu wierszy. `pThis` Wskaźnika reprezentuje klasę, która utworzony zestaw wierszy, jest to klasa przechowywania map właściwości. `GetColumnInfo` rzutowaniach typu `pThis` wskaźnik do `RCustomRowset` wskaźnika.

Pod kątem `DBPROP_BOOKMARKS` właściwości `GetColumnInfo` używa `IRowsetInfo` interfejs, który można uzyskać przez wywołanie metody `QueryInterface` na `pRowset` interfejsu. Alternatywnie, można użyć ATL [CComQIPtr](../../atl/reference/ccomqiptr-class.md) metody zamiast tego.

```cpp
////////////////////////////////////////////////////////////////////
// CustomRS.cpp
ATLCOLUMNINFO* CAgentMan::GetColumnInfo(void* pThis, ULONG* pcCols)
{
   static ATLCOLUMNINFO _rgColumns[5];
   ULONG ulCols = 0;
  
   // Check the property flag for bookmarks; if it is set, set the zero 
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
         ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD), 
         DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark, 
         DBCOLUMNFLAGS_ISBOOKMARK)
         ulCols++;
      }
   }
  
   // Next, set the other columns up.
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

W tym przykładzie użyto tablicy statycznej do przechowywania informacji o kolumnie. Jeśli użytkownik nie chce, aby kolumna zakładki, jeden wpis w tablicy jest nieużywany. Aby obsługiwać informacje, należy utworzyć dwa makra tablicy: ADD_COLUMN_ENTRY i ADD_COLUMN_ENTRY_EX. ADD_COLUMN_ENTRY_EX przyjmuje jako dodatkowy parametr *flagi*, która jest wymagane, jeśli należy wyznaczyć kolumna zakładki.

```cpp
ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),
   DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,
   DBCOLUMNFLAGS_ISBOOKMARK)
```

Teraz możesz skompilować i uruchomić ulepszony dostawca. Aby przetestować dostawcę, zmodyfikować konsumenta testu, zgodnie z opisem w [Implementowanie prostego konsumenta](../../data/oledb/implementing-a-simple-consumer.md). Uruchom klienta testowego z dostawcą. Sprawdź, czy odbiorcy test pobiera odpowiednie ciągi od dostawcy, po kliknięciu **Uruchom** znajdujący się w **Test konsumenta** okno dialogowe.

## <a name="see-also"></a>Zobacz też

[Udoskonalanie prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md)<br/>
