---
title: Klasa CAtlFile | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlFile
- ATLFILE/ATL::CAtlFile
- ATLFILE/ATL::CAtlFile::CAtlFile
- ATLFILE/ATL::CAtlFile::Create
- ATLFILE/ATL::CAtlFile::Flush
- ATLFILE/ATL::CAtlFile::GetOverlappedResult
- ATLFILE/ATL::CAtlFile::GetPosition
- ATLFILE/ATL::CAtlFile::GetSize
- ATLFILE/ATL::CAtlFile::LockRange
- ATLFILE/ATL::CAtlFile::Read
- ATLFILE/ATL::CAtlFile::Seek
- ATLFILE/ATL::CAtlFile::SetSize
- ATLFILE/ATL::CAtlFile::UnlockRange
- ATLFILE/ATL::CAtlFile::Write
- ATLFILE/ATL::CAtlFile::m_pTM
dev_langs: C++
helpviewer_keywords: CAtlFile class
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a66e697a3599e7bfeef0f1d5d147e19b668222ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="catlfile-class"></a>Klasa CAtlFile
Ta klasa udostępnia cienką otoką wokół systemu Windows, plików obsługi interfejsu API.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CAtlFile : public CHandle
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlFile::CAtlFile](#catlfile)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlFile::Create](#create)|Wywołaj tę metodę, aby utworzyć lub otworzyć pliku.|  
|[CAtlFile::Flush](#flush)|Wywołaj tę metodę, aby wyczyścić buforów dla pliku i spowodować, że wszystkie buforowane dane są zapisywane w pliku.|  
|[CAtlFile::GetOverlappedResult](#getoverlappedresult)|Wywołanie tej metody, aby uzyskać wyniki nachodzące operacji na pliku.|  
|[CAtlFile::GetPosition](#getposition)|Wywołaj tę metodę, aby uzyskać bieżącą pozycję wskaźnika pliku z pliku.|  
|[CAtlFile::GetSize](#getsize)|Wywołaj tę metodę, aby pobrać rozmiar w bajtach pliku.|  
|[CAtlFile::LockRange](#lockrange)|Wywołaj tę metodę, aby zablokować region, w pliku, aby uniemożliwić dostęp do jej przez inne procesy.|  
|[CAtlFile::Read](#read)|Wywołaj tę metodę w celu odczytania danych z pliku, zaczynając od pozycji wskaźnika pliku.|  
|[CAtlFile::Seek](#seek)|Wywołanie tej metody można przenieść pliku wskaźnika pliku.|  
|[CAtlFile::SetSize](#setsize)|Wywołanie tej metody, aby ustawić limit rozmiaru pliku.|  
|[CAtlFile::UnlockRange](#unlockrange)|Wywołaj tę metodę, aby odblokować regionu pliku.|  
|[CAtlFile::Write](#write)|Wywołanie tej metody można zapisać danych do pliku, zaczynając od pozycji wskaźnika pliku.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlFile::m_pTM](#m_ptm)|Wskaźnik do `CAtlTransactionManager` obiektu|  
  
## <a name="remarks"></a>Uwagi  
 Podczas obsługi plików są stosunkowo proste, ale abstrakcji więcej niż interfejs API systemu Windows jest wymagany, bez wraz z zależnościami MFC, należy użyć tej klasy.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CHandle](../../atl/reference/chandle-class.md)  
  
 `CAtlFile`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlfile.h  
  
##  <a name="catlfile"></a>CAtlFile::CAtlFile  
 Konstruktor.  
  
```
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `file`  
 Obiekt pliku.  
  
 `hFile`  
 Dojście do pliku.  
  
 `pTM`  
 Wskaźnik do obiektu CAtlTransactionManager  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor kopiujący przesyła własność dojście do pliku z oryginalnym `CAtlFile` obiekt do nowo skonstruowanego obiektu.  
  
##  <a name="create"></a>CAtlFile::Create  
 Wywołaj tę metodę, aby utworzyć lub otworzyć pliku.  
  
```
HRESULT Create(
    LPCTSTR szFilename,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes = FILE_ATTRIBUTE_NORMAL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    HANDLE hTemplateFile = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *szFilename*  
 Nazwa pliku.  
  
 `dwDesiredAccess`  
 Żądany dostęp. Zobacz `dwDesiredAccess` w [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858) w systemie Windows SDK.  
  
 `dwShareMode`  
 Tryb udostępniania. Zobacz `dwShareMode` w **CreateFile**.  
  
 `dwCreationDisposition`  
 Tworzenie dyspozycji. Zobacz `dwCreationDisposition` w **CreateFile**.  
  
 `dwFlagsAndAttributes`  
 Flagi i atrybutów. Zobacz `dwFlagsAndAttributes` w **CreateFile**.  
  
 `lpsa`  
 Atrybuty zabezpieczeń. Zobacz *lpSecurityAttributes* w **CreateFile**.  
  
 `hTemplateFile`  
 Plik szablonu. Zobacz `hTemplateFile` w **CreateFile**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858) można utworzyć lub otworzyć pliku.  
  
##  <a name="flush"></a>CAtlFile::Flush  
 Wywołaj tę metodę, aby wyczyścić buforów dla pliku i spowodować, że wszystkie buforowane dane są zapisywane w pliku.  
  
```
HRESULT Flush() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [opróżnienie buforów plików przez](http://msdn.microsoft.com/library/windows/desktop/aa364439) opróżnić buforowane dane do pliku.  
  
##  <a name="getoverlappedresult"></a>CAtlFile::GetOverlappedResult  
 Wywołanie tej metody, aby uzyskać wyniki nachodzące operacji na pliku.  
  
```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pOverlapped`  
 Nachodzące struktury. Zobacz `lpOverlapped` w [GetOverlappedResult](http://msdn.microsoft.com/library/windows/desktop/ms683209) w systemie Windows SDK.  
  
 *dwBytesTransferred*  
 Przesłanych bajtów. Zobacz *lpNumberOfBytesTransferred* w `GetOverlappedResult`.  
  
 `bWait`  
 Opcja oczekiwania. Zobacz `bWait` w `GetOverlappedResult`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [GetOverlappedResult](http://msdn.microsoft.com/library/windows/desktop/ms683209) Aby uzyskać wyniki nachodzące operacji na pliku.  
  
##  <a name="getposition"></a>CAtlFile::GetPosition  
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
 Wywołania [funkcji SetFilePointer](http://msdn.microsoft.com/library/windows/desktop/aa365541) można pobrać bieżącą pozycję wskaźnika pliku.  
  
##  <a name="getsize"></a>CAtlFile::GetSize  
 Wywołaj tę metodę, aby pobrać rozmiar w bajtach pliku.  
  
```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nLen`  
 Liczba bajtów w pliku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [funkcji GetFileSize](http://msdn.microsoft.com/library/windows/desktop/aa364955) można pobrać rozmiar w bajtach pliku.  
  
##  <a name="lockrange"></a>CAtlFile::LockRange  
 Wywołaj tę metodę, aby zablokować region, w pliku, aby uniemożliwić dostęp do jej przez inne procesy.  
  
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
 Wywołania [LockFile](http://msdn.microsoft.com/library/windows/desktop/aa365202) zablokować regionu w pliku. Blokowanie bajtów w pliku uniemożliwia dostęp do tych bajtów przez inne procesy. Można zablokować więcej niż jeden region, pliku, ale nie nakładające się regiony są dozwolone. Po odblokowaniu region przy użyciu [CAtlFile::UnlockRange](#unlockrange), zakres bajtów musi dokładnie odpowiadać region, który wcześniej był zablokowany. `LockRange`Scala sąsiadujących ze sobą regionów; Jeśli dwóch regionach zablokowanym sąsiadujących ze sobą, należy odblokować każdego oddzielnie.  
  
##  <a name="m_ptm"></a>CAtlFile::m_pTM  
 Wskaźnik do `CAtlTransactionManager` obiektu.  
  
```
CAtlTransactionManager* m_pTM;
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="read"></a>CAtlFile::Read  
 Wywołaj tę metodę w celu odczytania danych z pliku, zaczynając od pozycji wskaźnika pliku.  
  
```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();

HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pBuffer`  
 Wskaźnik do buforu, który będzie odbierać dane z pliku do odczytu.  
  
 `nBufSize`  
 Rozmiar buforu w bajtach.  
  
 `nBytesRead`  
 Liczba bajtów odczytanych.  
  
 `pOverlapped`  
 Nachodzące struktury. Zobacz `lpOverlapped` w [ReadFile](http://msdn.microsoft.com/library/windows/desktop/aa365467) w systemie Windows SDK.  
  
 `pfnCompletionRoutine`  
 Procedura ukończenia. Zobacz *lpCompletionRoutine* w [ReadFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365468) w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Pierwsze trzy formularze wywołać [ReadFile](http://msdn.microsoft.com/library/windows/desktop/aa365467), ostatniego [ReadFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365468) można odczytać danych z pliku. Użyj [CAtlFile::Seek](#seek) przesuwanie wskaźnika pliku.  
  
##  <a name="seek"></a>CAtlFile::Seek  
 Wywołanie tej metody można przenieść pliku wskaźnika pliku.  
  
```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nOffset`  
 Przesunięcie od początkowego punktu określonego przez `dwFrom`.  
  
 `dwFrom`  
 Punkt początkowy (FILE_BEGIN, FILE_CURRENT lub FILE_END).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [funkcji SetFilePointer](http://msdn.microsoft.com/library/windows/desktop/aa365541) przesuwanie wskaźnika pliku.  
  
##  <a name="setsize"></a>CAtlFile::SetSize  
 Wywołanie tej metody, aby ustawić limit rozmiaru pliku.  
  
```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nNewLen`  
 Długość nowego pliku w bajtach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [funkcji SetFilePointer](http://msdn.microsoft.com/library/windows/desktop/aa365541) i [funkcji SetEndOfFile](http://msdn.microsoft.com/library/windows/desktop/aa365531) można ustawić rozmiaru pliku. Przy powrocie wskaźnika pliku znajduje się na końcu pliku.  
  
##  <a name="unlockrange"></a>CAtlFile::UnlockRange  
 Wywołaj tę metodę, aby odblokować regionu pliku.  
  
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
 Wywołania [UnlockFile](http://msdn.microsoft.com/library/windows/desktop/aa365715) do odblokowania regionu pliku.  
  
##  <a name="write"></a>CAtlFile::Write  
 Wywołanie tej metody można zapisać danych do pliku, zaczynając od pozycji wskaźnika pliku.  
  
```
HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped,
    LPOVERLAPPED_COMPLETION_ROUTINE pfnCompletionRoutine) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();

HRESULT Write(
    LPCVOID pBuffer,
    DWORD nBufSize,
    LPOVERLAPPED pOverlapped) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pBuffer`  
 Bufor zawierający dane do zapisania do pliku.  
  
 `nBufSize`  
 Liczba bajtów do przeniesienia z buforu.  
  
 `pOverlapped`  
 Nachodzące struktury. Zobacz `lpOverlapped` w [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747) w systemie Windows SDK.  
  
 `pfnCompletionRoutine`  
 Procedura ukończenia. Zobacz *lpCompletionRoutine* w [WriteFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365748) w zestawie Windows SDK.  
  
 `pnBytesWritten`  
 Zapisanych bajtów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` na powodzenie lub błąd `HRESULT` w przypadku awarii.  
  
### <a name="remarks"></a>Uwagi  
 Pierwsze trzy formularze wywołać [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747), ostatni wywołania [WriteFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365748) można zapisać danych do pliku. Użyj [CAtlFile::Seek](#seek) przesuwanie wskaźnika pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe ramki](../../visual-cpp-samples.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasa CHandle](../../atl/reference/chandle-class.md)
