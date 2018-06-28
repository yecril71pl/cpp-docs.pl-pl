---
title: Klasa CGopherFileFind | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGopherFileFind
- AFXINET/CGopherFileFind
- AFXINET/CGopherFileFind::CGopherFileFind
- AFXINET/CGopherFileFind::FindFile
- AFXINET/CGopherFileFind::FindNextFile
- AFXINET/CGopherFileFind::GetCreationTime
- AFXINET/CGopherFileFind::GetLastAccessTime
- AFXINET/CGopherFileFind::GetLastWriteTime
- AFXINET/CGopherFileFind::GetLength
- AFXINET/CGopherFileFind::GetLocator
- AFXINET/CGopherFileFind::GetScreenName
- AFXINET/CGopherFileFind::IsDots
dev_langs:
- C++
helpviewer_keywords:
- CGopherFileFind [MFC], CGopherFileFind
- CGopherFileFind [MFC], FindFile
- CGopherFileFind [MFC], FindNextFile
- CGopherFileFind [MFC], GetCreationTime
- CGopherFileFind [MFC], GetLastAccessTime
- CGopherFileFind [MFC], GetLastWriteTime
- CGopherFileFind [MFC], GetLength
- CGopherFileFind [MFC], GetLocator
- CGopherFileFind [MFC], GetScreenName
- CGopherFileFind [MFC], IsDots
ms.assetid: 8465a979-6323-496d-ab4b-e81383fb999d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eae84c647f068e49136968e60bfd8bd51a528112
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038532"
---
# <a name="cgopherfilefind-class"></a>Klasa CGopherFileFind
Pomoc w wyszukiwania plików internetowych serwerów gopher.  
  
