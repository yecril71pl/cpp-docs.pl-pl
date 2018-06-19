---
title: Dynamicznie Określanie kolumn zwracanych do konsumenta | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: fd84b6f9451e924fac9e3630df38719c83ff583a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33107942"
---
# <a name="dynamically-determining-columns-returned-to-the-consumer"></a>Dynamicznie określanie kolumn zwracanych do konsumenta
Makra PROVIDER_COLUMN_ENTRY zwykle obsługi **IColumnsInfo::GetColumnsInfo** wywołania. Jednak ponieważ konsumenta, można użyć zakładki, dostawca musi być można zmienić kolumny zwracane w zależności od tego, czy klient pyta o zakładki.  
  
 Do obsługi **IColumnsInfo::GetColumnsInfo** wywołanie, Usuń PROVIDER_COLUMN_MAP, który definiuje funkcję `GetColumnInfo`, z `CAgentMan` użytkownika zarejestrowania w MyProviderRS.h i zastąp go definicji własne `GetColumnInfo` funkcji:  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
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
  
 Następnie należy zaimplementować `GetColumnInfo` działać w MyProviderRS.cpp, jak pokazano w poniższym kodzie.  
  
 `GetColumnInfo` najpierw sprawdza, czy właściwość OLE DB **DBPROP_BOOKMARKS** jest ustawiona. Aby pobrać właściwość, `GetColumnInfo` używa wskaźnika (`pRowset`) do obiektu zestawu wierszy. `pThis` Wskaźnika reprezentuje klasa, która utworzyła zestawu wierszy, które jest klasą przechowywania mapy właściwości. `GetColumnInfo` typecasts `pThis` wskaźnik do `RMyProviderRowset` wskaźnika.  
  
 Aby sprawdzić **DBPROP_BOOKMARKS** właściwości, `GetColumnInfo` używa `IRowsetInfo` interfejsu, który można uzyskać przez wywołanie metody `QueryInterface` na `pRowset` interfejsu. Alternatywnie, można użyć ATL [CComQIPtr](../../atl/reference/ccomqiptr-class.md) metody zamiast tego.  
  
```cpp
////////////////////////////////////////////////////////////////////  
// MyProviderRS.cpp  
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
  
 W tym przykładzie używane statyczne tablica zawiera informacji o kolumnie. Aby klient nie kolumny zakładki, jeden wpis w tablicy jest nieużywany. Aby obsłużyć informacje, należy utworzyć makra macierzy dwa: ADD_COLUMN_ENTRY i ADD_COLUMN_ENTRY_EX. Dodatkowy parametr przyjmuje ADD_COLUMN_ENTRY_EX `flags`, która jest niezbędny w przypadku wyznaczyć kolumnę zakładki.  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
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
  
 W `GetColumnInfo` służy funkcja, makro zakładki następująco:  
  
```  
ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),  
   DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,   
   DBCOLUMNFLAGS_ISBOOKMARK)  
```  
  
 Można teraz skompilować i uruchomić rozszerzoną dostawcy. Aby przetestować dostawcy, zmodyfikuj konsumenta testu zgodnie z opisem w [Implementowanie prostego konsumenta](../../data/oledb/implementing-a-simple-consumer.md). Uruchomić klienta testowego z dostawcą. Sprawdź, czy konsumenta test pobiera odpowiednie ciągi od dostawcy, po kliknięciu **Uruchom** przycisk **Test konsumenta** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Udoskonalanie prostego dostawcy tylko do odczytu](../../data/oledb/enhancing-the-simple-read-only-provider.md)