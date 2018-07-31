---
title: Obsługa dostawców dla zakładek | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IRowsetLocate class, provider support for bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- IRowsetLocate class
- OLE DB providers, bookmark support
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b16605b8cd0b5855d7a6cc1f5ceac9f46ad495f4
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337634"
---
# <a name="provider-support-for-bookmarks"></a>Obsługa dostawców dla zakładek
W przykładzie w tym temacie dodano `IRowsetLocate` współpracować w celu `CMyProviderRowset` klasy. Prawie we wszystkich przypadkach należy rozpocząć od Dodawanie interfejsu do istniejącego obiektu COM. Można następnie przetestuj je, dodając więcej wywołań z szablonami konsumentów. W przykładzie pokazano, jak:  
  
-   Dodawanie interfejsu do dostawcy.  
  
-   Dynamiczne określanie kolumn, aby powrócić do konsumenta.  
  
-   Dodanie obsługi zakładek.  
  
 `IRowsetLocate` Interfejs dziedziczy z `IRowset` interfejsu. Aby dodać `IRowsetLocate` interfejsu, dziedziczą `CMyProviderRowset` z [irowsetlocateimpl —](../../data/oledb/irowsetlocateimpl-class.md).  
  
 Dodawanie `IRowsetLocate` interfejs jest nieco inne niż większość interfejsów. Dzięki czemu wiersz tablic metod wirtualnych się OLE DB provider szablony mają parametr szablonu, aby obsłużyć interfejsu pochodnego. Poniższy kod przedstawia nową listę dziedziczenia:  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
// CMyProviderRowset  
class CMyProviderRowset : public CRowsetImpl< CMyProviderRowset,   
      CTextData, CMyProviderCommand, CAtlArray<CTextData>,   
      CSimpleRow,   
          IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate>>  
```  
  
 Czwarty, piąty i szóstego parametry wszystkie dodane. W tym przykładzie użyto wartości domyślne dla czwarty i piąty parametrów i określić `IRowsetLocateImpl` jako szóstego parametru. `IRowsetLocateImpl` jest klasą szablonu OLE DB, która przyjmuje dwa parametry szablonu: te podpinanie `IRowsetLocate` współpracować w celu `CMyProviderRowset` klasy. Aby dodać większość interfejsów, można pominąć ten krok i przejść do następnej. Tylko `IRowsetLocate` i `IRowsetScroll` interfejsów, które muszą być obsługiwani w ten sposób.  
  
 Następnie należy sprawdzić `CMyProviderRowset` do wywołania `QueryInterface` dla `IRowsetLocate` interfejsu. Dodaj wiersz `COM_INTERFACE_ENTRY(IRowsetLocate)` do mapy. Mapę interfejsu dla `CMyProviderRowset` powinien pojawić się, jak pokazano w poniższym kodzie:  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
typedef CRowsetImpl< CMyProviderRowset, CTextData, CMyProviderCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate>> _RowsetBaseClass;  
  
BEGIN_COM_MAP(CMyProviderRowset)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 Musisz również dołączyć mapę do `CRowsetImpl` klasy. Dodaj w makrze COM_INTERFACE_ENTRY_CHAIN można dołączyć w `CRowsetImpl` mapy. Ponadto utworzyć element typedef o nazwie `RowsetBaseClass` składający się z informacje o dziedziczeniu. Ten element typedef jest dowolnego i można je zignorować.  
  
 Na koniec obsługi `IColumnsInfo::GetColumnsInfo` wywołania. Makra PROVIDER_COLUMN_ENTRY zwykle są używane w tym celu. Jednak użytkownik może być używanie zakładek. Musi być w stanie zmienić kolumny, które zwraca dostawcę, w zależności od tego, czy użytkownik poprosi o podanie zakładki.  
  
 Aby obsłużyć `IColumnsInfo::GetColumnsInfo` wywołania, Usuń `PROVIDER_COLUMN` mapy w `CTextData` klasy. Makra PROVIDER_COLUMN_MAP definiuje funkcję `GetColumnInfo`. Musisz zdefiniować własne `GetColumnInfo` funkcji. Deklaracja funkcji powinna wyglądać następująco:  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
  
class CTextData  
{  
   ...  
     // NOTE: Be sure you removed the PROVIDER_COLUMN_MAP!  
   static ATLCOLUMNINFO* GetColumnInfo(CMyProviderRowset* pThis,   
        ULONG* pcCols);  
   static ATLCOLUMNINFO* GetColumnInfo(CMyProviderCommand* pThis,   
        ULONG* pcCols);  
...  
};  
```  
  
 Następnie należy zaimplementować `GetColumnInfo` funkcji w pliku MyProviderRS.cpp w następujący sposób:  
  