> [!NOTE]
>  Klasy `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` i ich elementy członkowskie są przestarzałe, ponieważ nie działają na platformie Windows XP, ale będą one nadal działać na starszych platformach.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CGopherFileFind : public CFileFind  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CGopherFileFind::CGopherFileFind](#cgopherfilefind)|Konstruuje `CGopherFileFind` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CGopherFileFind::FindFile](#findfile)|Umożliwia znalezienie pliku na serwerze gopher.|  
|[CGopherFileFind::FindNextFile](#findnextfile)|Kontynuuje wyszukiwanie plików z poprzedniego wywołania [FindFile](#findfile).|  
|[CGopherFileFind::GetCreationTime](#getcreationtime)|Pobiera godzinę utworzenia określonego pliku.|  
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|Pobiera czas ostatniego dostępu do określonego pliku.|  
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|Pobiera czas ostatniej zostało zapisane określonego pliku.|  
|[CGopherFileFind::GetLength](#getlength)|Pobiera długość znaleziony plik, w bajtach.|  
|[CGopherFileFind::GetLocator](#getlocator)|Pobierz `CGopherLocator` obiektu.|  
|[CGopherFileFind::GetScreenName](#getscreenname)|Pobiera nazwę ekranu gopher.|  
|[CGopherFileFind::IsDots](#isdots)|Testy dla bieżącego katalogu nadrzędnego katalogu znaczniki i podczas iteracji plików.|  
  
## <a name="remarks"></a>Uwagi  
 `CGopherFileFind` obejmuje funkcje Członkowskie, które rozpocząć wyszukiwanie, zlokalizuj plik i zwraca adres URL pliku.  
  
 Inne klasy MFC przeznaczony dla Internet i lokalny plik przeszukiwane obejmują [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) i [CFileFind](../../mfc/reference/cfilefind-class.md). Razem z `CGopherFileFind`, te klasy mechanizm łatwego dla użytkownika o znalezienie określonych plików, niezależnie od protokołu serwera, typu pliku i lokalizację (komputer lokalny lub zdalny serwer.) Należy zauważyć, że nie jest Brak klasy MFC do wyszukiwania na serwerach HTTP, ponieważ HTTP nie obsługuje manipulowania bezpośredniego pliku wymagane przez wyszukiwania.  
  
> [!NOTE]
> `CGopherFileFind` nie obsługuje następujące funkcje elementu członkowskiego klasy podstawowej [CFileFind](../../mfc/reference/cfilefind-class.md):  
  
- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)  
  
- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)  
  
- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)  
  
- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)  
  
- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)  
  
 Ponadto, gdy jest używany z `CGopherFileFind`, `CFileFind` funkcji członkowskiej [IsDots](../../mfc/reference/cfilefind-class.md#isdots) jest zawsze **FALSE**.  
  
 Aby uzyskać więcej informacji o sposobie używania `CGopherFileFind` i innych klasach WinInet, zobacz artykuł [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFileFind](../../mfc/reference/cfilefind-class.md)  
  
 `CGopherFileFind`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
  
##  <a name="cgopherfilefind"></a>  CGopherFileFind::CGopherFileFind  
 Ta funkcja elementu członkowskiego jest wywoływana w celu utworzenia `CGopherFileFind` obiektu.  
  
```  
explicit CGopherFileFind(
    CGopherConnection* pConnection,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 *pConnection*  
 Wskaźnik do [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) obiektu.  
  
 *dwContext*  
 Identyfikator kontekstu dla tej operacji. Zobacz **uwagi** uzyskać więcej informacji o *dwContext*.  
  
### <a name="remarks"></a>Uwagi  
 Wartość domyślna dla *dwContext* są wysyłane przez MFC do `CGopherFileFind` obiekt z [CInternetSession](../../mfc/reference/cinternetsession-class.md) utworzony obiekt `CGopherFileFind` obiektu. Podczas konstruowania `CGopherFileFind` obiektu, można zastąpić domyślną ustawioną wartość wybrane identyfikator kontekstu. Identyfikator kontekstu jest zwracana do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zapewnienie stanu dla obiektu, z którym zostanie zidentyfikowana. Zapoznaj się z artykułem [pierwsze kroki Internet: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.  
  
##  <a name="findfile"></a>  CGopherFileFind::FindFile  
 Wywołanie tej funkcji Członkowskich, aby znaleźć plik gopher.  
  
```  
virtual BOOL FindFile(
    CGopherLocator& refLocator,  
    LPCTSTR pstrString,  
    DWORD dwFlags = INTERNET_FLAG_RELOAD);

 
virtual BOOL FindFile(
    LPCTSTR pstrString,  
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```  
  
### <a name="parameters"></a>Parametry  
 *refLocator*  
 Odwołanie do [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) obiektu.  
  
 *pstrString*  
 Wskaźnik do ciąg zawierający nazwę pliku.  
  
 *wartość elementu dwFlags*  
 Flagi opisujące sposób obsługi tej sesji. Prawidłowe flagi są:  
  
-   INTERNET_FLAG_RELOAD Pobierz dane z serwera zdalnego, nawet jeśli jest buforowany lokalnie.  
  
-   INTERNET_FLAG_DONT_CACHE nie buforują danych lokalnie lub w żadnych bram.  
  
-   Żądanie INTERNET_FLAG_SECURE zabezpieczone transakcje umieszczonego Secure Sockets Layer lub procent Ta flaga jest dotyczy tylko żądania HTTP.  
  
-   INTERNET_FLAG_USE_EXISTING, jeśli to możliwe, ponowne użycie istniejących połączeń z serwerem o nowych **FindFile** żądania, zamiast tworzenia nowej sesji dla każdego żądania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. Aby uzyskać rozszerzone informacje o błędzie, wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu **FindFile** można pobrać pierwszy obiekt gopher, można wywołać [FindNextFile](#findnextfile) do pobierania plików gopher kolejne.  
  
##  <a name="findnextfile"></a>  CGopherFileFind::FindNextFile  
 Wywołanie tej funkcji Członkowskich, aby kontynuować wyszukiwanie plików uruchomione za pomocą wywołania [CGopherFileFind::FindFile](#findfile).  
  
```  
virtual BOOL FindNextFile();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ma więcej plików; zero, jeśli znaleziono plik jest ostatnim w katalogu lub wystąpił błąd. Aby uzyskać rozszerzone informacje o błędzie, wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360). Jeśli znaleziono pliku ostatniego pliku w katalogu, lub jeśli pasujących plików można znaleźć `GetLastError` funkcja zwraca ERROR_NO_MORE_FILES.  
  
##  <a name="getcreationtime"></a>  CGopherFileFind::GetCreationTime  
 Pobiera czas utworzenia dla bieżącego pliku.  
  
```  
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;  
virtual BOOL GetCreationTime(CTime& refTime) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pTimeStamp*  
 Wskaźnik do [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) struktury zawierającej czas utworzenia pliku.  
  
 *refTime*  
 Odwołanie do [ctime —](../../atl-mfc-shared/reference/ctime-class.md) obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; 0 w przypadku niepowodzenia. `GetCreationTime` Zwraca wartość 0, tylko wtedy, gdy [FindNextFile](#findnextfile) nigdy nie została wywołana na tym `CGopherFileFind` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetCreationTime`.  
  
> [!NOTE]
>  Nie wszystkie systemy plików użycie tej samej semantyki do zaimplementowania sygnaturę czasową zwracane przez tę funkcję. Ta funkcja może zwrócić taką samą wartość zwrócona przez inne funkcje sygnatury czasu, jeśli źródłowy system plików lub serwer nie obsługuje atrybutu czas przechowywania. Zobacz [Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktury informacji o formaty czasu. W niektórych systemach operacyjnych zwrócony czas jest w czasie lokalnej strefy do komputera, w której znajduje się plik. Zobacz Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) interfejsu API, aby uzyskać więcej informacji.  
  
##  <a name="getlastaccesstime"></a>  CGopherFileFind::GetLastAccessTime  
 Pobiera czas ostatniego dostępu do określonego pliku.  
  
```  
virtual BOOL GetLastAccessTime(CTime& refTime) const;  
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *refTime*  
 Odwołanie do [ctime —](../../atl-mfc-shared/reference/ctime-class.md) obiektu.  
  
 *pTimeStamp*  
 Wskaźnik do [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) struktury zawierającej czas ostatniego dostępu do pliku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; 0 w przypadku niepowodzenia. `GetLastAccessTime` Zwraca wartość 0, tylko wtedy, gdy [FindNextFile](#findnextfile) nigdy nie została wywołana na tym `CGopherFileFind` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetLastAccessTime`.  
  
> [!NOTE]
>  Nie wszystkie systemy plików użycie tej samej semantyki do zaimplementowania sygnaturę czasową zwracane przez tę funkcję. Ta funkcja może zwrócić taką samą wartość zwrócona przez inne funkcje sygnatury czasu, jeśli źródłowy system plików lub serwer nie obsługuje atrybutu czas przechowywania. Zobacz [Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktury informacji o formaty czasu. W niektórych systemach operacyjnych zwrócony czas jest w czasie lokalnej strefy do komputera, w której znajduje się plik. Zobacz Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) interfejsu API, aby uzyskać więcej informacji.  
  
##  <a name="getlastwritetime"></a>  CGopherFileFind::GetLastWriteTime  
 Pobiera czasu, gdy plik został zmieniony.  
  
```  
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;  
virtual BOOL GetLastWriteTime(CTime& refTime) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pTimeStamp*  
 Wskaźnik do [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) struktury zawierającej czas ostatniego został zapisany plik.  
  
 *refTime*  
 Odwołanie do [ctime —](../../atl-mfc-shared/reference/ctime-class.md) obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; 0 w przypadku niepowodzenia. `GetLastWriteTime` Zwraca wartość 0, tylko wtedy, gdy [FindNextFile](#findnextfile) nigdy nie została wywołana na tym `CGopherFileFind` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetLastWriteTime`.  
  
> [!NOTE]
>  Nie wszystkie systemy plików użycie tej samej semantyki do zaimplementowania sygnaturę czasową zwracane przez tę funkcję. Ta funkcja może zwrócić taką samą wartość zwrócona przez inne funkcje sygnatury czasu, jeśli źródłowy system plików lub serwer nie obsługuje atrybutu czas przechowywania. Zobacz [Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktury informacji o formaty czasu. W niektórych systemach operacyjnych zwrócony czas jest w czasie lokalnej strefy do komputera, w której znajduje się plik. Zobacz Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) interfejsu API, aby uzyskać więcej informacji.  
  
##  <a name="getlength"></a>  CGopherFileFind::GetLength  
 Wywołanie tej funkcji członkowskich można pobrać długości w bajtach znaleziony plik.  
  
```  
virtual ULONGLONG GetLength() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość, w bajtach znaleziony plik.  
  
### <a name="remarks"></a>Uwagi  
 `GetLength` używa struktury Win32 [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) można uzyskać wartość rozmiaru pliku w bajtach.  
  
> [!NOTE]
>  Począwszy od MFC 7.0 `GetLength` obsługuje typy 64-bitową liczbę całkowitą. Kod istniejących wcześniej skompilowanej za pomocą tego nowszej wersji biblioteki może spowodować obcięcie ostrzeżenia.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) (implementacji klasy podstawowej).  
  
##  <a name="getlocator"></a>  CGopherFileFind::GetLocator  
 Wywołanie tej funkcji Członkowskich, aby uzyskać [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) obiekt, który [FindFile](#findfile) używa można znaleźć pliku gopher.  
  
```  
CGopherLocator GetLocator() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CGopherLocator` obiektu.  
  
##  <a name="getscreenname"></a>  CGopherFileFind::GetScreenName  
 Wywołanie tej funkcji Członkowskich nazwy gopher ekranu.  
  
```  
CString GetScreenName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa gopher ekranu.  
  
##  <a name="isdots"></a>  CGopherFileFind::IsDots  
 Testy dla bieżącego katalogu nadrzędnego katalogu znaczniki i podczas iteracji plików.  
  
```  
virtual BOOL IsDots() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli znaleziono plik ma nazwę "."lub"..", co oznacza, że znaleziony plik jest w rzeczywistości katalogiem. W przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsDots`.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CFileFind](../../mfc/reference/cfilefind-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)   
 [Klasa CFileFind](../../mfc/reference/cfilefind-class.md)   
 [Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)   
 [Cgopherfile — klasa](../../mfc/reference/cgopherfile-class.md)   
 [Klasa CHttpFile](../../mfc/reference/chttpfile-class.md)
