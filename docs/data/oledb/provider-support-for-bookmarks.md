---
title: "Obsługa dostawców dla zakładek | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- IRowsetLocate class, provider support for bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- IRowsetLocate class
- OLE DB providers, bookmark support
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cb3c0d60c4b339d7ed2ae8bc4eee503036ac9097
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="provider-support-for-bookmarks"></a>Obsługa dostawców dla zakładek
Dodaje na przykład w tym temacie `IRowsetLocate` interfejsu do `CMyProviderRowset` klasy. W większości przypadków możesz uruchomić Dodawanie interfejsu do istniejącego obiektu COM. Można następnie testować przez dodanie kolejnych wywołań z szablonami konsumentów. W przykładzie pokazano, jak:  
  
-   Dodawanie interfejsu do dostawcy.  
  
-   Dynamiczne określanie kolumn, aby powrócić do konsumenta.  
  
-   Dodawanie obsługi zakładki.  
  
 `IRowsetLocate` Dziedziczy interfejs `IRowset` interfejsu. Aby dodać `IRowsetLocate` interfejsu, dziedziczą `CMyProviderRowset` z [irowsetlocateimpl —](../../data/oledb/irowsetlocateimpl-class.md).  
  
 Dodawanie `IRowsetLocate` interfejs jest nieco inne niż większość interfejsów. Dzięki czemu wiersz tablic metod wirtualnych zapasowej OLE DB szablony dostawców ma parametr szablonu w celu obsługi interfejsu pochodnego. Poniższy kod przedstawia nową listę dziedziczenia:  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
// CMyProviderRowset  
class CMyProviderRowset : public CRowsetImpl< CMyProviderRowset,   
      CTextData, CMyProviderCommand, CAtlArray<CTextData>,   
      CSimpleRow,   
          IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate> >  
```  
  
 Czwarta piątego i szóstego parametry wszystkie dodane. W tym przykładzie używane wartości domyślne dla czwartego i piątego parametrów i określić `IRowsetLocateImpl` jako szóstego parametru. `IRowsetLocateImpl`jest to klasa szablonu OLE DB, który przyjmuje dwa parametry szablonu: te Podłączanie `IRowsetLocate` interfejsu do `CMyProviderRowset` klasy. Aby dodać większość interfejsów, można pominąć ten krok i przejść do kolejnego. Tylko `IRowsetLocate` i `IRowsetScroll` interfejsy muszą być obsługiwani w ten sposób.  
  
 Następnie należy przekazać do `CMyProviderRowset` do wywołania `QueryInterface` dla `IRowsetLocate` interfejsu. Dodaj wiersz `COM_INTERFACE_ENTRY(IRowsetLocate)` do mapy. Mapa interfejs dla `CMyProviderRowset` powinna być taka jak pokazano w poniższym kodzie:  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
typedef CRowsetImpl< CMyProviderRowset, CTextData, CMyProviderCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate> > _RowsetBaseClass;  
  
BEGIN_COM_MAP(CMyProviderRowset)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 Należy również utworzenie punktu zaczepienia mapy do `CRowsetImpl` klasy. Dodaj w makrze COM_INTERFACE_ENTRY_CHAIN utworzenie punktu zaczepienia w `CRowsetImpl` mapy. Ponadto utworzyć jako element typedef o nazwie `RowsetBaseClass` składający się z informacje o dziedziczeniu. Ten element typedef jest dowolnego i można zignorować.  
  
 Na koniec obsługi **IColumnsInfo::GetColumnsInfo** wywołania. Makra PROVIDER_COLUMN_ENTRY będzie zwykle używany w tym celu. Jednak klient chcieć użyć zakładki. Musi być w stanie zmienić kolumny, które zwraca dostawcy, w zależności od tego, czy klient pyta o zakładki.  
  
 Do obsługi **IColumnsInfo::GetColumnsInfo** wywołanie, Usuń **PROVIDER_COLUMN** mapy w `CTextData` klasy. Makro PROVIDER_COLUMN_MAP definiuje funkcję `GetColumnInfo`. Musisz zdefiniować własny `GetColumnInfo` funkcji. Deklaracja funkcji powinna wyglądać następująco:  
  
```  
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
  
 Następnie należy zaimplementować `GetColumnInfo` działają w pliku MyProviderRS.cpp w następujący sposób:  
  
```  
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
  
 `GetColumnInfo`pierwszy sprawdza, czy właściwość o nazwie **DBPROP_IRowsetLocate** jest ustawiona. OLE DB ma właściwości dla poszczególnych interfejsów opcjonalne poza obiektu zestawu wierszy. Jeśli użytkownik chce użyć jednej z tych interfejsów opcjonalne, ustawia właściwość na wartość true. Dostawcę można sprawdzić tę właściwość i podjąć akcję specjalną na ich podstawie.  
  
 W implementacji można pobrać właściwości przy użyciu wskaźnika do obiektu command. `pThis` Wskaźnika reprezentuje klasy zestawu wierszy lub polecenie. Ponieważ w tym miejscu użyć szablonów, trzeba przekazać go jako `void` wskaźnika lub kod nie kompiluje się.  
  
 Określanie statycznego tablica zawiera informacji o kolumnie. Aby klient nie kolumny zakładki, wpis w tablicy jest niewykorzystana. Można dynamicznie przydzielić tej tablicy, ale trzeba upewnij się, że poprawnie zniszczenia. W tym przykładzie definiuje i korzysta z makra ADD_COLUMN_ENTRY i ADD_COLUMN_ENTRY_EX do wstawiania informacji do tablicy. Makra można dodać do plików MyProviderRS.H, jak pokazano w poniższym kodzie:  
  
```  
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
  
 Do testowania kodu w konsumenta, które należy podjąć kilka zmian do `OnRun` obsługi. Pierwsza zmiana funkcji jest, że Dodaj kod, aby dodać właściwość do zestawu właściwości. Ustawia kod **DBPROP_IRowsetLocate** właściwości na wartość true, w związku z tym poleceniem dostawcy czy chcesz kolumnę zakładki. `OnRun` Kod obsługi powinna wyglądać następująco:  
  
```  
//////////////////////////////////////////////////////////////////////  
// TestProv Consumer Application in TestProvDlg.cpp  
  
void CTestProvDlg::OnRun()   
{  
   CCommand<CAccessor<CProvider> > table;  
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
  
 While pętla zawiera kod, aby wywołać `Compare` metoda `IRowsetLocate` interfejsu. Kod, który jest zawsze należy przekazać, ponieważ porównywana dokładnie tego samego zakładki. Co zakładki w przechowywać zmiennej tymczasowej tak, aby można go użyć po while zakończenie do wywołania w pętli `MoveToBookmark` funkcji w szablonach konsumenta. `MoveToBookmark` Wywołania funkcji `GetRowsAt` metoda `IRowsetLocate`.  
  
 Należy również zaktualizować rekord użytkownika w konsumenta. Dodaj wpis w klasie obsługi zakładki i wpis w **COLUMN_MAP**:  
  
```  
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
  
 Po zaktualizowaniu kod, powinno być możliwe do tworzenia i wykonywania dostawcy o `IRowsetLocate` interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zaawansowane techniki dostawcy](../../data/oledb/advanced-provider-techniques.md)