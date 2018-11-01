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
ms.openlocfilehash: 008fe318ee96248dfca0c3c87bf660726beb3092
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660832"
---
# <a name="ccustomwindowsfile"></a>CCustomWindowsFile

Kreator utworzy klasę, która ma jeden wiersz danych. w tym przypadku jest to `CCustomWindowsFile`. Poniższy kod dla `CCustomWindowsFile` jest generowany kreatora i wyświetla listę wszystkich plików w katalogu przy użyciu `WIN32_FIND_DATA` struktury. `CCustomWindowsFile` dziedziczy `WIN32_FIND_DATA` strukturę:

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

`CCustomWindowsFile` nosi nazwę [klasy rekordów użytkowników](../../data/oledb/user-record.md) ponieważ ma on także mapę zawierająca opis kolumn w zestawie wierszy dostawcy. Dostawcy mapy kolumny zawiera jeden wpis dla każdego pola w zestawie wierszy przy użyciu makr PROVIDER_COLUMN_ENTRY. Makra Określ nazwę kolumny, porządkowe i przesunięcia wpisu struktury. Wpisów kolumn dostawcy w powyższym kodzie zawierają przesunięcia do `WIN32_FIND_DATA` struktury. Gdy użytkownik wywołuje `IRowset::GetData`, dane są przesyłane w ciągłym buforu. Zamiast co możesz zrobić arytmetyka wskaźnika, mapa pozwala określić element członkowski danych.

`CCustomRowset` Klasa zawiera także `Execute` metody. `Execute` to, co faktycznie odczytuje dane w natywnej źródła. Poniższy kod pokazuje generowane przez kreatora `Execute` metody. Funkcja używa Win32 `FindFirstFile` i `FindNextFile` interfejsów API, aby pobrać informacje o plikach w katalogu i umieścić je w wystąpieniach `CCustomWindowsFile` klasy.

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

Katalog do przeszukania jest pokazywana przez `m_strCommandText`; zawiera tekst, reprezentowane przez `ICommandText` interfejsu w obiekcie command. Jeśli nie określono katalogu, używa bieżącego katalogu.

Metoda tworzy jeden wpis dla każdego pliku (odpowiadających na wiersz) i umieszcza je w `m_rgRowData` element członkowski danych. `CRowsetImpl` Klasa definiuje `m_rgRowData` element członkowski danych. Dane w tej tablicy jest wyświetlana cała tabela i jest używane w szablonach.

## <a name="see-also"></a>Zobacz też

[Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)<br/>
