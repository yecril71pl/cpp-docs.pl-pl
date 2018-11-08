---
title: Dynamicznie określanie kolumn zwracanych do konsumenta
ms.date: 10/26/2018
helpviewer_keywords:
- bookmarks [C++], dynamically determining columns
- dynamically determining columns [C++]
ms.assetid: 58522b7a-894e-4b7d-a605-f80e900a7f5f
ms.openlocfilehash: 7db319aa153cb281c8fd8b4eec16972f5ac0c2c9
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265181"
---
# <a name="dynamically-determining-columns-returned-to-the-consumer"></a>Dynamicznie określanie kolumn zwracanych do konsumenta

Makra PROVIDER_COLUMN_ENTRY zwykle obsłużyć `IColumnsInfo::GetColumnsInfo` wywołania. Jednak ponieważ konsumenta wybrać korzystanie z zakładek, dostawca musi mieć możliwość zmiany kolumn zwrócone w zależności od tego, czy użytkownik poprosi o podanie zakładki.

Do obsługi `IColumnsInfo::GetColumnsInfo` wywołania, Usuń PROVIDER_COLUMN_MAP, który definiuje funkcję `GetColumnInfo`, z `CCustomWindowsFile` rekordu użytkownika w *niestandardowe*RS.h i zastąp go własną definicję `GetColumnInfo` Funkcja:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.H
class CCustomWindowsFile
{
public:
   DWORD dwBookmark;
   static const int iSize = 256;
   TCHAR szCommand[iSize];
   TCHAR szText[iSize];
   TCHAR szCommand2[iSize];
   TCHAR szText2[iSize];
  
   static ATLCOLUMNINFO* GetColumnInfo(void* pThis, ULONG* pcCols);
   bool operator==(const CCustomWindowsFile& am)
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
ATLCOLUMNINFO* CCustomWindowsFile::GetColumnInfo(void* pThis, ULONG* pcCols)
{
   static ATLCOLUMNINFO _rgColumns[5];
   ULONG ulCols = 0;
  
   // Check the property flag for bookmarks; if it is set, set the zero 
   // ordinal entry in the column map with the bookmark information.
   CCustomRowset* pRowset = (CCustomRowset*) pThis;
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
         DBTYPE_BYTES, 0, 0, GUID_NULL, CCustomWindowsFile, dwBookmark, 
         DBCOLUMNFLAGS_ISBOOKMARK)
         ulCols++;
      }
   }
  
   // Next, set the other columns up.
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command"), 1, 256, DBTYPE_STR, 0xFF, 0xFF, 
      GUID_NULL, CCustomWindowsFile, szCommand)
   ulCols++;
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text"), 2, 256, DBTYPE_STR, 0xFF, 0xFF, 
      GUID_NULL, CCustomWindowsFile, szText)
   ulCols++;
  
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command2"), 3, 256, DBTYPE_STR, 0xFF, 0xFF, 
      GUID_NULL, CCustomWindowsFile, szCommand2)
   ulCols++;
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text2"), 4, 256, DBTYPE_STR, 0xFF, 0xFF, 
      GUID_NULL, CCustomWindowsFile, szText2)
   ulCols++;
  
   if (pcCols != NULL)
      *pcCols = ulCols;
  
   return _rgColumns;
}
```

W tym przykładzie użyto tablicy statycznej do przechowywania informacji o kolumnie. Jeśli użytkownik nie chce, aby kolumna zakładki, jeden wpis w tablicy jest nieużywany. Aby obsługiwać informacje, należy utworzyć dwa makra tablicy: ADD_COLUMN_ENTRY i ADD_COLUMN_ENTRY_EX. ADD_COLUMN_ENTRY_EX przyjmuje jako dodatkowy parametr *flagi*, która jest wymagane, jeśli należy wyznaczyć kolumna zakładki.

```cpp
////////////////////////////////////////////////////////////////////////  
// CustomRS.h  
  
#define ADD_COLUMN_ENTRY(ulCols, name, ordinal, colSize, type, precision, scale, guid, dataClass, member) \  
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \  
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \  
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \  
   _rgColumns[ulCols].dwFlags = 0; \  
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \  
   _rgColumns[ulCols].wType = (DBTYPE)type; \  
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \  
   _rgColumns[ulCols].bScale = (BYTE)scale; \  
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member);  
  
#define ADD_COLUMN_ENTRY_EX(ulCols, name, ordinal, colSize, type, precision, scale, guid, dataClass, member, flags) \  
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \  
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \  
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \  
   _rgColumns[ulCols].dwFlags = flags; \  
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \  
   _rgColumns[ulCols].wType = (DBTYPE)type; \  
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \  
   _rgColumns[ulCols].bScale = (BYTE)scale; \  
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member); \  
   memset(&(_rgColumns[ulCols].columnid), 0, sizeof(DBID)); \  
   _rgColumns[ulCols].columnid.uName.pwszName = (LPOLESTR)name;  
```

W `GetColumnInfo` służy funkcja i makra zakładki następująco:

```cpp
ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),
   DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,
   DBCOLUMNFLAGS_ISBOOKMARK)
```

Teraz możesz skompilować i uruchomić ulepszony dostawca. Aby przetestować dostawcę, zmodyfikować konsumenta testu, zgodnie z opisem w [Implementowanie prostego konsumenta](../../data/oledb/implementing-a-simple-consumer.md). Uruchom klienta testowego z dostawcą i sprawdź, czy konsumenta test pobiera odpowiednie ciągi od dostawcy.

## <a name="see-also"></a>Zobacz też

[Udoskonalanie prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md)<br/>