```cpp
////////////////////////////////////////////////////////////////////  
// MyProviderRS.cpp  
  
template <class TInterface>  
ATLCOLUMNINFO* CommonGetColInfo(IUnknown* pPropsUnk, ULONG* pcCols)  
{  
   static ATLCOLUMNINFO _rgColumns[5];  
   ULONG ulCols = 0;  
  
   CComQIPtr<TInterface> spProps = pPropsUnk;  
  
   CDBPropIDSet set(DBPROPSET_ROWSET);  
   set.AddPropertyID(DBPROP_BOOKMARKS);  
   DBPROPSET* pPropSet = NULL;  
   ULONG ulPropSet = 0;  
   HRESULT hr;  
  
   if (spProps)  
      hr = spProps->GetProperties(1, &set, &ulPropSet, &pPropSet);  
  
   // Check the property flag for bookmarks, if it is set, set the   
// zero ordinal entry in the column map with the bookmark   
// information.  
  
   if (pPropSet)  
   {  
      CComVariant var = pPropSet->rgProperties[0].vValue;  
      CoTaskMemFree(pPropSet->rgProperties);  
      CoTaskMemFree(pPropSet);  
  
      if ((SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE)))  
      {  
         ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0,   
                     sizeof(DWORD), DBTYPE_BYTES,  
            0, 0, GUID_NULL, CAgentMan, dwBookmark,         
                        DBCOLUMNFLAGS_ISBOOKMARK)  
         ulCols++;  
      }  
  
   }  
  
   // Next set the other columns up.  
   ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Field1"), 1, 16, DBTYPE_STR,   
          0xFF, 0xFF, GUID_NULL, CTextData, szField1)  
   ulCols++;  
   ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Field2"), 2, 16, DBTYPE_STR,  
       0xFF, 0xFF, GUID_NULL, CTextData, szField2)  
   ulCols++;  
  
   if (pcCols != NULL)  
      *pcCols = ulCols;  
  
   return _rgColumns;  
}  
  
ATLCOLUMNINFO* CTextData::GetColumnInfo(CMyProviderCommand* pThis,   
     ULONG* pcCols)  
{  
   return CommonGetColInfo<ICommandProperties>(pThis->GetUnknown(),  
        pcCols);  
}  
  
ATLCOLUMNINFO* CAgentMan::GetColumnInfo(RUpdateRowset* pThis, ULONG* pcCols)  
{  
   return CommonGetColInfo<IRowsetInfo>(pThis->GetUnknown(), pcCols);  
}  
```  
  
 `GetColumnInfo` Po pierwsze sprawdza czy właściwość o nazwie `DBPROP_IRowsetLocate` jest ustawiona. OLE DB ma właściwości dla każdego opcjonalne interfejsów wyłączyć obiektu zestawu wierszy. Jeśli użytkownik chce, aby użyć jednego z tych interfejsów opcjonalne, ustawia właściwość na true. Dostawcę można sprawdzić tę właściwość i podejmować żadnych specjalnych czynności, na jego podstawie.  
  
 W danej implementacji można pobrać właściwości, za pomocą wskaźnika do obiektu command. `pThis` Wskaźnika reprezentuje klasę polecenia lub zestaw wierszy. Ponieważ w tym miejscu możesz użyć szablonów, należy przekazać go jako `void` wskaźnik lub kod nie kompiluje się.  
  
 Określ tablicy statycznej w celu uwzględnienia informacji o kolumnie. Jeśli użytkownik nie chce kolumna zakładki, zostanie zmarnowane wpisem w tablicy. Mogą dynamicznie przydzielać tej tablicy, ale trzeba upewnij się, że prawidłowo zniszczenia. W tym przykładzie definiuje i używa makra ADD_COLUMN_ENTRY i ADD_COLUMN_ENTRY_EX do wstawiania informacji do tablicy. Makra można dodać do pliku MyProviderRS.H, jak pokazano w poniższym kodzie:  
  
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
  
 Aby przetestować kod u odbiorcy, musisz wprowadzić kilka zmian, aby `OnRun` programu obsługi. Pierwszy zmiana funkcji jest, że dodasz kod, aby dodać właściwość do zestawu właściwości. Zestawy kodów `DBPROP_IRowsetLocate` właściwości na wartość true, w związku z tym informuje dostawcę mają kolumna zakładki. `OnRun` Kod procedury obsługi powinna wyglądać następująco:  
  
