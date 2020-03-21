---
title: Dynamicznie określanie kolumn zwracanych do konsumenta
ms.date: 10/26/2018
helpviewer_keywords:
- bookmarks [C++], dynamically determining columns
- dynamically determining columns [C++]
ms.assetid: 58522b7a-894e-4b7d-a605-f80e900a7f5f
ms.openlocfilehash: 6b6061fc7da6f4c4dd53ae70a0e2d5ba7ec40023
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079644"
---
# <a name="dynamically-determining-columns-returned-to-the-consumer"></a>Dynamicznie określanie kolumn zwracanych do konsumenta

Makra PROVIDER_COLUMN_ENTRY zwykle obsługują wywołanie `IColumnsInfo::GetColumnsInfo`. Ponieważ jednak odbiorca może wybrać używanie zakładek, dostawca musi mieć możliwość zmiany kolumn zwracanych w zależności od tego, czy użytkownik pyta o zakładkę.

Aby obsłużyć `IColumnsInfo::GetColumnsInfo` wywołanie, Usuń PROVIDER_COLUMN_MAP, który definiuje funkcję `GetColumnInfo`z rekordu użytkownika `CCustomWindowsFile` w polu *niestandardowy*RS. h i zastąp go definicją własnej funkcji `GetColumnInfo`:

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

Następnie Zaimplementuj funkcję `GetColumnInfo` w *niestandardowym*RS. cpp, jak pokazano w poniższym kodzie.

`GetColumnInfo` najpierw sprawdza, czy właściwość OLE DB `DBPROP_BOOKMARKS` jest ustawiona. Aby uzyskać właściwość, `GetColumnInfo` używa wskaźnika (`pRowset`) do obiektu zestawu wierszy. Wskaźnik `pThis` reprezentuje klasę, która utworzyła zestaw wierszy, która jest klasą, w której jest przechowywana Mapa właściwości. `GetColumnInfo` typecasts wskaźnik `pThis` do wskaźnika `RCustomRowset`.

Aby wyszukać Właściwość `DBPROP_BOOKMARKS`, `GetColumnInfo` używa interfejsu `IRowsetInfo`, który można uzyskać, wywołując `QueryInterface` w interfejsie `pRowset`. Alternatywnie, zamiast tego można użyć metody ATL [CComQIPtr](../../atl/reference/ccomqiptr-class.md) .

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

Ten przykład używa tablicy statycznej do przechowywania informacji o kolumnie. Jeśli odbiorca nie powinna mieć kolumny zakładki, jeden wpis w tablicy jest nieużywany. Aby obsłużyć te informacje, należy utworzyć dwa makra tablicowe: ADD_COLUMN_ENTRY i ADD_COLUMN_ENTRY_EX. W przypadku wyznaczania kolumny zakładki ADD_COLUMN_ENTRY_EX przyjmuje dodatkowe *Parametry, które*są potrzebne.

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

W funkcji `GetColumnInfo` makro zakładki jest używane w następujący sposób:

```cpp
ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),
   DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,
   DBCOLUMNFLAGS_ISBOOKMARK)
```

Teraz można skompilować i uruchomić zwiększony dostawca. Aby przetestować dostawcę, należy zmodyfikować konsumenta testowego zgodnie z opisem w temacie [implementowanie prostego konsumenta](../../data/oledb/implementing-a-simple-consumer.md). Uruchom konsumenta testowego u dostawcy i sprawdź, czy konsument testowy pobiera odpowiednie ciągi od dostawcy.

## <a name="see-also"></a>Zobacz też

[Udoskonalanie prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md)<br/>
