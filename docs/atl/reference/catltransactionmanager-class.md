---
title: Klasa CAtlTransactionManager | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::Close
- ATLTRANSACTIONMANAGER/ATL::Commit
- ATLTRANSACTIONMANAGER/ATL::Create
- ATLTRANSACTIONMANAGER/ATL::CreateFile
- ATLTRANSACTIONMANAGER/ATL::DeleteFile
- ATLTRANSACTIONMANAGER/ATL::FindFirstFile
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributesEx
- ATLTRANSACTIONMANAGER/ATL::GetHandle
- ATLTRANSACTIONMANAGER/ATL::IsFallback
- ATLTRANSACTIONMANAGER/ATL::MoveFile
- ATLTRANSACTIONMANAGER/ATL::RegCreateKeyEx
- ATLTRANSACTIONMANAGER/ATL::RegDeleteKey
- ATLTRANSACTIONMANAGER/ATL::RegOpenKeyEx
- ATLTRANSACTIONMANAGER/ATL::Rollback
- ATLTRANSACTIONMANAGER/ATL::SetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::m_bFallback
- ATLTRANSACTIONMANAGER/ATL::m_hTransaction
dev_langs:
- C++
helpviewer_keywords:
- CAtlTransactionManager class
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3776f95db1a1e6fad8f885e23bb0dc8836a31ff
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681661"
---
# <a name="catltransactionmanager-class"></a>Klasa CAtlTransactionManager
Klasa CAtlTransactionManager zapewnia otoki dla funkcji Menedżera transakcji jądra (KTM).  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CAtlTransactionManager;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[~ CAtlTransactionManager](#dtor)|CAtlTransactionManager destruktora.|  
|[CAtlTransactionManager](#catltransactionmanager)|Konstruktor CAtlTransactionManager.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Zamknij](#close)|Zamyka jeden dojście transakcji.|  
|[Zatwierdzenia](#commit)|Żądania można zatwierdzić transakcji.|  
|[Utwórz](#create)|Tworzy dojście transakcji.|  
|[CreateFile](#createfile)|Tworzy i otwiera plik, strumienia pliku lub katalogu jako operacji transakcyjnych.|  
|[DeleteFile —](#deletefile)|Usuwa istniejący plik jako operacja transakcyjne.|  
|[FindFirstFile](#findfirstfile)|Przeszukuje katalog dla pliku lub podkatalog operacji transakcyjnych.|  
|[GetFileAttributes](#getfileattributes)|Pobiera atrybuty systemu plików dla określonego pliku lub katalogu jako operacja transakcyjne.|  
|[Funkcji GetFileAttributesEx](#getfileattributesex)|Pobiera atrybuty systemu plików dla określonego pliku lub katalogu jako operacja transakcyjne.|  
|[Gethandle —](#gethandle)|Zwraca uchwyt transakcji.|  
|[IsFallback](#isfallback)|Określa, czy rezerwowy wywołania są włączone.|  
|[MoveFile](#movefile)|Przenosi istniejący plik lub katalog, łącznie z jej funkcji podrzędnych operacji transakcyjnych.|  
|[RegCreateKeyEx](#regcreatekeyex)|Tworzy określonego klucza rejestru i kojarzy ją z transakcją. Jeśli klucz już istnieje, funkcja otwiera go.|  
|[RegDeleteKey](#regdeletekey)|Usuwa podklucz, a jego wartości z określonego widoku specyficzne dla platformy rejestru operacji transakcyjnych.|  
|[Działanie funkcji RegOpenKeyEx](#regopenkeyex)|Otwiera wskazanego klucza rejestru i kojarzy ją z transakcją.|  
|[Wycofywanie](#rollback)|Żądania, które transakcji można wycofać.|  
|[SetFileAttributes](#setfileattributes)|Ustawia atrybuty dla pliku lub katalogu jako operacji transakcyjnych.|  
  
### <a name="protected-data-members"></a>Chronione elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[m_bFallback](#m_bfallback)|Wartość TRUE, jeśli rezerwową jest obsługiwana; Wartość FALSE w przeciwnym razie.|  
|[m_hTransaction](#m_htransaction)|Dojście transakcji.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [ATL::CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atltransactionmanager.h  
  
##  <a name="dtor"></a>  ~ CAtlTransactionManager  
 CAtlTransactionManager destruktora.  
  
```
virtual ~CAtlTransactionManager();
```  
  
### <a name="remarks"></a>Uwagi  
 Podczas normalnego przetwarzania transakcji jest automatycznie zatwierdzone i zamknięte. Jeśli destruktor jest wywoływane podczas odwijania wyjątek, transakcja jest wycofana i zamknięte.  
  
##  <a name="catltransactionmanager"></a>  CAtlTransactionManager  
 Konstruktor CAtlTransactionManager.  
  
```
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bFallback*  
 Wartość TRUE wskazuje rezerwowe pomocy technicznej. W przypadku niepowodzenia funkcja transakcyjne klasy automatycznie wywołuje funkcję "nietransakcyjnej". Wartość FALSE wskazuje nie wywołania "rezerwową".  
  
 *bAutoCreateTransaction*  
 Wartość TRUE wskazuje, że program obsługi transakcji jest tworzone automatycznie w konstruktorze. Wartość FALSE wskazuje, że nie jest.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="close"></a>  Zamknij  
 Zamyka uchwyt transakcji.  
  
```
inline BOOL Close();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli to się powiedzie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `CloseHandle` funkcji. Metoda jest wywoływana automatycznie w destruktorze.  
  
##  <a name="commit"></a>  Zatwierdzenia  
 Żądania można zatwierdzić transakcji.  
  
```
inline BOOL Commit();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli to się powiedzie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `CommitTransaction` funkcji. Metoda jest wywoływana automatycznie w destruktorze.  
  
##  <a name="create"></a>  Utwórz  
 Tworzy dojście transakcji.  
  
```
inline BOOL Create();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli to się powiedzie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `CreateTransaction` funkcji. Sprawdź je  
  
##  <a name="createfile"></a>  CreateFile  
 Tworzy i otwiera plik, strumienia pliku lub katalogu jako operacji transakcyjnych.  
  
```
inline HANDLE CreateFile(
  LPCTSTR lpFileName,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes,
    HANDLE hTemplateFile);
```  
  
### <a name="parameters"></a>Parametry  
 *lpFileName*  
 Nazwa obiektu do utworzenia lub otwarcia.  
  
 *dwDesiredAccess*  
 Dostęp do obiektu, który można podsumować w jak Odczyt, zapis, zarówno lub żadna (zero). Najczęściej używane wartości są GENERIC_READ i/lub GENERIC_WRITE: GENERIC_READ &#124; GENERIC_WRITE.  
  
 *dwShareMode*  
 Tryb współdzielenia obiekt, który może być Odczyt, zapis, zarówno, Usuń wszystkie te lub Brak: 0, FILE_SHARE_DELETE, flag FILE_SHARE_READ, FILE_SHARE_WRITE.  
  
 *lpSecurityAttributes*  
 Wskaźnik do struktury SECURITY_ATTRIBUTES, który zawiera deskryptor zabezpieczeń opcjonalny i określa, czy zwracany uchwyt może być dziedziczony przez procesy podrzędne. Parametr może mieć wartości NULL.  
  
 *dwCreationDisposition*  
 Akcja do wykonania na pliki, które istnieją i nie istnieją. Ten parametr musi mieć jedną z następujących wartości, które nie mogą być łączone: CREATE_ALWAYS, CREATE_NEW, OPEN_ALWAYS, OPEN_EXISTING lub TRUNCATE_EXISTING.  
  
 *dwFlagsAndAttributes*  
 Atrybuty pliku i flagi. Ten parametr może zawierać dowolną kombinację atrybutów plików (FILE_ATTRIBUTE_ *). Wszystkie inne atrybuty pliku musi zostać zastąpiona FILE_ATTRIBUTE_NORMAL. Ten parametr może również zawierać kombinacji flag (FILE_FLAG_\*) do kontroli zachowania buforowania, uzyskać dostęp do trybów i inne flagi specjalnego przeznaczenia. Ich połączenie z dowolnym FILE_ATTRIBUTE_\* wartości.  
  
 *hTemplateFile*  
 Prawidłowe dojście do pliku szablonu z prawo dostępu GENERIC_READ. Plik szablonu zawiera atrybuty pliku i atrybuty rozszerzone dla pliku, który jest tworzony. Ten parametr może mieć wartości NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca uchwyt, który może służyć do dostępu do obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `CreateFileTransacted` funkcji.  
  
##  <a name="deletefile"></a>  DeleteFile —  
 Usuwa istniejący plik jako operacja transakcyjne.  
  
```
inline BOOL DeleteFile(LPCTSTR lpFileName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpFileName*  
 Nazwa pliku do usunięcia.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `DeleteFileTransacted` funkcji.  
  
##  <a name="findfirstfile"></a>  FindFirstFile  
 Przeszukuje katalog dla pliku lub podkatalog operacji transakcyjnych.  
  
```
inline HANDLE FindFirstFile(
  LPCTSTR lpFileName,
  WIN32_FIND_DATA* pNextInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *lpFileName*  
 Katalog lub ścieżka i nazwa pliku do wyszukania. Ten parametr może zawierać symboli wieloznacznych, takich jak znak gwiazdki (*) lub znak zapytania ().  
  
 *pNextInfo*  
 Wskaźnik do struktury WIN32_FIND_DATA, która otrzymuje informacje o znaleziony plik lub podkatalog.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja się powiedzie, wartość zwracana jest uchwytem wyszukiwania używane w następnym wywołaniu do metody `FindNextFile` lub `FindClose`. Jeśli funkcja kończy się niepowodzeniem lub nie powiedzie się zlokalizować pliki z ciągu wyszukiwania w *lpFileName* parametr, wartość zwracana jest INVALID_HANDLE_VALUE.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `FindFirstFileTransacted` funkcji.  
  
##  <a name="getfileattributes"></a>  GetFileAttributes  
 Pobiera atrybuty systemu plików dla określonego pliku lub katalogu jako operacja transakcyjne.  
  
```
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpFileName*  
 Nazwa pliku lub katalogu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `GetFileAttributesTransacted` funkcji.  
  
##  <a name="getfileattributesex"></a>  Funkcji GetFileAttributesEx  
 Pobiera atrybuty systemu plików dla określonego pliku lub katalogu jako operacja transakcyjne.  
  
```
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```  
  
### <a name="parameters"></a>Parametry  
 *lpFileName*  
 Nazwa pliku lub katalogu.  
  
 *fInfoLevelId*  
 Poziom informacji o atrybutach do pobrania.  
  
 *lpFileInformation*  
 Wskaźnik do buforu, który otrzymuje informacje o atrybutach. Typ danych atrybutu znajduje się do tego buforu jest określana przez wartość *fInfoLevelId*. Jeśli *fInfoLevelId* parametr jest GetFileExInfoStandard, a następnie ten parametr wskazuje na strukturę WIN32_FILE_ATTRIBUTE_DATA.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `GetFileAttributesTransacted` funkcji.  
  
##  <a name="gethandle"></a>  Gethandle —  
 Zwraca uchwyt transakcji.  
  
```
HANDLE GetHandle() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca uchwyt transakcji dla klasy. Zwraca wartość NULL, jeśli `CAtlTransactionManager` nie jest dołączony do uchwytu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isfallback"></a>  IsFallback  
 Określa, czy rezerwowy wywołania są włączone.  
  
```
BOOL IsFallback() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość TRUE, to wywołania rezerwowego obsługuje klasy. Wartość FALSE w przeciwnym razie.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_bfallback"></a>  m_bFallback  
 Wartość TRUE, jeśli rezerwową jest obsługiwana; Wartość FALSE w przeciwnym razie.  
  
```
BOOL m_bFallback;
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_htransaction"></a>  m_hTransaction  
 Dojście transakcji.  
  
```
HANDLE m_hTransaction;
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="movefile"></a>  MoveFile  
 Przenosi istniejący plik lub katalog, łącznie z jej funkcji podrzędnych operacji transakcyjnych.  
  
```
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpOldFileName*  
 Bieżąca nazwa istniejącego pliku lub katalogu na komputerze lokalnym.  
  
 *lpNewFileName*  
 Nowa nazwa pliku lub katalogu. Ta nazwa nie musi już istnieć. Nowy plik może być na dysku lub innego systemu plików. Nowy katalog musi być na tym samym dysku.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `MoveFileTransacted` funkcji.  
  
##  <a name="regcreatekeyex"></a>  RegCreateKeyEx  
 Tworzy określonego klucza rejestru i kojarzy ją z transakcją. Jeśli klucz już istnieje, funkcja otwiera go.  
  
```
inline LSTATUS RegCreateKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD dwReserved,
    LPTSTR lpClass,
    DWORD dwOptions,
    REGSAM samDesired,
    CONST LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    PHKEY phkResult,
    LPDWORD lpdwDisposition);
```  
  
### <a name="parameters"></a>Parametry  
 *hKey*  
 Dojście można otworzyć klucza rejestru.  
  
 *lpSubKey*  
 Nazwa podklucza, ta funkcja zostanie otwarty lub utworzy.  
  
 *dwReserved*  
 Ten parametr jest zarezerwowana i musi mieć wartość zero.  
  
 *lpClass*  
 Klasa zdefiniowanych przez użytkownika tego klucza. Ten parametr może być ignorowany. Ten parametr może mieć wartości NULL.  
  
 *dwOptions*  
 Ten parametr może być jedną z następujących wartości: REG_OPTION_BACKUP_RESTORE, REG_OPTION_NON_VOLATILE lub REG_OPTION_VOLATILE.  
  
 *samDesired*  
 Maska, który określa prawa dostępu do klucza.  
  
 *lpSecurityAttributes*  
 Wskaźnik do struktury SECURITY_ATTRIBUTES, która określa, czy zwracany uchwyt może być dziedziczony przez procesy podrzędne. Jeśli *lpSecurityAttributes* ma wartość NULL, uchwyt nie może być dziedziczona.  
  
 *phkResult*  
 Wskaźnik do zmiennej, która odbiera dojścia do klucza otwarte lub utworzone. Jeśli klucz nie jest jeden z kluczy rejestru wstępnie zdefiniowane, wywołanie `RegCloseKey` działać po zakończeniu za pomocą uchwytu.  
  
 *lpdwDisposition*  
 Wskaźnik do zmiennej, która otrzyma jeden z następujących wartości Dyspozycja: REG_CREATED_NEW_KEY lub REG_OPENED_EXISTING_KEY.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja się powiedzie, wartością zwracaną jest ERROR_SUCCESS. Jeśli funkcja zawiedzie, wartość zwracana jest kod błędu różny od zera określonych w pliku Winerror.h.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `RegCreateKeyTransacted` funkcji.  
  
##  <a name="regdeletekey"></a>  RegDeleteKey  
 Usuwa podklucz, a jego wartości z określonego widoku specyficzne dla platformy rejestru operacji transakcyjnych.  
  
```
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*hKey*|Dojście można otworzyć klucza rejestru.|  
|*lpSubKey*|Nazwa klucza do usunięcia.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja się powiedzie, wartością zwracaną jest ERROR_SUCCESS. Jeśli funkcja zawiedzie, wartość zwracana jest kod błędu różny od zera określonych w pliku Winerror.h.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `RegDeleteKeyTransacted` funkcji.  
  
##  <a name="regopenkeyex"></a>  Działanie funkcji RegOpenKeyEx  
 Otwiera wskazanego klucza rejestru i kojarzy ją z transakcją.  
  
```
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```  
  
### <a name="parameters"></a>Parametry  
 *hKey*  
 Dojście można otworzyć klucza rejestru.  
  
 *lpSubKey*  
 Nazwa podklucza rejestru, który ma zostać otwarty.  
  
 *ulOptions*  
 Ten parametr jest zarezerwowana i musi mieć wartość zero.  
  
 *samDesired*  
 Maska, który określa prawa dostępu do klucza.  
  
 *phkResult*  
 Wskaźnik do zmiennej, która odbiera dojścia do klucza otwarte lub utworzone. Jeśli klucz nie jest jeden z kluczy rejestru wstępnie zdefiniowane, wywołanie `RegCloseKey` działać po zakończeniu za pomocą uchwytu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja się powiedzie, wartością zwracaną jest ERROR_SUCCESS. Jeśli funkcja zawiedzie, wartością zwracaną jest kod błędu różny od zera określonych w pliku Winerror.h  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `RegOpenKeyTransacted` funkcji.  
  
##  <a name="rollback"></a>  Wycofywanie  
 Żądania, które transakcji można wycofać.  
  
```
inline BOOL Rollback();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli to się powiedzie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `RollbackTransaction` funkcji.  
  
##  <a name="setfileattributes"></a>  SetFileAttributes  
 Ustawia atrybuty dla pliku lub katalogu jako operacji transakcyjnych.  
  
```
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```  
  
### <a name="parameters"></a>Parametry  
 *lpFileName*  
 Nazwa pliku lub katalogu.  
  
 *dwAttributes*  
 Atrybuty pliku można ustawić dla pliku. Aby uzyskać więcej informacji, zobacz [SetFileAttributesTransacted](/windows/desktop/api/winbase/nf-winbase-setfileattributestransacteda).  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `SetFileAttributesTransacted` funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)