```cpp
//////////////////////////////////////////////////////////////////////  
// TestProv Consumer Application in TestProvDlg.cpp  
  
void CTestProvDlg::OnRun()   
{  
   CCommand<CAccessor<CProvider>> table;  
   CDataSource source;  
   CSession   session;  
  
   if (source.Open("MyProvider.MyProvider.1", NULL, NULL, NULL,   
          NULL) != S_OK)  
      return;  
  
   if (session.Open(source) != S_OK)  
      return;  
  
   CDBPropSet propset(DBPROPSET_ROWSET);  
   propset.AddProperty(DBPROP_IRowsetLocate, true);  
   if (table.Open(session, _T("c:\\public\\testprf2\\myData.txt"),   
          &propset) != S_OK)  
      return;  
  
   CBookmark<4> tempBookmark;  
   ULONG ulCount=0;  
   while (table.MoveNext() == S_OK)  
   {  
  
      DBCOMPARE compare;  
      if (ulCount == 2)  
         tempBookmark = table.bookmark;  

HRESULT hr = table.Compare(table.dwBookmark, table.dwBookmark,  
                 &compare);  
      if (FAILED(hr))  
         ATLTRACE(_T("Compare failed: 0x%X\n"), hr);  
      else  
         _ASSERTE(compare == DBCOMPARE_EQ);  
  
      m_ctlString1.AddString(table.szField1);  
      m_ctlString2.AddString(table.szField2);  
      ulCount++;  
   }  
  
   table.MoveToBookmark(tempBookmark);  
   m_ctlString1.AddString(table.szField1);  
   m_ctlString2.AddString(table.szField2);  
}  
```  
  
 While pętla zawiera kod, aby wywołać `Compare` method in Class metoda `IRowsetLocate` interfejsu. Kod, który masz powinna zawsze przekazać, ponieważ porównujemy dokładnie tych samych zakładek. Ponadto przechowywanie jedną zakładkę w zmiennej tymczasowej, tak, aby można go użyć po while pętla zostanie zakończone, aby wywołać `MoveToBookmark` funkcji w szablonach konsumenta. `MoveToBookmark` Wywołaniach funkcji `GetRowsAt` method in Class metoda `IRowsetLocate`.  
  
 Należy również zaktualizować rekord użytkownika u odbiorcy. Dodaj odpowiedni wpis w klasie w celu obsługi zakładki i do wpisu w `COLUMN_MAP`:  
  
```cpp
///////////////////////////////////////////////////////////////////////  
// TestProvDlg.cpp  
  
class CProvider  
{  
// Attributes  
public:  
   CBookmark<4>    bookmark;  // Add this line  
   char   szCommand[16];  
   char   szText[256];  
  
   // Binding Maps  
BEGIN_ACCESSOR_MAP(CProvider, 1)  
   BEGIN_ACCESSOR(0, true)   // auto accessor  
      BOOKMARK_ENTRY(bookmark)  // Add this line  
      COLUMN_ENTRY(1, szField1)  
      COLUMN_ENTRY(2, szField2)  
   END_ACCESSOR()  
END_ACCESSOR_MAP()  
};  
```  
  
 Po zaktualizowaniu kodu, powinno być możliwe tworzenie i wykonywanie dostawcę za pomocą `IRowsetLocate` interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zaawansowane techniki dostawcy](../../data/oledb/advanced-provider-techniques.md)