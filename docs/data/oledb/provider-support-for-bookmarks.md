---
title: Obsługa dostawców dla zakładek
ms.date: 11/04/2016
helpviewer_keywords:
- IRowsetLocate class, provider support for bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- IRowsetLocate class
- OLE DB providers, bookmark support
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
ms.openlocfilehash: 240cb4da03d6c8c1958b7a86e78171aca2dc30e9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216456"
---
# <a name="provider-support-for-bookmarks"></a>Obsługa dostawców dla zakładek

Przykład w tym temacie dodaje `IRowsetLocate` interfejs do `CCustomRowset` klasy. Niemal we wszystkich przypadkach należy zacząć od dodania interfejsu do istniejącego obiektu COM. Następnie można przetestować go, dodając więcej wywołań z szablonów odbiorców. W przykładzie pokazano, jak:

- Dodaj interfejs do dostawcy.

- Dynamiczne Określanie kolumn, które mają zostać zwrócone do konsumenta.

- Dodaj obsługę zakładki.

`IRowsetLocate`Interfejs dziedziczy po `IRowset` interfejsie. Aby dodać `IRowsetLocate` interfejs, Dziedzicz `CCustomRowset` z [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md).

Dodawanie `IRowsetLocate` interfejsu jest nieco inne niż większość interfejsów. Aby linie tablic wirtualnych były wyznaczone, szablon dostawcy OLE DB ma parametr szablonu do obsługi interfejsu pochodnego. Poniższy kod przedstawia nową listę dziedziczenia:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

// CCustomRowset
class CCustomRowset : public CRowsetImpl< CCustomRowset,
      CTextData, CCustomCommand, CAtlArray<CTextData>,
      CSimpleRow,
          IRowsetLocateImpl<CCustomRowset, IRowsetLocate>>
```

Zostaną dodane czwarty, piąty i szósty parametr. W tym przykładzie używane są wartości domyślne dla czwartego i piątego `IRowsetLocateImpl` parametru, ale określono jako szósty parametr. `IRowsetLocateImpl`jest klasą szablonu OLE DB, która przyjmuje dwa parametry szablonu: podłącza `IRowsetLocate` interfejs do `CCustomRowset` klasy. Aby dodać większość interfejsów, można pominąć ten krok i przejść do kolejnego. Tylko `IRowsetLocate` interfejsy i `IRowsetScroll` muszą być obsługiwane w ten sposób.

Następnie należy poinformować o `CCustomRowset` wywołaniu `QueryInterface` `IRowsetLocate` interfejsu. Dodaj linię `COM_INTERFACE_ENTRY(IRowsetLocate)` do mapy. Mapa interfejsu dla `CCustomRowset` powinna być wyświetlana, jak pokazano w poniższym kodzie:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

typedef CRowsetImpl< CCustomRowset, CTextData, CCustomCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CCustomRowset, IRowsetLocate>> _RowsetBaseClass;

BEGIN_COM_MAP(CCustomRowset)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

Musisz również podłączyć mapę do `CRowsetImpl` klasy. Dodaj w makrze COM_INTERFACE_ENTRY_CHAIN, aby podpiąć `CRowsetImpl` mapę. Ponadto Utwórz element typedef o nazwie `RowsetBaseClass` , który składa się z informacji o dziedziczeniu. Ten element typedef jest dowolny i można go zignorować.

Na koniec obsłuż `IColumnsInfo::GetColumnsInfo` wywołanie. W tym celu zwykle należy użyć makr PROVIDER_COLUMN_ENTRY. Jednak odbiorca może chcieć używać zakładek. Musisz mieć możliwość zmiany kolumn zwracanych przez dostawcę w zależności od tego, czy użytkownik pyta o zakładkę.

Aby obsłużyć `IColumnsInfo::GetColumnsInfo` wywołanie, Usuń mapę PROVIDER_COLUMN w `CTextData` klasie. Makro PROVIDER_COLUMN_MAP definiuje funkcję `GetColumnInfo` . Zdefiniuj własną `GetColumnInfo` funkcję. Deklaracja funkcji powinna wyglądać następująco:

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.H

class CTextData
{
   ...
     // NOTE: Be sure you removed the PROVIDER_COLUMN_MAP!
   static ATLCOLUMNINFO* GetColumnInfo(CCustomRowset* pThis,
        ULONG* pcCols);
   static ATLCOLUMNINFO* GetColumnInfo(CCustomCommand* pThis,
        ULONG* pcCols);
...
};
```

