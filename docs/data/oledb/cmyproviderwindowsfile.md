---
title: CMyProviderWindowsFile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyproviderwindowsfile
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8f0ba90bdcbaa4255757ee31015d0f6986862916
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmyproviderwindowsfile"></a>CMyProviderWindowsFile
Kreator utworzy klasę, aby zawierać jeden wiersz danych. w tym przypadku jest to `CMyProviderWindowsFile`. Poniższy kod dla `CMyProviderWindowsFile` jest generowany kreatora i listę wszystkich plików w katalogu za pomocą **WIN32_FIND_DATA** struktury. `CMyProviderWindowsFile` dziedziczy **WIN32_FIND_DATA** struktury:  
  
```cpp
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
  
class CMyProviderWindowsFile:   
   public WIN32_FIND_DATA  
{  
public:  
BEGIN_PROVIDER_COLUMN_MAP(CMyProviderWindowsFile)  
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)  
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)  
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)  
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)  
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)  
END_PROVIDER_COLUMN_MAP()  
};  
```  
  
 `CMyProviderWindowsFile` jest nazywana [klasy rekordów użytkowników](../../data/oledb/user-record.md) ponieważ zawiera ona również mapy zawierająca opis kolumn w zestawie wierszy dostawcy. Mapowania kolumn dostawcy zawiera jeden wpis dla każdego pola w zestawie wierszy za pomocą makra PROVIDER_COLUMN_ENTRY. Makra Określ nazwę kolumny, numer porządkowy i przesunięcia wpisu struktury. Dostawca wpisów kolumn w powyższym kodzie zawierają przesunięcia do **WIN32_FIND_DATA** struktury. Kiedy klient wywołuje **IRowset::GetData**, dane są przesyłane w ciągłego buforu. Zamiast co możesz zrobić arytmetyka wskaźnika, mapy służy do określenia członka danych.  
  
 `CMyProviderRowset` Klasa zawiera także `Execute` metody. `Execute` to, co faktycznie odczytuje dane w z natywnego źródła. Poniższy kod przedstawia generowane przez kreatora `Execute` metody. Funkcja używa Win32 **FindFirstFile** i `FindNextFile` interfejsów API, aby pobrać informacje o plikach w katalogu i umieścić je w wystąpieniach `CMyProviderWindowsFile` klasy.  
  
```cpp
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
  
HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)  
{  
   USES_CONVERSION;  
   BOOL bFound = FALSE;  
   HANDLE hFile;  
   LPTSTR  szDir = (m_strCommandText == _T("")) ? _T("*.*") :  
       OLE2T(m_strCommandText);  
   CMyProviderWindowsFile wf;  
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
  
 Katalog do wyszukiwania jest reprezentowana przez `m_strCommandText`; zawiera tekst reprezentowany przez `ICommandText` interfejsu w obiekcie command. Jeśli nie określono katalogu, używa bieżącego katalogu.  
  
 Metoda tworzy jeden wpis dla każdego pliku (odpowiadającego na wiersz) i umieszcza je w **m_rgRowData** element członkowski danych. `CRowsetImpl` Klasa definiuje **m_rgRowData** element członkowski danych. Dane w tej tablicy reprezentuje całą tabelę i jest używane w szablonach.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki dostawcy generowane przez kreatora](../../data/oledb/provider-wizard-generated-files.md)