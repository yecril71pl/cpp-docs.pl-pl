---
title: CCustomWindowsFile
ms.date: 10/22/2018
f1_keywords:
- cmyproviderwindowsfile
- ccustomwindowsfile
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
- CCustomWindowsFile class
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
ms.openlocfilehash: 103a1ce5568c6137994056e574ce8eec04511d8f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079743"
---
# <a name="ccustomwindowsfile"></a>CCustomWindowsFile

Kreator tworzy klasę, która ma jeden wiersz danych. w tym przypadku jest on nazywany `CCustomWindowsFile`. Poniższy kod dla `CCustomWindowsFile` jest generowany przez kreatora i zawiera listę wszystkich plików w katalogu przy użyciu struktury `WIN32_FIND_DATA`. `CCustomWindowsFile` dziedziczy po strukturze `WIN32_FIND_DATA`:

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

class CCustomWindowsFile:
   public WIN32_FIND_DATA
{
public:
BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
END_PROVIDER_COLUMN_MAP()
};
```

`CCustomWindowsFile` jest nazywana [klasą rekordów użytkownika](../../data/oledb/user-record.md) , ponieważ ma również mapę opisującą kolumny w zestawie wierszy dostawcy. Mapa kolumn dostawcy zawiera jeden wpis dla każdego pola w zestawie wierszy przy użyciu makr PROVIDER_COLUMN_ENTRY. Makra określają nazwę kolumny, porządkową i przesunięcie do wpisu struktury. Wpisy kolumny dostawcy w powyższym kodzie zawierają przesunięcia do struktury `WIN32_FIND_DATA`. Gdy użytkownik wywołuje `IRowset::GetData`, dane są przesyłane w jednym ciągłym buforze. Zamiast wykonywać operacje arytmetyczne wskaźnika, Mapa umożliwia określenie elementu członkowskiego danych.

Klasa `CCustomRowset` zawiera również metodę `Execute`. `Execute` to to, co faktycznie odczytuje dane ze źródła natywnego. Poniższy kod przedstawia metodę `Execute` wygenerowaną przez kreatora. Funkcja używa `FindFirstFile` Win32 i interfejsów API `FindNextFile` do pobierania informacji o plikach w katalogu i umieszczania ich w wystąpieniach klasy `CCustomWindowsFile`.

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)
{
   USES_CONVERSION;
   BOOL bFound = FALSE;
   HANDLE hFile;
   LPTSTR  szDir = (m_strCommandText == _T("")) ? _T("*.*") :
       OLE2T(m_strCommandText);
   CCustomWindowsFile wf;
   hFile = FindFirstFile(szDir, &wf);
   if (hFile == INVALID_HANDLE_VALUE)
      return DB_E_ERRORSINCOMMAND;
   LONG cFiles = 1;
   BOOL bMoreFiles = TRUE;
   while (bMoreFiles)
   {
      if (!m_rgRowData.Add(wf))
         return E_OUTOFMEMORY;
      bMoreFiles = FindNextFile(hFile, &wf);
      cFiles++;
   }
   FindClose(hFile);
   if (pcRowsAffected != NULL)
      *pcRowsAffected = cFiles;
   return S_OK;
}
```

Katalog do przeszukania jest pokazywany przez `m_strCommandText`; zawiera tekst reprezentowany przez interfejs `ICommandText` w obiekcie Command. Jeśli katalog nie zostanie określony, zostanie użyty bieżący katalog.

Metoda tworzy jeden wpis dla każdego pliku (odpowiadającego wierszowi) i umieszcza go w elemencie członkowskim danych `m_rgRowData`. Klasa `CRowsetImpl` definiuje element członkowski danych `m_rgRowData`. Dane w tej tablicy są wyświetlane w całej tabeli i są używane w szablonach.

## <a name="see-also"></a>Zobacz też

[Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)<br/>