Następnie Zaimplementuj `GetColumnInfo` funkcję w pliku *Custom*RS. cpp w następujący sposób:

```cpp
////////////////////////////////////////////////////////////////////
// CustomRS.cpp

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

ATLCOLUMNINFO* CTextData::GetColumnInfo(CCustomCommand* pThis,
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

`GetColumnInfo`najpierw sprawdza, czy ustawiono właściwość o nazwie `DBPROP_IRowsetLocate` . OLE DB ma właściwości dla każdego z opcjonalnych interfejsów poza obiektem zestawu wierszy. Jeśli odbiorca chce użyć jednego z tych opcjonalnych interfejsów, ustawia właściwość na true. Dostawca może następnie sprawdzić tę właściwość i wykonać specjalną akcję na jej podstawie.

W implementacji uzyskasz Właściwość za pomocą wskaźnika do obiektu polecenia. `pThis`Wskaźnik reprezentuje zestaw wierszy lub klasę poleceń. Ponieważ używasz tutaj szablonów, musisz przekazać go jako **`void`** wskaźnik lub kod nie kompiluje się.

Określ tablicę statyczną do przechowywania informacji o kolumnie. Jeśli odbiorca nie ma zamiaru kolumny zakładki, wpis w tablicy jest tracony. Można dynamicznie przydzielić tę tablicę, ale należy upewnić się, że jest ona poprawna. Ten przykład definiuje i używa makr ADD_COLUMN_ENTRY i ADD_COLUMN_ENTRY_EX do wstawienia informacji do tablicy. Możesz dodać makra do *niestandardowego*RS. H plik, jak pokazano w poniższym kodzie:

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

Aby przetestować kod w odbiorcy, należy wprowadzić kilka zmian w programie `OnRun` obsługi. Pierwsza zmiana funkcji polega na dodaniu kodu w celu dodania właściwości do zestawu właściwości. Kod ustawia `DBPROP_IRowsetLocate` Właściwość na wartość true, co oznacza, że dostawca ma być kolumną zakładki. `OnRun`Kod procedury obsługi powinien wyglądać następująco:

```cpp
//////////////////////////////////////////////////////////////////////
// TestProv Consumer Application in TestProvDlg.cpp

void CTestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession   session;

   if (source.Open("Custom.Custom.1", NULL, NULL, NULL,
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

**`while`** Pętla zawiera kod, który wywołuje `Compare` metodę w `IRowsetLocate` interfejsie. Kod, który powinien być zawsze przekazywany, ponieważ porównywane są dokładnie te same zakładki. Ponadto należy przechowywać jedną zakładkę w zmiennej tymczasowej, aby można było użyć jej po **`while`** zakończeniu pętli do wywołania `MoveToBookmark` funkcji w szablonach konsumentów. `MoveToBookmark`Funkcja wywołuje `GetRowsAt` metodę w `IRowsetLocate` .

Należy również zaktualizować rekord użytkownika w odbiorcy. Dodaj wpis w klasie, aby obsłużyć zakładkę i wpis w COLUMN_MAP:

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

Po zaktualizowaniu kodu należy być w stanie skompilować i uruchomić dostawcę przy użyciu `IRowsetLocate` interfejsu.

## <a name="see-also"></a>Zobacz także

[Zaawansowane techniki dostawcy](../../data/oledb/advanced-provider-techniques.md)
