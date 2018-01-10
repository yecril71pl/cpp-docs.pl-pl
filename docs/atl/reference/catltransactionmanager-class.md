---
title: Klasa CAtlTransactionManager | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords: CAtlTransactionManager class
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0def8aa809cd1ccc115ccc2a09b1ae752316098f
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="catltransactionmanager-class"></a>Klasa CAtlTransactionManager
Klasa CAtlTransactionManager udostępnia otokę dla funkcji Menedżera transakcji jądra (KTM).  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CAtlTransactionManager;
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[~ CAtlTransactionManager](#dtor)|Destruktor CAtlTransactionManager.|  
|[CAtlTransactionManager](#catltransactionmanager)|Konstruktor CAtlTransactionManager.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Zamknij](#close)|Zamyka jedną dojście transakcji.|  
|[Zatwierdź](#commit)|Żądania można zatwierdzić transakcji.|  
|[Utwórz](#create)|Tworzy dojście transakcji.|  
|[CreateFile](#createfile)|Tworzy lub otwiera plik, strumienia pliku lub katalogu jako operacją transakcji.|  
|[DeleteFile](#deletefile)|Usuwa istniejący plik jako operacją transakcji.|  
|[FindFirstFile](#findfirstfile)|Wyszukuje katalog dla pliku lub podkatalogu co transakcyjne operacji.|  
|[GetFileAttributes](#getfileattributes)|Pobiera atrybuty systemu plików dla określonego pliku lub katalogu jako operacją transakcji.|  
|[GetFileAttributesEx](#getfileattributesex)|Pobiera atrybuty systemu plików dla określonego pliku lub katalogu jako operacją transakcji.|  
|[GetHandle](#gethandle)|Zwraca dojście transakcji.|  
|[IsFallback](#isfallback)|Określa, czy rezerwowy wywołania są włączone.|  
|[MoveFile](#movefile)|Przenosi istniejący plik lub katalog, w tym jej funkcji podrzędnych jako operacją transakcji.|  
|[RegCreateKeyEx](#regcreatekeyex)|Tworzy określony klucz rejestru i kojarzy ją z transakcji. Jeśli klucz już istnieje, funkcja go otwiera.|  
|[RegDeleteKey](#regdeletekey)|Usuwa podklucz i jego wartości z rejestru określony widok specyficzne dla platformy jako operacją transakcji.|  
|[RegOpenKeyEx](#regopenkeyex)|Otwiera określony klucz rejestru i kojarzy ją z transakcji.|  
|[Wycofywanie](#rollback)|Żądania, które wycofana transakcji.|  
|[SetFileAttributes](#setfileattributes)|Ustawia wartości atrybutów pliku lub katalogu jako operacją transakcji.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[m_bFallback](#m_bfallback)|`TRUE`Jeśli powrotu jest obsługiwany; `FALSE` inaczej.|  
|[m_hTransaction](#m_htransaction)|Dojście transakcji.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [ATL::CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atltransactionmanager.h  
  
##  <a name="dtor"></a>~ CAtlTransactionManager  
 Destruktor CAtlTransactionManager.  
  
```
virtual ~CAtlTransactionManager();
```  
  
### <a name="remarks"></a>Uwagi  
 Podczas normalnego przetwarzania transakcji jest automatycznie zatwierdzone i zamknięte. Jeśli destruktor jest wywoływana podczas unwind wyjątek, transakcja jest wycofana i zamknąć.  
  
##  <a name="catltransactionmanager"></a>CAtlTransactionManager  
 Konstruktor CAtlTransactionManager.  
  
```
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bFallback`  
 `TRUE`Wskazuje powrotu pomocy technicznej. Jeśli funkcja transakcyjne nie powiedzie się, klasa automatycznie wywołuje funkcję "nietransakcyjnej". `FALSE`Wskazuje nie wywołania "rezerwowej".  
  
 `bAutoCreateTransaction`  
 `TRUE`Wskazuje, że program obsługi transakcji jest tworzone automatycznie w konstruktorze. `FALSE`Wskazuje, że nie jest.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="close"></a>Zamknij  
 Zamyka dojście transakcji.  
  
```
inline BOOL Close();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`w przypadku powodzenia; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `CloseHandle` funkcji. Metoda jest wywoływana automatycznie w destruktor.  
  
##  <a name="commit"></a>Zatwierdź  
 Żądania można zatwierdzić transakcji.  
  
```
inline BOOL Commit();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`w przypadku powodzenia; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `CommitTransaction` funkcji. Metoda jest wywoływana automatycznie w destruktor.  
  
##  <a name="create"></a>Utwórz  
 Tworzy dojście transakcji.  
  
```
inline BOOL Create();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`w przypadku powodzenia; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `CreateTransaction` funkcji. Sprawdź go dla  
  
##  <a name="createfile"></a>CreateFile  
 Tworzy lub otwiera plik, strumienia pliku lub katalogu jako operacją transakcji.  
  
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
 `lpFileName`  
 Nazwa obiektu do utworzenia lub otwarcia.  
  
 `dwDesiredAccess`  
 Dostęp do obiektu, który można podsumować jako odczyt, zapis, zarówno lub żadna (zero). Najczęściej używanymi wartościami są GENERIC_READ i GENERIC_WRITE: GENERIC_READ &#124; GENERIC_WRITE.  
  
 `dwShareMode`  
 Tryb współdzielenia obiektu, który może być Odczyt, zapis, zarówno, Usuń wszystkie te lub Brak: 0, FILE_SHARE_DELETE, flag FILE_SHARE_READ, FILE_SHARE_WRITE.  
  
 `lpSecurityAttributes`  
 Wskaźnik do struktury SECURITY_ATTRIBUTES, który zawiera deskryptora zabezpieczeń opcjonalne, a także określa, czy zwrócone dojście mogą być dziedziczone przez procesy podrzędne. Parametr może być `NULL`.  
  
 `dwCreationDisposition`  
 Akcja do wykonania na plikach, które istnieje i nie istnieją. Ten parametr musi mieć jedną z następujących wartości, które nie mogą być łączone: CREATE_ALWAYS, CREATE_NEW, OPEN_ALWAYS, OPEN_EXISTING lub TRUNCATE_EXISTING.  
  
 `dwFlagsAndAttributes`  
 Atrybuty pliku i flagi. Ten parametr może zawierać dowolną kombinację atrybutów plików o dostępności (FILE_ATTRIBUTE_ *). Inne atrybuty pliku musi zostać zastąpiona FILE_ATTRIBUTE_NORMAL. Ten parametr może również zawierać kombinacji flag (FILE_FLAG_\*) do kontroli zachowania buforowania, dostęp tryby i inne flagi specjalnych. Ich połączenie z dowolnym FILE_ATTRIBUTE_\* wartości.  
  
 `hTemplateFile`  
 Prawidłowe dojście do pliku szablonu z prawo dostępu GENERIC_READ. Plik szablonu zawiera atrybuty pliku i atrybutów rozszerzonych do pliku, który jest tworzony. Ten parametr może być `NULL`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dojście, który może służyć do dostępu do obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `CreateFileTransacted` funkcji.  
  
##  <a name="deletefile"></a>DeleteFile  
 Usuwa istniejący plik jako operacją transakcji.  
  
```
inline BOOL DeleteFile(LPCTSTR lpFileName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFileName`  
 Nazwa pliku, który ma zostać usunięty.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `DeleteFileTransacted` funkcji.  
  
##  <a name="findfirstfile"></a>FindFirstFile  
 Wyszukuje katalog dla pliku lub podkatalogu co transakcyjne operacji.  
  
```
inline HANDLE FindFirstFile(
  LPCTSTR lpFileName,
  WIN32_FIND_DATA* pNextInfo);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFileName`  
 Katalog lub ścieżka i nazwa pliku do wyszukania. Ten parametr może zawierać symbole wieloznaczne, takie jak znak gwiazdki (*) lub znak zapytania ().  
  
 `pNextInfo`  
 Wskaźnik do struktury WIN32_FIND_DATA służącą do odbierania informacji na temat znaleziony plik lub podkatalogu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem, zwracana wartość jest dojścia wyszukiwania używane w wywołaniu kolejnych `FindNextFile` lub `FindClose`. Jeśli funkcja nie powiedzie się lub kończy się niepowodzeniem do lokalizacji plików z ciągu wyszukiwania w `lpFileName` INVALID_HANDLE_VALUE jest zwracana wartość parametru.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `FindFirstFileTransacted` funkcji.  
  
##  <a name="getfileattributes"></a>GetFileAttributes  
 Pobiera atrybuty systemu plików dla określonego pliku lub katalogu jako operacją transakcji.  
  
```
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFileName`  
 Nazwa pliku lub katalogu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `GetFileAttributesTransacted` funkcji.  
  
##  <a name="getfileattributesex"></a>GetFileAttributesEx  
 Pobiera atrybuty systemu plików dla określonego pliku lub katalogu jako operacją transakcji.  
  
```
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFileName`  
 Nazwa pliku lub katalogu.  
  
 `fInfoLevelId`  
 Poziom informacje o atrybutach do pobrania.  
  
 `lpFileInformation`  
 Wskaźnik do buforu, który otrzymuje informacje o atrybutach. Typ danych atrybutu jest przechowywany w buforze ta jest określana przez wartość `fInfoLevelId`. Jeśli `fInfoLevelId` parametr jest GetFileExInfoStandard, a następnie ten parametr wskazuje struktury WIN32_FILE_ATTRIBUTE_DATA.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `GetFileAttributesTransacted` funkcji.  
  
##  <a name="gethandle"></a>GetHandle  
 Zwraca dojście transakcji.  
  
```
HANDLE GetHandle() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dojście transakcji dla klasy. Zwraca `NULL` Jeśli `CAtlTransactionManager` nie jest dołączony do uchwytu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="isfallback"></a>IsFallback  
 Określa, czy rezerwowy wywołania są włączone.  
  
```
BOOL IsFallback() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `TRUE` jest klasa obsługuje wywołania rezerwowego. `FALSE`w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_bfallback"></a>m_bFallback  
 `TRUE`Jeśli powrotu jest obsługiwany; `FALSE` inaczej.  
  
```
BOOL m_bFallback;
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="m_htransaction"></a>m_hTransaction  
 Dojście transakcji.  
  
```
HANDLE m_hTransaction;
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="movefile"></a>MoveFile  
 Przenosi istniejący plik lub katalog, w tym jej funkcji podrzędnych jako operacją transakcji.  
  
```
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpOldFileName`  
 Nazwa bieżącego istniejący plik lub katalog na komputerze lokalnym.  
  
 `lpNewFileName`  
 Nowa nazwa pliku lub katalogu. Ta nazwa nie może już istnieć. Nowy plik może być dla innego systemu plików lub stacji. Nowy katalog musi być na tym samym dysku.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `MoveFileTransacted` funkcji.  
  
##  <a name="regcreatekeyex"></a>RegCreateKeyEx  
 Tworzy określony klucz rejestru i kojarzy ją z transakcji. Jeśli klucz już istnieje, funkcja go otwiera.  
  
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
 `hKey`  
 Dojście można otworzyć klucza rejestru.  
  
 `lpSubKey`  
 Nazwa podklucza tej funkcji zostanie otwarty lub tworzy.  
  
 `dwReserved`  
 Ten parametr jest zarezerwowany i musi być równy zero.  
  
 `lpClass`  
 Klasa użytkownika tego klucza. Można zignorować ten parametr. Ten parametr może mieć wartości NULL.  
  
 `dwOptions`  
 Ten parametr może mieć jedną z następujących wartości: REG_OPTION_BACKUP_RESTORE, REG_OPTION_NON_VOLATILE lub REG_OPTION_VOLATILE.  
  
 `samDesired`  
 Maska, który określa prawa dostępu do klucza.  
  
 `lpSecurityAttributes`  
 Wskaźnik do struktury SECURITY_ATTRIBUTES, która określa, czy zwrócone dojście mogą być dziedziczone przez procesy podrzędne. Jeśli `lpSecurityAttributes` jest `NULL`, dojście nie może być dziedziczona.  
  
 `phkResult`  
 Wskaźnik do zmiennej, która odbiera dojście do klucza otwarty lub utworzony. Jeśli klucz nie jest jednym z kluczy rejestru wstępnie zdefiniowane, wywołanie `RegCloseKey` działać po zakończeniu przy użyciu dojścia.  
  
 `lpdwDisposition`  
 Wskaźnik do zmiennej, która otrzyma jeden z następujących wartości dyspozycji: REG_CREATED_NEW_KEY lub REG_OPENED_EXISTING_KEY.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem, wartość zwracana jest ERROR_SUCCESS. Jeśli funkcja nie powiedzie się, wartość zwracana jest zdefiniowane w pliku Winerror.h kod błędu różną od zera.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `RegCreateKeyTransacted` funkcji.  
  
##  <a name="regdeletekey"></a>RegDeleteKey  
 Usuwa podklucz i jego wartości z rejestru określony widok specyficzne dla platformy jako operacją transakcji.  
  
```
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`hKey`|Dojście można otworzyć klucza rejestru.|  
|`lpSubKey`|Nazwa klucza do usunięcia.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem, wartość zwracana jest ERROR_SUCCESS. Jeśli funkcja nie powiedzie się, wartość zwracana jest zdefiniowane w pliku Winerror.h kod błędu różną od zera.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `RegDeleteKeyTransacted` funkcji.  
  
##  <a name="regopenkeyex"></a>RegOpenKeyEx  
 Otwiera określony klucz rejestru i kojarzy ją z transakcji.  
  
```
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```  
  
### <a name="parameters"></a>Parametry  
 `hKey`  
 Dojście można otworzyć klucza rejestru.  
  
 `lpSubKey`  
 Nazwa podklucza rejestru, aby go otworzyć.  
  
 `ulOptions`  
 Ten parametr jest zarezerwowany i musi być równy zero.  
  
 `samDesired`  
 Maska, który określa prawa dostępu do klucza.  
  
 `phkResult`  
 Wskaźnik do zmiennej, która odbiera dojście do klucza otwarty lub utworzony. Jeśli klucz nie jest jednym z kluczy rejestru wstępnie zdefiniowane, wywołanie `RegCloseKey` działać po zakończeniu przy użyciu dojścia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem, wartość zwracana jest ERROR_SUCCESS. Jeśli funkcja nie powiedzie się, wartość zwracana jest zdefiniowane w pliku Winerror.h kod błędu różną od zera  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `RegOpenKeyTransacted` funkcji.  
  
##  <a name="rollback"></a>Wycofywanie  
 Żądania, które wycofana transakcji.  
  
```
inline BOOL Rollback();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `TRUE`w przypadku powodzenia; w przeciwnym razie `FALSE`.  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `RollbackTransaction` funkcji.  
  
##  <a name="setfileattributes"></a>SetFileAttributes  
 Ustawia wartości atrybutów pliku lub katalogu jako operacją transakcji.  
  
```
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFileName`  
 Nazwa pliku lub katalogu.  
  
 `dwAttributes`  
 Atrybuty plików, które można ustawić dla pliku. Aby uzyskać więcej informacji, zobacz [SetFileAttributesTransacted](http://go.microsoft.com/fwlink/p/?linkid=158699).  
  
### <a name="remarks"></a>Uwagi  
 Wywołuje tę otokę `SetFileAttributesTransacted` funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)
