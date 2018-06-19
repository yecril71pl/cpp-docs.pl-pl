---
title: Klasa CAtlTemporaryFile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::Close
- ATLFILE/ATL::CAtlTemporaryFile::Create
- ATLFILE/ATL::CAtlTemporaryFile::Flush
- ATLFILE/ATL::CAtlTemporaryFile::GetPosition
- ATLFILE/ATL::CAtlTemporaryFile::GetSize
- ATLFILE/ATL::CAtlTemporaryFile::HandsOff
- ATLFILE/ATL::CAtlTemporaryFile::HandsOn
- ATLFILE/ATL::CAtlTemporaryFile::LockRange
- ATLFILE/ATL::CAtlTemporaryFile::Read
- ATLFILE/ATL::CAtlTemporaryFile::Seek
- ATLFILE/ATL::CAtlTemporaryFile::SetSize
- ATLFILE/ATL::CAtlTemporaryFile::TempFileName
- ATLFILE/ATL::CAtlTemporaryFile::UnlockRange
- ATLFILE/ATL::CAtlTemporaryFile::Write
dev_langs:
- C++
helpviewer_keywords:
- CAtlTemporaryFile class
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 49adcb572e355c62e6f21081eb033496e60e2369
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366068"
---
# <a name="catltemporaryfile-class"></a>Klasa CAtlTemporaryFile
Ta klasa dostarcza metody do tworzenia i używania pliku tymczasowego.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CAtlTemporaryFile
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|Konstruktor.|  
|[CAtlTemporaryFile:: ~ CAtlTemporaryFile](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlTemporaryFile::Close](#close)|Wywołanie tej metody, aby zamknąć plik tymczasowy i albo usunąć jej zawartość lub przechowywać je w obszarze określonej nazwy pliku.|  
|[CAtlTemporaryFile::Create](#create)|Wywołanie tej metody można utworzyć pliku tymczasowego.|  
|[CAtlTemporaryFile::Flush](#flush)|Wywołanie tej metody, aby wymusić żadnych danych pozostałych w buforze pliku do zapisania pliku tymczasowego.|  
|[CAtlTemporaryFile::GetPosition](#getposition)|Wywołanie tej metody, aby uzyskać bieżącą pozycję wskaźnika pliku.|  
|[CAtlTemporaryFile::GetSize](#getsize)|Wywołaj tę metodę, aby pobrać rozmiar w bajtach pliku tymczasowego.|  
|[CAtlTemporaryFile::HandsOff](#handsoff)|Wywołanie tej metody, aby usunąć skojarzenie pliku z `CAtlTemporaryFile` obiektu.|  
|[CAtlTemporaryFile::HandsOn](#handson)|Wywołaj tę metodę, aby otworzyć istniejący plik tymczasowy i umieść kursor na końcu pliku.|  
|[CAtlTemporaryFile::LockRange](#lockrange)|Wywołaj tę metodę, aby zablokować region, w pliku, aby uniemożliwić dostęp do jej przez inne procesy.|  
|[CAtlTemporaryFile::Read](#read)|Wywołanie tej metody można odczytać danych z pliku tymczasowego, zaczynając od pozycji wskaźnika pliku.|  
|[CAtlTemporaryFile::Seek](#seek)|Wywołaj tę metodę, aby przenieść wskaźnik pliku tymczasowego pliku.|  
|[CAtlTemporaryFile::SetSize](#setsize)|Wywołaj tę metodę, aby określić rozmiar pliku tymczasowego.|  
|[CAtlTemporaryFile::TempFileName](#tempfilename)|Wywołaj tę metodę, aby zwrócić nazwę pliku tymczasowego.|  
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|Wywołaj tę metodę, aby odblokować obszaru pliku tymczasowego.|  
|[CAtlTemporaryFile::Write](#write)|Wywołanie tej metody można zapisać danych do pliku tymczasowego, zaczynając od pozycji wskaźnika pliku.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlTemporaryFile::operator dojścia](#operator_handle)|Zwraca dojście do pliku tymczasowego.|  
  
## <a name="remarks"></a>Uwagi  
 `CAtlTemporaryFile` ułatwia tworzenie i używanie pliku tymczasowego. Plik jest automatycznie o nazwie, otworzyć zamknięty i usunięty. Jeśli zawartość pliku są wymagane, po zamknięciu pliku, zapisaniem do nowego pliku o określonej nazwie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlfile.h  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
##  <a name="catltemporaryfile"></a>  CAtlTemporaryFile::CAtlTemporaryFile  
 Konstruktor.  
  
```
CAtlTemporaryFile() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Plik nie jest rzeczywiście otwarty do momentu połączenie jest nawiązywane w przypadku [CAtlTemporaryFile::Create](#create).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]  
  
##  <a name="dtor"></a>  CAtlTemporaryFile:: ~ CAtlTemporaryFile  
 Destruktor.  
  
```
~CAtlTemporaryFile() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołania destruktora [CAtlTemporaryFile::Close](#close).  
  
##  <a name="close"></a>  CAtlTemporaryFile::Close  
 Wywołanie tej metody, aby zamknąć plik tymczasowy i albo usunąć jej zawartość lub przechowywać je w obszarze określonej nazwy pliku.  
  
```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *szNewName*  
 Nazwa nowego pliku do przechowywania zawartości pliku tymczasowego w. Jeśli ten argument ma wartość NULL, są usuwane zawartość pliku tymczasowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
##  <a name="create"></a>  CAtlTemporaryFile::Create  
 Wywołanie tej metody można utworzyć pliku tymczasowego.  
  
```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszDir`  
 Ścieżka do pliku tymczasowego. Jeśli jest to wartość NULL, [GetTempPath](http://msdn.microsoft.com/library/windows/desktop/aa364992) zostanie wywołana w celu przypisania ścieżki.  
  
 `dwDesiredAccess`  
 Żądany dostęp. Zobacz `dwDesiredAccess` w [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858) w systemie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
##  <a name="flush"></a>  CAtlTemporaryFile::Flush  
 Wywołanie tej metody, aby wymusić żadnych danych pozostałych w buforze pliku do zapisania pliku tymczasowego.  
  
```
HRESULT Flush() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Podobnie jak [CAtlTemporaryFile::HandsOff](#handsoff), z wyjątkiem tego, że plik nie jest zamknięty.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
##  <a name="getposition"></a>  CAtlTemporaryFile::GetPosition  
 Wywołanie tej metody, aby uzyskać bieżącą pozycję wskaźnika pliku.  
  
```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Pozycja w bajtach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Aby zmienić pozycję wskaźnika pliku, użyj [CAtlTemporaryFile::Seek](#seek).  
  
##  <a name="getsize"></a>  CAtlTemporaryFile::GetSize  
 Wywołaj tę metodę, aby pobrać rozmiar w bajtach pliku tymczasowego.  
  
```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nLen`  
 Liczba bajtów w pliku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
##  <a name="handsoff"></a>  CAtlTemporaryFile::HandsOff  
 Wywołanie tej metody, aby usunąć skojarzenie pliku z `CAtlTemporaryFile` obiektu.  
  
```
HRESULT HandsOff() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 `HandsOff` i [CAtlTemporaryFile::HandsOn](#handson) są używane do usuwania skojarzenia pliku z obiektu i dołączyć go w razie potrzeby. `HandsOff` zostanie wymusić żadnych danych pozostałych w buforze pliku do zapisania pliku tymczasowego, a następnie zamknij plik. Jeśli chcesz zamknąć i trwale usunąć plik, lub jeśli chcesz zamknąć i zachować zawartość pliku o podanej nazwie, użyj [CAtlTemporaryFile::Close](#close).  
  
##  <a name="handson"></a>  CAtlTemporaryFile::HandsOn  
 Wywołaj tę metodę, aby otworzyć istniejący plik tymczasowy i umieść kursor na końcu pliku.  
  
```
HRESULT HandsOn() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 [CAtlTemporaryFile::HandsOff](#handsoff) i `HandsOn` są używane do usuwania skojarzenia pliku z obiektu i dołączyć go w razie potrzeby.  
  
##  <a name="lockrange"></a>  CAtlTemporaryFile::LockRange  
 Wywołaj tę metodę, aby zablokować region, w pliku tymczasowym, aby uniemożliwić dostęp do jej przez inne procesy.  
  
```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Pozycja w pliku, w którym powinny one zacząć blokady.  
  
 `nCount`  
 Długość zakresu bajtów do zablokowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Blokowanie bajtów w pliku uniemożliwia dostęp do tych bajtów przez inne procesy. Można zablokować więcej niż jeden region, pliku, ale nie nakładające się regiony są dozwolone. Aby pomyślnie odblokować regionu, użyj [CAtlTemporaryFile::UnlockRange](#unlockrange), zapewniając zakres bajtów dokładnie odpowiada region, który wcześniej był zablokowany. `LockRange` Scala sąsiadujących ze sobą regionów; Jeśli dwóch regionach zablokowanym sąsiadujących ze sobą, należy odblokować każdego oddzielnie.  
  
##  <a name="operator_handle"></a>  CAtlTemporaryFile::operator dojścia  
 Zwraca dojście do pliku tymczasowego.  
  
```  
operator HANDLE() throw();
```  
  
##  <a name="read"></a>  CAtlTemporaryFile::Read  
 Wywołanie tej metody można odczytać danych z pliku tymczasowego, zaczynając od pozycji wskaźnika pliku.  
  
```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pBuffer`  
 Wskaźnik do buforu, który będzie odbierać dane z pliku do odczytu.  
  
 `nBufSize`  
 Rozmiar buforu w bajtach.  
  
 `nBytesRead`  
 Liczba bajtów odczytanych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [CAtlFile::Read](../../atl/reference/catlfile-class.md#read). Aby zmienić pozycję wskaźnika pliku, należy wywołać [CAtlTemporaryFile::Seek](#seek).  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
##  <a name="seek"></a>  CAtlTemporaryFile::Seek  
 Wywołaj tę metodę, aby przenieść wskaźnik pliku tymczasowego pliku.  
  
```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nOffset`  
 Przesunięcie, w bajtach, od początkowego punktu określonego przez *dwFrom.*  
  
 `dwFrom`  
 Punkt początkowy (FILE_BEGIN, FILE_CURRENT lub FILE_END).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [CAtlFile::Seek](../../atl/reference/catlfile-class.md#seek). Aby uzyskać bieżącą pozycję wskaźnika pliku, należy wywołać [CAtlTemporaryFile::GetPosition](#getposition).  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
##  <a name="setsize"></a>  CAtlTemporaryFile::SetSize  
 Wywołaj tę metodę, aby określić rozmiar pliku tymczasowego.  
  
```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nNewLen`  
 Długość nowego pliku w bajtach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [CAtlFile::SetSize](../../atl/reference/catlfile-class.md#setsize). Przy powrocie wskaźnika pliku znajduje się na końcu pliku.  
  
##  <a name="tempfilename"></a>  CAtlTemporaryFile::TempFileName  
 Wywołaj tę metodę, aby zwrócić nazwę pliku tymczasowego.  
  
```
LPCTSTR TempFileName() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `LPCTSTR` wskazujące na nazwę pliku.  
  
### <a name="remarks"></a>Uwagi  
 Nazwa pliku jest generowana w [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile) wywołaniem [GetTempFile](http://msdn.microsoft.com/library/windows/desktop/aa364991)funkcji zestawu SDK systemu Windows. Rozszerzenie pliku jest zawsze "TFR" dla pliku tymczasowego.  
  
##  <a name="unlockrange"></a>  CAtlTemporaryFile::UnlockRange  
 Wywołaj tę metodę, aby odblokować obszaru pliku tymczasowego.  
  
```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Pozycja w pliku, w którym powinny one zacząć unlock.  
  
 `nCount`  
 Długość zakresu bajtów do odblokowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [CAtlFile::UnlockRange](../../atl/reference/catlfile-class.md#unlockrange).  
  
##  <a name="write"></a>  CAtlTemporaryFile::Write  
 Wywołanie tej metody można zapisać danych do pliku tymczasowego, zaczynając od pozycji wskaźnika pliku.  
  
```
HRESULT Write(  
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pBuffer`  
 Bufor zawierający dane do zapisania do pliku.  
  
 `nBufSize`  
 Liczba bajtów do przeniesienia z buforu.  
  
 `pnBytesWritten`  
 Liczba zapisanych bajtów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [CAtlFile::Write](../../atl/reference/catlfile-class.md#write).  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasa CAtlFile](../../atl/reference/catlfile-class.md)
