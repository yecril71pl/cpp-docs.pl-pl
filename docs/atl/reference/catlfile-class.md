---
title: Klasa CAtlFile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
dev_langs:
- C++
helpviewer_keywords:
- CAtlFile class
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ecf0dc1907d2f78a844756d0efc8add04de6046
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885276"
---
# <a name="catlfile-class"></a>Klasa CAtlFile
Ta klasa dostarcza alokowania elastycznego otokę Windows plików obsługi interfejsu API.  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
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
|[CAtlFile::GetOverlappedResult](#getoverlappedresult)|Wywołaj tę metodę, aby uzyskać wyniki nachodzące operacji na pliku.|  
|[CAtlFile::GetPosition](#getposition)|Wywołaj tę metodę, aby uzyskać bieżącą pozycję wskaźnika w pliku z pliku.|  
|[CAtlFile::GetSize](#getsize)|Wywołaj tę metodę, aby uzyskać rozmiar w bajtach pliku.|  
|[CAtlFile::LockRange](#lockrange)|Wywołaj tę metodę, aby zablokować region, w pliku, aby uniemożliwić innym procesom uzyskiwanie do niej dostępu.|  
|[CAtlFile::Read](#read)|Wywołaj tę metodę można odczytać danych z pliku, zaczynając od pozycji wskazywanym przez wskaźnik pliku.|  
|[CAtlFile::Seek](#seek)|Wywołaj tę metodę, aby przesunąć wskaźnik pliku pliku.|  
|[CAtlFile::SetSize](#setsize)|Wywołaj tę metodę, aby ustawić rozmiar pliku.|  
|[CAtlFile::UnlockRange](#unlockrange)|Wywołaj tę metodę w celu odblokowania region pliku.|  
|[CAtlFile::Write](#write)|Wywołaj tę metodę można zapisać danych do pliku, zaczynając od pozycji wskazywanym przez wskaźnik pliku.|  
  
### <a name="protected-data-members"></a>Chronione elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlFile::m_pTM](#m_ptm)|Wskaźnik do `CAtlTransactionManager` obiektu|  
  
## <a name="remarks"></a>Uwagi  
 Klasa jest używana, gdy potrzeby obsługi plików jest stosunkowo prosta, ale abstrakcji więcej niż zapewnia interfejs API Windows jest wymagany, bez uwzględniania zależności biblioteki MFC.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CHandle](../../atl/reference/chandle-class.md)  
  
 `CAtlFile`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlfile.h  
  
##  <a name="catlfile"></a>  CAtlFile::CAtlFile  
 Konstruktor.  
  
```
CAtlFile() throw();
CAtlFile(CAtlTransactionManager* pTM = NULL) throw();
CAtlFile(CAtlFile& file) throw();
explicit CAtlFile(HANDLE hFile) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *Plik*  
 Obiekt pliku.  
  
 *hFile —*  
 Dojście do pliku.  
  
 *pTM*  
 Wskaźnik do obiektu CAtlTransactionManager  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor kopiujący tym przenosi własność dojście do pliku z oryginalnym `CAtlFile` obiekt do nowo utworzonym obiekcie.  
  
##  <a name="create"></a>  CAtlFile::Create  
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
  
 *dwDesiredAccess*  
 Żądany dostęp. Zobacz *dwDesiredAccess* w [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858) w zestawie Windows SDK.  
  
 *dwShareMode*  
 Tryb udostępniania. Zobacz *dwShareMode* w `CreateFile`.  
  
 *dwCreationDisposition*  
 Tworzenie dyspozycji. Zobacz *dwCreationDisposition* w `CreateFile`.  
  
 *dwFlagsAndAttributes*  
 Flagi i atrybutów. Zobacz *dwFlagsAndAttributes* w `CreateFile`.  
  
 *lpsa*  
 Atrybuty zabezpieczeń. Zobacz *lpSecurityAttributes* w `CreateFile`.  
  
 *hTemplateFile*  
 Plik szablonu. Zobacz *hTemplateFile* w `CreateFile`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858) do utworzenia lub otwarcia pliku.  
  
##  <a name="flush"></a>  CAtlFile::Flush  
 Wywołaj tę metodę, aby wyczyścić buforów dla pliku i spowodować, że wszystkie buforowane dane są zapisywane w pliku.  
  
```
HRESULT Flush() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [FlushFileBuffers](http://msdn.microsoft.com/library/windows/desktop/aa364439) opróżnić buforowane dane do pliku.  
  
##  <a name="getoverlappedresult"></a>  CAtlFile::GetOverlappedResult  
 Wywołaj tę metodę, aby uzyskać wyniki nachodzące operacji na pliku.  
  
```
HRESULT GetOverlappedResult(
    LPOVERLAPPED pOverlapped,
    DWORD& dwBytesTransferred,
    BOOL bWait) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pOverlapped*  
 Nachodzące struktury. Zobacz *lpOverlapped* w [GetOverlappedResult](http://msdn.microsoft.com/library/windows/desktop/ms683209) w zestawie Windows SDK.  
  
 *dwBytesTransferred*  
 Bajty przesłane. Zobacz *lpNumberOfBytesTransferred* w `GetOverlappedResult`.  
  
 *bWait*  
 Opcja oczekiwania. Zobacz *bWait* w `GetOverlappedResult`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [GetOverlappedResult](http://msdn.microsoft.com/library/windows/desktop/ms683209) można pobrać wyniki nachodzące operacji na pliku.  
  
##  <a name="getposition"></a>  CAtlFile::GetPosition  
 Wywołaj tę metodę, aby uzyskać bieżącą pozycję wskaźnika w pliku.  
  
```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *npos —*  
 Pozycja w bajtach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [funkcja SetFilePointer](http://msdn.microsoft.com/library/windows/desktop/aa365541) można pobrać bieżącą pozycję wskaźnika w pliku.  
  
##  <a name="getsize"></a>  CAtlFile::GetSize  
 Wywołaj tę metodę, aby uzyskać rozmiar w bajtach pliku.  
  
```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nLen*  
 Liczba bajtów w pliku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [funkcji GetFileSize](http://msdn.microsoft.com/library/windows/desktop/aa364955) Aby uzyskać rozmiar w bajtach pliku.  
  
##  <a name="lockrange"></a>  CAtlFile::LockRange  
 Wywołaj tę metodę, aby zablokować region, w pliku, aby uniemożliwić innym procesom uzyskiwanie do niej dostępu.  
  
```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *npos —*  
 Pozycja w pliku, w którym ma się zacząć blokady.  
  
 *nCount*  
 Długość zakresu bajtów do zablokowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [LockFile](http://msdn.microsoft.com/library/windows/desktop/aa365202) zablokować regionu w pliku. Blokowanie bajtów w pliku uniemożliwia dostęp do tych bajtów przez inne procesy. Możesz zablokować więcej niż jeden region pliku, ale nie nakładających się regiony są dozwolone. Po odblokowaniu region, za pomocą [CAtlFile::UnlockRange](#unlockrange), zakres bajtów musi dokładnie odpowiadać elementowi region, który wcześniej został zablokowany. `LockRange` Scala sąsiadujących regiony; Jeśli dwa regiony zablokowane sąsiadujących ze sobą, musisz odblokować każdego oddzielnie.  
  
##  <a name="m_ptm"></a>  CAtlFile::m_pTM  
 Wskaźnik do `CAtlTransactionManager` obiektu.  
  
```
CAtlTransactionManager* m_pTM;
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="read"></a>  CAtlFile::Read  
 Wywołaj tę metodę można odczytać danych z pliku, zaczynając od pozycji wskazywanym przez wskaźnik pliku.  
  
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
 *pBuffer*  
 Wskaźnik do buforu, który będzie otrzymywać dane odczytane z pliku.  
  
 *nBufSize*  
 Rozmiar buforu w bajtach.  
  
 *nBytesRead*  
 Liczba odczytanych bajtów.  
  
 *pOverlapped*  
 Nachodzące struktury. Zobacz *lpOverlapped* w [ReadFile](http://msdn.microsoft.com/library/windows/desktop/aa365467) w zestawie Windows SDK.  
  
 *pfnCompletionRoutine*  
 Procedura ukończenia. Zobacz *lpCompletionRoutine* w [ReadFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365468) w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Pierwsze trzy formularze wywołać [ReadFile](http://msdn.microsoft.com/library/windows/desktop/aa365467), ostatni [ReadFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365468) można odczytać danych z pliku. Użyj [CAtlFile::Seek](#seek) przesuwanie wskaźnika pliku.  
  
##  <a name="seek"></a>  CAtlFile::Seek  
 Wywołaj tę metodę, aby przesunąć wskaźnik pliku pliku.  
  
```
HRESULT Seek(
    LONGLONG nOffset,
    DWORD dwFrom = FILE_CURRENT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nOffset*  
 Przesunięcie od początkowego punktu określonego przez właściwość *dwFrom*.  
  
 *dwFrom*  
 Punkt początkowy (FILE_BEGIN, FILE_CURRENT lub FILE_END).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [funkcja SetFilePointer](http://msdn.microsoft.com/library/windows/desktop/aa365541) przesuwanie wskaźnika pliku.  
  
##  <a name="setsize"></a>  CAtlFile::SetSize  
 Wywołaj tę metodę, aby ustawić rozmiar pliku.  
  
```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *nNewLen*  
 Długość nowego pliku w bajtach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [funkcja SetFilePointer](http://msdn.microsoft.com/library/windows/desktop/aa365541) i [funkcji SetEndOfFile](http://msdn.microsoft.com/library/windows/desktop/aa365531) można ustawić rozmiar pliku. Przy powrocie wskaźnik pliku jest umieszczony na końcu pliku.  
  
##  <a name="unlockrange"></a>  CAtlFile::UnlockRange  
 Wywołaj tę metodę w celu odblokowania region pliku.  
  
```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *npos —*  
 Pozycja w pliku, w którym ma się zacząć unlock.  
  
 *nCount*  
 Długość zakresu bajtów do odblokowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [UnlockFile](http://msdn.microsoft.com/library/windows/desktop/aa365715) do odblokowania region pliku.  
  
##  <a name="write"></a>  CAtlFile::Write  
 Wywołaj tę metodę można zapisać danych do pliku, zaczynając od pozycji wskazywanym przez wskaźnik pliku.  
  
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
 *pBuffer*  
 Bufor zawierające dane są zapisywane w pliku.  
  
 *nBufSize*  
 Liczba bajtów, które mają zostać przeniesione z buforu.  
  
 *pOverlapped*  
 Nachodzące struktury. Zobacz *lpOverlapped* w [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747) w zestawie Windows SDK.  
  
 *pfnCompletionRoutine*  
 Procedura ukończenia. Zobacz *lpCompletionRoutine* w [WriteFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365748) w zestawie Windows SDK.  
  
 *pnBytesWritten*  
 Bajty zapisane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Pierwsze trzy formularze wywołać [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747), ostatniego wywołania [WriteFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365748) można zapisać danych do pliku. Użyj [CAtlFile::Seek](#seek) przesuwanie wskaźnika pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe Neon](../../visual-cpp-samples.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)   
 [Klasa CHandle](../../atl/reference/chandle-class.md)
