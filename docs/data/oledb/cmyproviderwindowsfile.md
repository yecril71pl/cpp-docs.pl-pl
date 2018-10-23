---
title: CCustomWindowsFile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyproviderwindowsfile
- ccustomwindowsfile
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
- CCustomWindowsFile class
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a87f8cc4d6581c253225fa038d0c8972e71fcff1
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808800"
---
# <a name="ccustomwindowsfile"></a>CCustomWindowsFile

Kreator tworzy klasę umożliwiającą zawierają jeden wiersz danych. w tym przypadku jest to `CCustomWindowsFile`. Poniższy kod dla `CCustomWindowsFile` jest generowany kreatora i wyświetla listę wszystkich plików w katalogu przy użyciu `WIN32_FIND_DATA` struktury. `CCustomWindowsFile` dziedziczy `WIN32_FIND_DATA` strukturę:  
  
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
  
`CCustomWindowsFile` nosi nazwę [klasy rekordów użytkowników](../../data/oledb/user-record.md) ponieważ zawiera ona także mapę zawierająca opis kolumn w zestawie wierszy z dostawcy. Dostawcy mapy kolumny zawiera jeden wpis dla każdego pola w zestawie wierszy przy użyciu makr PROVIDER_COLUMN_ENTRY. Makra Określ nazwę kolumny, porządkowe i przesunięcia wpisu struktury. Wpisów kolumn dostawcy w powyższym kodzie zawierają przesunięcia do `WIN32_FIND_DATA` struktury. Gdy użytkownik wywołuje `IRowset::GetData`, dane są przesyłane w ciągłym buforu. Zamiast co możesz zrobić arytmetyka wskaźnika, mapa pozwala określić element członkowski danych.  
  
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
  
Katalog do przeszukania jest reprezentowany przez `m_strCommandText`; zawiera tekst, reprezentowane przez `ICommandText` interfejsu w obiekcie command. Jeśli nie określono katalogu, używa bieżącego katalogu.  
  
Metoda tworzy jeden wpis dla każdego pliku (odpowiadających na wiersz) i umieszcza je w `m_rgRowData` element członkowski danych. `CRowsetImpl` Klasa definiuje `m_rgRowData` element członkowski danych. Dane w tej tablicy reprezentuje całą tabelę i jest używana w całej szablonów.  
  
## <a name="see-also"></a>Zobacz też  

[Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)