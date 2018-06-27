---
title: Klasa CFileFind | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFileFind
- AFX/CFileFind
- AFX/CFileFind::CFileFind
- AFX/CFileFind::Close
- AFX/CFileFind::FindFile
- AFX/CFileFind::FindNextFile
- AFX/CFileFind::GetCreationTime
- AFX/CFileFind::GetFileName
- AFX/CFileFind::GetFilePath
- AFX/CFileFind::GetFileTitle
- AFX/CFileFind::GetFileURL
- AFX/CFileFind::GetLastAccessTime
- AFX/CFileFind::GetLastWriteTime
- AFX/CFileFind::GetLength
- AFX/CFileFind::GetRoot
- AFX/CFileFind::IsArchived
- AFX/CFileFind::IsCompressed
- AFX/CFileFind::IsDirectory
- AFX/CFileFind::IsDots
- AFX/CFileFind::IsHidden
- AFX/CFileFind::IsNormal
- AFX/CFileFind::IsReadOnly
- AFX/CFileFind::IsSystem
- AFX/CFileFind::IsTemporary
- AFX/CFileFind::MatchesMask
- AFX/CFileFind::CloseContext
- AFX/CFileFind::m_pTM
dev_langs:
- C++
helpviewer_keywords:
- CFileFind [MFC], CFileFind
- CFileFind [MFC], Close
- CFileFind [MFC], FindFile
- CFileFind [MFC], FindNextFile
- CFileFind [MFC], GetCreationTime
- CFileFind [MFC], GetFileName
- CFileFind [MFC], GetFilePath
- CFileFind [MFC], GetFileTitle
- CFileFind [MFC], GetFileURL
- CFileFind [MFC], GetLastAccessTime
- CFileFind [MFC], GetLastWriteTime
- CFileFind [MFC], GetLength
- CFileFind [MFC], GetRoot
- CFileFind [MFC], IsArchived
- CFileFind [MFC], IsCompressed
- CFileFind [MFC], IsDirectory
- CFileFind [MFC], IsDots
- CFileFind [MFC], IsHidden
- CFileFind [MFC], IsNormal
- CFileFind [MFC], IsReadOnly
- CFileFind [MFC], IsSystem
- CFileFind [MFC], IsTemporary
- CFileFind [MFC], MatchesMask
- CFileFind [MFC], CloseContext
- CFileFind [MFC], m_pTM
ms.assetid: 9990068c-b023-4114-9580-a50182d15240
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de63a53e23f4ea22a6fe8df7ab55bfc57d409779
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955079"
---
# <a name="cfilefind-class"></a>Klasa CFileFind
Przeprowadza wyszukiwanie pliku lokalnego i jest klasą bazową dla [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) i [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md), który wykonać wyszukiwania plików z Internetu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CFileFind : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFileFind::CFileFind](#cfilefind)|Konstruuje `CFileFind` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFileFind::Close](#close)|Zamknięcie żądania wyszukiwania.|  
|[CFileFind::FindFile](#findfile)|Wyszukuje katalog dla określonej nazwy pliku.|  
|[CFileFind::FindNextFile](#findnextfile)|Kontynuuje wyszukiwanie plików z poprzedniego wywołania [FindFile](#findfile).|  
|[CFileFind::GetCreationTime](#getcreationtime)|Pobiera godzinę utworzenia pliku.|  
|[CFileFind::GetFileName](#getfilename)|Pobiera nazwę, wraz z rozszerzeniem pliku znaleziono|  
|[CFileFind::GetFilePath](#getfilepath)|Pobiera pełną ścieżkę znaleziony plik.|  
|[CFileFind::GetFileTitle](#getfiletitle)|Pobiera tytuł znaleziony plik. Tytuł nie zawiera rozszerzenia.|  
|[CFileFind::GetFileURL](#getfileurl)|Pobiera adres URL, łącznie ze ścieżką pliku znalezionego pliku.|  
|[CFileFind::GetLastAccessTime](#getlastaccesstime)|Pobiera czas ostatniego dostępu do pliku.|  
|[CFileFind::GetLastWriteTime](#getlastwritetime)|Pobiera godzinę plik został ostatnio zmieniony i zapisany.|  
|[CFileFind::GetLength](#getlength)|Pobiera długość znaleziony plik, w bajtach.|  
|[CFileFind::GetRoot](#getroot)|Pobiera katalog główny znaleziony plik.|  
|[CFileFind::IsArchived](#isarchived)|Określa, jeśli znaleziono plik zostaną zarchiwizowane.|  
|[CFileFind::IsCompressed](#iscompressed)|Określa, jeśli znaleziono plik jest skompresowany.|  
|[CFileFind::IsDirectory](#isdirectory)|Określa, czy znaleziony plik jest katalogiem.|  
|[CFileFind::IsDots](#isdots)|Określa, czy nazwa znaleziony plik ma nazwę "."lub"..", co oznacza, że jest w rzeczywistości katalogiem.|  
|[CFileFind::IsHidden](#ishidden)|Określa, jeśli znaleziono plik jest ukryty.|  
|[CFileFind::IsNormal](#isnormal)|Określa, czy plik znaleziono jest normalne (innymi słowy, nie ma żadnych innych atrybutów).|  
|[CFileFind::IsReadOnly](#isreadonly)|Określa, czy znaleziony plik jest tylko do odczytu.|  
|[CFileFind::IsSystem](#issystem)|Określa, czy plik znaleziono plik systemowy.|  
|[CFileFind::IsTemporary](#istemporary)|Określa, czy znaleziony plik tymczasowy.|  
|[CFileFind::MatchesMask](#matchesmask)|Określa atrybuty pliku żądanego pliku, który ma zostać odnaleziona.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFileFind::CloseContext](#closecontext)|Zamyka określonego przez dojście wyszukiwania bieżącego pliku.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFileFind::m_pTM](#m_ptm)|Wskaźnik do `CAtlTransactionManager` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CFileFind` obejmuje funkcje Członkowskie, które rozpocząć wyszukiwanie, zlokalizuj plik i zwracać tytuł, nazwa lub ścieżka do pliku. Wyszukiwanie Internet funkcji członkowskiej [GetFileURL](#getfileurl) zwraca adres URL pliku.  
  
 `CFileFind` Klasa podstawowa dla dwóch klas MFC zaprojektowano w celu wyszukiwania typów konkretnego serwera: `CGopherFileFind` działa z serwerów gopher i `CFtpFileFind` działa z serwerami FTP. Razem tych trzech klas mechanizm łatwego klienta można znaleźć plików, niezależnie od tego, czy protokół serwera, typ pliku lub lokalizacji, na komputerze lokalnym lub serwerze zdalnym.  
  
 Poniższy kod powoduje wyliczenie wszystkich plików w bieżącym katalogu drukowanie nazwy każdego pliku:  
  
 [!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]  
  
 Aby zachować prosty przykład, ten kod używa standardowa biblioteka C++ `cout` klasy. `cout` Wiersza mogły zostać zastąpione przez wywołanie do `CListBox::AddString`, na przykład w programie z graficznego interfejsu użytkownika.  
  
 Aby uzyskać więcej informacji o sposobie używania `CFileFind` i innych klasach WinInet, zobacz artykuł [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CFileFind`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
##  <a name="cfilefind"></a>  CFileFind::CFileFind  
 Ta funkcja członkowska jest wywoływane, gdy `CFileFind` konstruowania obiektu.  
  
```  
CFileFind();  
CFileFind(CAtlTransactionManager* pTM);
```  
  
### <a name="parameters"></a>Parametry  
 *pTM*  
 Wskaźnik do obiektu CAtlTransactionManager  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::GetFileName](#getfilename).  
  
##  <a name="close"></a>  CFileFind::Close  
 Wywołaj tę funkcję elementu członkowskiego, aby zakończyć wyszukiwanie, Resetowanie kontekstu i zwolnić wszystkie zasoby.  
  
```  
void Close();
```  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu **Zamknij**, nie trzeba utworzyć nową `CFileFind` wystąpienia przed wywołaniem [FindFile](#findfile) można rozpocząć nowego wyszukiwania.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::GetFileName](#getfilename).  
  
##  <a name="closecontext"></a>  CFileFind::CloseContext  
 Zamyka określonego przez dojście wyszukiwania bieżącego pliku.  
  
```  
virtual void CloseContext();
```  
  
### <a name="remarks"></a>Uwagi  
 Zamyka plik określony przez bieżącą wartość dojście wyszukiwania. Należy przesłonić tę funkcję, aby zmienić zachowanie domyślne.  
  
 Należy wywołać [FindFile](#findfile) lub [FindNextFile](#findnextfile) funkcje co najmniej raz, można pobrać uchwytu prawidłowe wyszukiwania. `FindFile` i `FindNextFile` funkcji przy użyciu uchwytu wyszukiwania do lokalizowania plików o nazwach odpowiadających podanej nazwie.  
  
##  <a name="findfile"></a>  CFileFind::FindFile  
 Wywołanie tej funkcji elementu członkowskiego, aby otworzyć wyszukiwania plików.  
  
```  
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,  
    DWORD dwUnused = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *pstrName*  
 Wskaźnik do ciągu zawierającego nazwę znajduje się w pliku. W przypadku przekazania **NULL** dla *pstrName*, **FindFile** jest symbol wieloznaczny (*.\*) wyszukiwania.  
  
 *dwUnused*  
 Zarezerwowane dokonanie `FindFile` polimorficznym z klasy pochodnej. Musi być równa 0.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. Aby uzyskać rozszerzone informacje o błędzie, wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu `FindFile` aby rozpocząć wyszukiwanie plików, należy wywołać [FindNextFile](#findnextfile) można pobrać kolejne pliki. Należy wywołać `FindNextFile` co najmniej raz przed wywołaniem metody żadnego z następujących atrybutów funkcji elementów członkowskich:  
  
- [GetCreationTime](#getcreationtime)  
  
- [GetFileName](#getfilename)  
  
- [GetFileTitle](#getfiletitle)  
  
- [GetFilePath](#getfilepath)  
  
- [GetFileURL](#getfileurl)  
  
- [GetLastAccessTime](#getlastaccesstime)  
  
- [GetLastWriteTime](#getlastwritetime)  
  
- [GetLength](#getlength)  
  
- [GetRoot](#getroot)  
  
- [IsArchived](#isarchived)  
  
- [IsCompressed](#iscompressed)  
  
- [IsDirectory](#isdirectory)  
  
- [IsDots](#isdots)  
  
- [IsHidden](#ishidden)  
  
- [Isnormal —](#isnormal)  
  
- [IsReadOnly](#isreadonly)  
  
- [IsSystem](#issystem)  
  
- [IsTemporary](#istemporary)  
  
- [MatchesMask](#matchesmask)  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::IsDirectory](#isdirectory).  
  
##  <a name="findnextfile"></a>  CFileFind::FindNextFile  
 Wywołanie tej funkcji Członkowskich, aby kontynuować wyszukiwanie plików z poprzedniego wywołania [FindFile](#findfile).  
  
```  
virtual BOOL FindNextFile();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ma więcej plików; zero, jeśli znaleziono plik jest ostatnim w katalogu lub wystąpił błąd. Aby uzyskać rozszerzone informacje o błędzie, wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360). Jeśli znaleziono pliku ostatniego pliku w katalogu, lub jeśli pasujących plików można znaleźć `GetLastError` funkcja zwraca ERROR_NO_MORE_FILES.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać `FindNextFile` co najmniej raz przed wywołaniem metody żadnego z następujących atrybutów funkcji elementów członkowskich:  
  
- [GetCreationTime](#getcreationtime)  
  
- [GetFileName](#getfilename)  
  
- [GetFileTitle](#getfiletitle)  
  
- [GetFilePath](#getfilepath)  
  
- [GetFileURL](#getfileurl)  
  
- [GetLastAccessTime](#getlastaccesstime)  
  
- [GetLastWriteTime](#getlastwritetime)  
  
- [GetLength](#getlength)  
  
- [GetRoot](#getroot)  
  
- [IsArchived](#isarchived)  
  
- [IsCompressed](#iscompressed)  
  
- [IsDirectory](#isdirectory)  
  
- [IsDots](#isdots)  
  
- [IsHidden](#ishidden)  
  
- [Isnormal —](#isnormal)  
  
- [IsReadOnly](#isreadonly)  
  
- [IsSystem](#issystem)  
  
- [IsTemporary](#istemporary)  
  
- [MatchesMask](#matchesmask)  
  
 `FindNextFile` opakowuje funkcję Win32 [FindNextFile](http://msdn.microsoft.com/library/windows/desktop/aa364428).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::IsDirectory](#isdirectory).  
  
##  <a name="getcreationtime"></a>  CFileFind::GetCreationTime  
 Wywołanie tej funkcji członkowskich można pobrać czasu utworzenia określonego pliku.  
  
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
 Różna od zera, w przypadku powodzenia; 0 w przypadku niepowodzenia. `GetCreationTime` Zwraca wartość 0, tylko wtedy, gdy [FindNextFile](#findnextfile) nigdy nie została wywołana na tym `CFileFind` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetCreationTime`.  
  
> [!NOTE]
>  Nie wszystkie systemy plików użycie tej samej semantyki do zaimplementowania sygnaturę czasową zwracane przez tę funkcję. Ta funkcja może zwrócić taką samą wartość zwrócona przez inne funkcje sygnatury czasu, jeśli źródłowy system plików lub serwer nie obsługuje atrybutu czas przechowywania. Zobacz [Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktury informacji o formaty czasu. W niektórych systemach operacji zwrócony czas jest w czasie lokalnej strefy do komputera, w której znajduje się plik. Zobacz Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) interfejsu API, aby uzyskać więcej informacji.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::GetLength](#getlength).  
  
##  <a name="getfilename"></a>  CFileFind::GetFileName  
 Wywołanie tej funkcji Członkowskich nazwy znaleziony plik.  
  
```  
virtual CString GetFileName() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa pliku ostatnio znaleziono.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem metody GetFileName.  
  
 `GetFileName` jest jednym z trzech `CFileFind` funkcje Członkowskie, które zwracają pewnej formy nazwy pliku. Na poniższej liście opisano trzy i jak ich w zależności od:  
  
- `GetFileName` Zwraca nazwę pliku z rozszerzeniem. Na przykład wywołanie elementu `GetFileName` do generowania wiadomości użytkownika o pliku `c:\myhtml\myfile.txt` zwraca nazwę `myfile.txt`.  
  
- [GetFilePath](#getfilepath) zwraca pełną ścieżkę pliku. Na przykład wywołanie elementu `GetFilePath` do generowania wiadomości użytkownika o pliku `c:\myhtml\myfile.txt` zwraca ścieżkę pliku `c:\myhtml\myfile.txt`.  
  
- [GetFileTitle](#getfiletitle) zwraca nazwę pliku bez rozszerzenia pliku. Na przykład wywołanie elementu `GetFileTitle` do generowania wiadomości użytkownika o pliku `c:\myhtml\myfile.txt` zwraca nazwy pliku `myfile`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]  
  
##  <a name="getfilepath"></a>  CFileFind::GetFilePath  
 Wywołaj tę funkcję elementu członkowskiego, aby pobrać pełnej ścieżki pliku.  
  
```  
virtual CString GetFilePath() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ścieżka pliku.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetFilePath`.  
  
 `GetFilePath` jest jednym z trzech `CFileFind` funkcje Członkowskie, które zwracają pewnej formy nazwy pliku. Na poniższej liście opisano trzy i jak ich w zależności od:  
  
- [GetFileName](#getfilename) zwraca nazwę pliku z rozszerzeniem. Na przykład wywołanie elementu `GetFileName` do generowania wiadomości użytkownika o pliku `c:\myhtml\myfile.txt` zwraca nazwę `myfile.txt`.  
  
- `GetFilePath` Zwraca pełną ścieżkę pliku. Na przykład wywołanie elementu `GetFilePath` do generowania wiadomości użytkownika o pliku `c:\myhtml\myfile.txt` zwraca ścieżkę pliku `c:\myhtml\myfile.txt`.  
  
- [GetFileTitle](#getfiletitle) zwraca nazwę pliku bez rozszerzenia pliku. Na przykład wywołanie elementu `GetFileTitle` do generowania wiadomości użytkownika o pliku `c:\myhtml\myfile.txt` zwraca nazwy pliku `myfile`.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::GetFileName](#getfilename).  
  
##  <a name="getfiletitle"></a>  CFileFind::GetFileTitle  
 Wywołanie tej funkcji Członkowskich uzyskanie tytuł znaleziony plik.  
  
```  
virtual CString GetFileTitle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa pliku.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetFileTitle`.  
  
 `GetFileTitle` jest jednym z trzech `CFileFind` funkcje Członkowskie, które zwracają pewnej formy nazwy pliku. Na poniższej liście opisano trzy i jak ich w zależności od:  
  
- [GetFileName](#getfilename) zwraca nazwę pliku z rozszerzeniem. Na przykład wywołanie elementu `GetFileName` do generowania wiadomości użytkownika o pliku `c:\myhtml\myfile.txt` zwraca nazwę `myfile.txt`.  
  
- [GetFilePath](#getfilepath) zwraca pełną ścieżkę pliku. Na przykład wywołanie elementu `GetFilePath` do generowania wiadomości użytkownika o pliku `c:\myhtml\myfile.txt` zwraca ścieżkę pliku `c:\myhtml\myfile.txt`.  
  
- `GetFileTitle` Zwraca nazwę pliku bez rozszerzenia pliku. Na przykład wywołanie elementu `GetFileTitle` do generowania wiadomości użytkownika o pliku `c:\myhtml\myfile.txt` zwraca nazwy pliku `myfile`.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::GetFileName](#getfilename).  
  
##  <a name="getfileurl"></a>  CFileFind::GetFileURL  
 Wywołanie tej funkcji Członkowskich do określonego adresu URL pobierania.  
  
```  
virtual CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pełny adres URL.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetFileURL`.  
  
 `GetFileURL` jest podobne do funkcji członkowskiej [GetFilePath](#getfilepath), ale zwraca adres URL w postaci `file://path`. Na przykład wywołanie elementu `GetFileURL` Aby uzyskać pełny adres URL dla `myfile.txt` zwraca adres URL `file://c:\myhtml\myfile.txt`.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::GetFileName](#getfilename).  
  
##  <a name="getlastaccesstime"></a>  CFileFind::GetLastAccessTime  
 Wywołanie tej funkcji Członkowskich uzyskanie godzinę, o której nastąpił ostatni dostęp do określonego pliku.  
  
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
 Różna od zera, w przypadku powodzenia; 0 w przypadku niepowodzenia. `GetLastAccessTime` Zwraca wartość 0, tylko wtedy, gdy [FindNextFile](#findnextfile) nigdy nie została wywołana na tym `CFileFind` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetLastAccessTime`.  
  
> [!NOTE]
>  Nie wszystkie systemy plików użycie tej samej semantyki do zaimplementowania sygnaturę czasową zwracane przez tę funkcję. Ta funkcja może zwrócić taką samą wartość zwrócona przez inne funkcje sygnatury czasu, jeśli źródłowy system plików lub serwer nie obsługuje atrybutu czas przechowywania. Zobacz [Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktury informacji o formaty czasu. W niektórych systemach operacji zwrócony czas jest w czasie lokalnej strefy do komputera, w której znajduje się plik. Zobacz Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) interfejsu API, aby uzyskać więcej informacji.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::GetLength](#getlength).  
  
##  <a name="getlastwritetime"></a>  CFileFind::GetLastWriteTime  
 Wywołanie tej funkcji członkowskich można pobrać czasu, gdy plik został zmieniony.  
  
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
 Różna od zera, w przypadku powodzenia; 0 w przypadku niepowodzenia. `GetLastWriteTime` Zwraca wartość 0, tylko wtedy, gdy [FindNextFile](#findnextfile) nigdy nie została wywołana na tym `CFileFind` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetLastWriteTime`.  
  
> [!NOTE]
>  Nie wszystkie systemy plików użycie tej samej semantyki do zaimplementowania sygnaturę czasową zwracane przez tę funkcję. Ta funkcja może zwrócić taką samą wartość zwrócona przez inne funkcje sygnatury czasu, jeśli źródłowy system plików lub serwer nie obsługuje atrybutu czas przechowywania. Zobacz [Win32_Find_Data](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktury informacji o formaty czasu. W niektórych systemach operacji zwrócony czas jest w czasie lokalnej strefy do komputera, w której znajduje się plik. Zobacz Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) interfejsu API, aby uzyskać więcej informacji.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::GetLength](#getlength).  
  
##  <a name="getlength"></a>  CFileFind::GetLength  
 Wywołaj tę funkcję elementu członkowskiego, aby pobrać długości znaleziony plik, w bajtach.  
  
```  
ULONGLONG GetLength() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość znaleziony plik, w bajtach.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetLength`.  
  
 `GetLength` używa struktury Win32 [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) do pobrania i zwracający wartość rozmiaru pliku w bajtach.  
  
> [!NOTE]
>  Począwszy od MFC 7.0 `GetLength` obsługuje typy 64-bitową liczbę całkowitą. Wcześniej istniejący kod skompilowanej za pomocą tego nowszej wersji biblioteki może spowodować obcięcie ostrzeżenia.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]  
  
##  <a name="getroot"></a>  CFileFind::GetRoot  
 Wywołanie tej funkcji Członkowskich uzyskać katalogu głównego znaleziony plik.  
  
```  
virtual CString GetRoot() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Katalog główny aktywnego wyszukiwania.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `GetRoot`.  
  
 Ta funkcja członkowska zwraca specyfikator dysk i ścieżkę można rozpocząć wyszukiwania. Na przykład wywołanie elementu [FindFile](#findfile) z `*.dat` powoduje `GetRoot` zwraca pusty ciąg. Przekazywanie ścieżki, takie jak `c:\windows\system\*.dll`, do **FindFile** wyniki `GetRoot` zwracanie `c:\windows\system\`.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::GetFileName](#getfilename).  
  
##  <a name="isarchived"></a>  CFileFind::IsArchived  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, jeśli znaleziono plik zostaną zarchiwizowane.  
  
```  
BOOL IsArchived() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aplikacje Oznacz plik archiwum, które ma być kopii zapasowej lub usunięte z FILE_ATTRIBUTE_ARCHIVE, atrybut pliku, określonej w [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktury.  
  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsArchived`.  
  
 Zobacz opis funkcji Członkowskich [MatchesMask](#matchesmask) pełną listę atrybutów pliku.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::GetLength](#getlength).  
  
##  <a name="iscompressed"></a>  CFileFind::IsCompressed  
 Wywołanie tej funkcji Członkowskich, aby ustalić, jeśli znaleziono plik jest skompresowany.  
  
```  
BOOL IsCompressed() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Skompresowany plik jest oznaczony atrybutem FILE_ATTRIBUTE_COMPRESSED, atrybut pliku zidentyfikowany w [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktury. Plik ten atrybut wskazuje wszystkie dane w pliku skompresowane. Dla nazwy katalogu ten atrybut wskazuje, że kompresja jest ustawieniem domyślnym dla nowo utworzone pliki i podkatalogi.  
  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsCompressed`.  
  
 Zobacz opis funkcji Członkowskich [MatchesMask](#matchesmask) pełną listę atrybutów pliku.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::GetLength](#getlength).  
  
##  <a name="isdirectory"></a>  CFileFind::IsDirectory  
 Wywołanie tej funkcji Członkowskich, aby ustalić, jeśli znaleziono plik jest katalogiem.  
  
```  
BOOL IsDirectory() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Plik, który jest katalogiem jest oznaczony atrybutem FILE_ATTRIBUTE_DIRECTORY objęci atrybutu pliku [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktury.  
  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsDirectory`.  
  
 Zobacz opis funkcji Członkowskich [MatchesMask](#matchesmask) pełną listę atrybutów pliku.  
  
### <a name="example"></a>Przykład  
 Ten program małych recurses każdy katalog na dysku C:\ i wyświetla nazwę katalogu.  
  
 [!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]  
  
##  <a name="isdots"></a>  CFileFind::IsDots  
 Wywołanie tej funkcji elementu członkowskiego do testowania dla bieżącego katalogu i nadrzędnej znaczników katalogu podczas iteracji plików.  
  
```  
virtual BOOL IsDots() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli znaleziono plik ma nazwę "."lub"..", co oznacza, że znaleziony plik jest w rzeczywistości katalogiem. W przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsDots`.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::IsDirectory](#isdirectory).  
  
##  <a name="ishidden"></a>  CFileFind::IsHidden  
 Wywołanie tej funkcji Członkowskich, aby ustalić, jeśli znaleziono plik jest ukryty.  
  
```  
BOOL IsHidden() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ukryte pliki, które są oznaczone ikoną z FILE_ATTRIBUTE_HIDDEN, atrybut pliku objęci [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktury. Ukryty plik nie jest uwzględniony na liście zawartości katalogu zwykłej.  
  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsHidden`.  
  
 Zobacz opis funkcji Członkowskich [MatchesMask](#matchesmask) pełną listę atrybutów pliku.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::GetLength](#getlength).  
  
##  <a name="isnormal"></a>  CFileFind::IsNormal  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, jeśli znaleziono plik jest plikiem normalnego.  
  
```  
BOOL IsNormal() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Plików z FILE_ATTRIBUTE_NORMAL, atrybut pliku objęci [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktury. Zwykłego pliku nie ma żadnych innych atrybutów, ustaw. Inne atrybuty pliku zastąpienie tego atrybutu.  
  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsNormal`.  
  
 Zobacz opis funkcji Członkowskich [MatchesMask](#matchesmask) pełną listę atrybutów pliku.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::GetLength](#getlength).  
  
##  <a name="isreadonly"></a>  CFileFind::IsReadOnly  
 Wywołanie tej funkcji Członkowskich, aby ustalić, czy znaleziony plik jest tylko do odczytu.  
  
```  
BOOL IsReadOnly() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Plik tylko do odczytu jest oznaczony atrybutem FILE_ATTRIBUTE_READONLY, atrybut pliku zidentyfikowany w [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktury. Aplikacje mogą odczytywać taki plik, ale nie może zapisywać do niego ani go usunąć.  
  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsReadOnly`.  
  
 Zobacz opis funkcji Członkowskich [MatchesMask](#matchesmask) pełną listę atrybutów pliku.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::GetLength](#getlength).  
  
##  <a name="issystem"></a>  CFileFind::IsSystem  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, jeśli znaleziono plik jest plikiem systemu.  
  
```  
BOOL IsSystem() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Plik systemowy jest oznaczony atrybutem FILE_ATTRIBUTE_SYSTEM, atrybut pliku zidentyfikowany w [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktury. Plik systemowy jest częścią lub jest używany wyłącznie przez system operacyjny.  
  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsSystem`.  
  
 Zobacz opis funkcji Członkowskich [MatchesMask](#matchesmask) pełną listę atrybutów pliku.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::GetLength](#getlength).  
  
##  <a name="istemporary"></a>  CFileFind::IsTemporary  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, jeśli znaleziono plik jest plikiem tymczasowego.  
  
```  
BOOL IsTemporary() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Plik tymczasowy jest oznaczony atrybutem FILE_ATTRIBUTE_TEMPORARY, atrybut pliku zidentyfikowany w [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktury. Plik tymczasowy jest używana do tymczasowego przechowywania danych. Aplikacje należy zapisać w pliku tylko wtedy, gdy jest to bezwzględnie konieczne. Większość plików danych pozostaje w pamięci bez opróżnianych na nośniku, ponieważ plik wkrótce zostanie usunięty.  
  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `IsTemporary`.  
  
 Zobacz opis funkcji Członkowskich [MatchesMask](#matchesmask) pełną listę atrybutów pliku.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CFileFind::GetLength](#getlength).  
  
##  <a name="m_ptm"></a>  CFileFind::m_pTM  
 Wskaźnik do `CAtlTransactionManager` obiektu.  
  
```  
CAtlTransactionManager* m_pTM;  
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="matchesmask"></a>  CFileFind::MatchesMask  
 Wywołanie tej funkcji elementu członkowskiego do testowania atrybutów znaleziony plik.  
  
```  
virtual BOOL MatchesMask(DWORD dwMask) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *dwMask*  
 Określa jeden lub więcej atrybutów plików zidentyfikowany w [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) strukturę, znaleziony plik. Aby wyszukiwać wiele atrybutów, należy użyć wartości bitowe lub (&#124;) operatora. Dopuszczalne jest dowolną kombinację następujących atrybutów:  
  
-   FILE_ATTRIBUTE_ARCHIVE plik jest plikiem archiwum. Aplikacje użyć tego atrybutu, aby oznaczyć pliki kopii zapasowej lub usunięcia.  
  
-   FILE_ATTRIBUTE_COMPRESSED plik lub katalog jest kompresowany. Dla pliku oznacza to, wszystkie dane w pliku skompresowane. Dla nazwy katalogu oznacza to, że kompresja jest ustawieniem domyślnym dla nowo utworzone pliki i podkatalogi.  
  
-   FILE_ATTRIBUTE_DIRECTORY plik jest katalogiem.  
  
-   FILE_ATTRIBUTE_NORMAL pliku nie ma żadnych innych atrybutów, ustaw. Ten atrybut jest prawidłowy tylko wtedy, gdy użyte bez parametrów. Inne atrybuty pliku zastąpienie tego atrybutu.  
  
-   FILE_ATTRIBUTE_HIDDEN plik jest ukryty. Jest nie powinny zostać uwzględnione na liście zawartości katalogu zwykłej.  
  
-   FILE_ATTRIBUTE_READONLY plik jest tylko do odczytu. Aplikacje można odczytać pliku, ale nie może zapisywać do niego lub usuń go.  
  
-   FILE_ATTRIBUTE_SYSTEM plik jest częścią lub jest używany wyłącznie przez system operacyjny.  
  
-   FILE_ATTRIBUTE_TEMPORARY plik jest używany do tymczasowego przechowywania danych. Aplikacje należy zapisać w pliku tylko wtedy, gdy jest to bezwzględnie konieczne. Większość plików danych pozostaje w pamięci bez opróżnianych na nośniku, ponieważ plik wkrótce zostanie usunięty.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. Aby uzyskać rozszerzone informacje o błędzie, wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać [FindNextFile](#findnextfile) co najmniej raz przed wywołaniem `MatchesMask`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#35](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)   
 [Klasa CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)   
 [Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)   
 [Cgopherfile — klasa](../../mfc/reference/cgopherfile-class.md)   
 [Klasa CHttpFile](../../mfc/reference/chttpfile-class.md)
