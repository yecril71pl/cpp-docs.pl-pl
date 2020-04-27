---
title: Klasa CAtlTransactionManager
ms.date: 11/04/2016
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
helpviewer_keywords:
- CAtlTransactionManager class
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
ms.openlocfilehash: 968582feccd8ba9252ca009699eef6eae2c5c3d6
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167828"
---
# <a name="catltransactionmanager-class"></a>Klasa CAtlTransactionManager

Klasa CAtlTransactionManager dostarcza otokę do funkcji Menedżera transakcji jądra (KTM).

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```cpp
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
|[Zamknij](#close)|Zamyka jeden uchwyt transakcji.|
|[Zatwierdzenie](#commit)|Żąda zatwierdzenia transakcji.|
|[Utwórz](#create)|Tworzy uchwyt transakcji.|
|[CreateFile](#createfile)|Tworzy lub otwiera plik, strumień plików lub katalog w ramach operacji transakcyjnej.|
|[DeleteFile](#deletefile)|Usuwa istniejący plik jako operację transakcji transakcyjnych.|
|[FindFirstFile](#findfirstfile)|Wyszukuje w katalogu plik lub podkatalog jako operację transakcji transakcyjnych.|
|[GetFileAttributes](#getfileattributes)|Pobiera atrybuty systemu plików dla określonego pliku lub katalogu jako operacji transakcyjnej.|
|[Funkcji GetFileAttributesEx](#getfileattributesex)|Pobiera atrybuty systemu plików dla określonego pliku lub katalogu jako operacji transakcyjnej.|
|[GetHandle —](#gethandle)|Zwraca dojście transakcji.|
|[Isfallback](#isfallback)|Określa, czy wywołania rezerwowe są włączone.|
|[MoveFile](#movefile)|Przenosi istniejący plik lub katalog, łącznie z jego elementami podrzędnymi, jako operację transakcyjnej.|
|[RegCreateKeyEx](#regcreatekeyex)|Tworzy określony klucz rejestru i kojarzy go z transakcją. Jeśli klucz już istnieje, funkcja otwiera go.|
|[RegDeleteKey](#regdeletekey)|Usuwa podklucz i jego wartości z określonego, specyficznego dla platformy widoku rejestru jako operacji transakcyjnej.|
|[Działanie funkcji RegOpenKeyEx](#regopenkeyex)|Otwiera określony klucz rejestru i kojarzy go z transakcją.|
|[Wycofywania](#rollback)|Żąda wycofania transakcji.|
|[Setgetfileattributes](#setfileattributes)|Ustawia atrybuty dla pliku lub katalogu jako operacji transakcyjnej.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[m_bFallback](#m_bfallback)|PRAWDA, jeśli rezerwa jest obsługiwana; W przeciwnym razie zwraca wartość FALSE.|
|[m_hTransaction](#m_htransaction)|Dojście transakcji.|

## <a name="remarks"></a>Uwagi

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[ATL:: CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltransactionmanager. h

## <a name="catltransactionmanager"></a><a name="dtor"></a>~ CAtlTransactionManager

Destruktor CAtlTransactionManager.

```cpp
virtual ~CAtlTransactionManager();
```

### <a name="remarks"></a>Uwagi

W przypadku normalnego przetwarzania transakcja jest automatycznie zatwierdzana i zamykana. Jeśli destruktor jest wywoływany podczas operacji unwindy wyjątku, transakcja zostanie wycofana i ZAMKNIĘTA.

## <a name="catltransactionmanager"></a><a name="catltransactionmanager"></a>CAtlTransactionManager

Konstruktor CAtlTransactionManager.

```cpp
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```

### <a name="parameters"></a>Parametry

*bFallback*<br/>
Wartość TRUE oznacza rezerwę na pomoc techniczną. Jeśli działanie transakcyjne nie powiedzie się, Klasa automatycznie wywoła funkcję "nietransakcyjnej". Wartość FALSE oznacza brak wywołań "Fallback".

*bAutoCreateTransaction*<br/>
Wartość TRUE wskazuje, że program obsługi transakcji jest tworzony automatycznie w konstruktorze. Wartość FALSE wskazuje, że nie jest.

### <a name="remarks"></a>Uwagi

## <a name="close"></a><a name="close"></a>Ściśle

Zamyka dojście transakcji.

```cpp
inline BOOL Close();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli powodzenie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta otoka wywołuje `CloseHandle` funkcję. Metoda jest wywoływana automatycznie w destruktorze.

## <a name="commit"></a><a name="commit"></a>Zleca

Żąda zatwierdzenia transakcji.

```cpp
inline BOOL Commit();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli powodzenie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta otoka wywołuje `CommitTransaction` funkcję. Metoda jest wywoływana automatycznie w destruktorze.

## <a name="create"></a><a name="create"></a>Create

Tworzy uchwyt transakcji.

```cpp
inline BOOL Create();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli powodzenie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta otoka wywołuje `CreateTransaction` funkcję. Sprawdź dla

## <a name="createfile"></a><a name="createfile"></a>CreateFile

Tworzy lub otwiera plik, strumień plików lub katalog w ramach operacji transakcyjnej.

```cpp
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

*lpFileName*<br/>
Nazwa obiektu, który ma zostać utworzony lub otwarty.

*dwDesiredAccess*<br/>
Dostęp do obiektu, który może być podsumowywany jako Odczyt, zapis, oba lub nie (zero). Najczęściej używane wartości to GENERIC_READ, GENERIC_WRITE lub oba: GENERIC_READ &#124; GENERIC_WRITE.

*dwShareMode*<br/>
Tryb udostępniania obiektu, który może być odczyt, zapis, oba, Usuń, wszystkie z nich lub brak: 0, FILE_SHARE_DELETE, FILE_SHARE_READ, FILE_SHARE_WRITE.

*lpSecurityAttributes*<br/>
Wskaźnik do struktury SECURITY_ATTRIBUTES, która zawiera opcjonalny deskryptor zabezpieczeń, a także określa, czy zwracany uchwyt może być dziedziczony przez procesy podrzędne. Parametr może mieć wartość NULL.

*dwCreationDisposition*<br/>
Akcja do wykonania na plikach, które istnieją i nie istnieją. Ten parametr musi być jedną z następujących wartości, które nie mogą być połączone: CREATE_ALWAYS, CREATE_NEW, OPEN_ALWAYS, OPEN_EXISTING ani TRUNCATE_EXISTING.

*dwFlagsAndAttributes*<br/>
Atrybuty i flagi pliku. Ten parametr może zawierać dowolną kombinację dostępnych atrybutów pliku (FILE_ATTRIBUTE_ *). Wszystkie inne atrybuty pliku zastępują FILE_ATTRIBUTE_NORMAL. Ten parametr może również zawierać kombinacje flag (FILE_FLAG_\*) do sterowania zachowaniem buforowania, trybami dostępu i innymi flagami specjalnego przeznaczenia. Łączą się z dowolnymi FILE_ATTRIBUTE_\* wartościami.

*hTemplateFile*<br/>
Prawidłowe dojście do pliku szablonu z prawem dostępu GENERIC_READ. Plik szablonu zawiera atrybuty pliku i atrybuty rozszerzone dla tworzonego pliku. Ten parametr może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście, którego można użyć w celu uzyskania dostępu do obiektu.

### <a name="remarks"></a>Uwagi

Ta otoka wywołuje `CreateFileTransacted` funkcję.

## <a name="deletefile"></a><a name="deletefile"></a>DeleteFile

Usuwa istniejący plik jako operację transakcji transakcyjnych.

```cpp
inline BOOL DeleteFile(LPCTSTR lpFileName);
```

### <a name="parameters"></a>Parametry

*lpFileName*<br/>
Nazwa pliku, który ma zostać usunięty.

### <a name="remarks"></a>Uwagi

Ta otoka wywołuje `DeleteFileTransacted` funkcję.

## <a name="findfirstfile"></a><a name="findfirstfile"></a>FindFirstFile

Wyszukuje w katalogu plik lub podkatalog jako operację transakcji transakcyjnych.

```cpp
inline HANDLE FindFirstFile(
    LPCTSTR lpFileName,
    WIN32_FIND_DATA* pNextInfo);
```

### <a name="parameters"></a>Parametry

*lpFileName*<br/>
Katalog lub ścieżka oraz nazwa pliku do wyszukania. Ten parametr może zawierać symbole wieloznaczne, takie jak gwiazdka (*) lub znak zapytania ().

*pNextInfo*<br/>
Wskaźnik do struktury WIN32_FIND_DATA, która otrzymuje informacje o znalezionym pliku lub podkatalogu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest dojściem wyszukiwania używanym podczas kolejnego wywołania `FindNextFile` do `FindClose`lub. Jeśli funkcja nie powiedzie się lub nie można zlokalizować plików z ciągu wyszukiwania w parametrze *lpFileName* , zwracana wartość jest INVALID_HANDLE_VALUE.

### <a name="remarks"></a>Uwagi

Ta otoka wywołuje `FindFirstFileTransacted` funkcję.

## <a name="getfileattributes"></a><a name="getfileattributes"></a>GetFileAttributes

Pobiera atrybuty systemu plików dla określonego pliku lub katalogu jako operacji transakcyjnej.

```cpp
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```

### <a name="parameters"></a>Parametry

*lpFileName*<br/>
Nazwa pliku lub katalogu.

### <a name="remarks"></a>Uwagi

Ta otoka wywołuje `GetFileAttributesTransacted` funkcję.

## <a name="getfileattributesex"></a><a name="getfileattributesex"></a>Funkcji GetFileAttributesEx

Pobiera atrybuty systemu plików dla określonego pliku lub katalogu jako operacji transakcyjnej.

```cpp
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```

### <a name="parameters"></a>Parametry

*lpFileName*<br/>
Nazwa pliku lub katalogu.

*fInfoLevelId*<br/>
Poziom informacji o atrybucie do pobrania.

*lpFileInformation*<br/>
Wskaźnik do buforu, który odbiera informacje o atrybutach. Typ informacji o atrybutach przechowywanych w tym buforze jest określany na podstawie wartości *fInfoLevelId*. Jeśli parametr *fInfoLevelId* jest GetFileExInfoStandard, ten parametr wskazuje na strukturę WIN32_FILE_ATTRIBUTE_DATA.

### <a name="remarks"></a>Uwagi

Ta otoka wywołuje `GetFileAttributesTransacted` funkcję.

## <a name="gethandle"></a><a name="gethandle"></a>GetHandle —

Zwraca dojście transakcji.

```cpp
HANDLE GetHandle() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście transakcji dla klasy. Zwraca wartość NULL, `CAtlTransactionManager` Jeśli nie jest dołączony do dojścia.

### <a name="remarks"></a>Uwagi

## <a name="isfallback"></a><a name="isfallback"></a>Isfallback

Określa, czy wywołania rezerwowe są włączone.

```cpp
BOOL IsFallback() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, ponieważ Klasa obsługuje wywołania rezerwowe. W przeciwnym razie zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

## <a name="m_bfallback"></a><a name="m_bfallback"></a>m_bFallback

PRAWDA, jeśli rezerwa jest obsługiwana; W przeciwnym razie zwraca wartość FALSE.

```cpp
BOOL m_bFallback;
```

### <a name="remarks"></a>Uwagi

## <a name="m_htransaction"></a><a name="m_htransaction"></a>m_hTransaction

Dojście transakcji.

```cpp
HANDLE m_hTransaction;
```

### <a name="remarks"></a>Uwagi

## <a name="movefile"></a><a name="movefile"></a>MoveFile

Przenosi istniejący plik lub katalog, łącznie z jego elementami podrzędnymi, jako operację transakcyjnej.

```cpp
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```

### <a name="parameters"></a>Parametry

*lpOldFileName*<br/>
Bieżąca nazwa istniejącego pliku lub katalogu na komputerze lokalnym.

*lpNewFileName*<br/>
Nowa nazwa pliku lub katalogu. Ta nazwa nie może już istnieć. Nowy plik może znajdować się w innym systemie plików lub dysku. Nowy katalog musi znajdować się na tym samym dysku.

### <a name="remarks"></a>Uwagi

Ta otoka wywołuje `MoveFileTransacted` funkcję.

## <a name="regcreatekeyex"></a><a name="regcreatekeyex"></a>RegCreateKeyEx

Tworzy określony klucz rejestru i kojarzy go z transakcją. Jeśli klucz już istnieje, funkcja otwiera go.

```cpp
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

*hKey*<br/>
Uchwyt do otwartego klucza rejestru.

*lpSubKey*<br/>
Nazwa podklucza, który zostanie otwarty lub utworzony przez tę funkcję.

*dwReserved*<br/>
Ten parametr jest zarezerwowany i musi mieć wartość zero.

*lpClass*<br/>
Zdefiniowana przez użytkownika Klasa tego klucza. Ten parametr może zostać zignorowany. Ten parametr może mieć wartość NULL.

*dwOptions*<br/>
Ten parametr może mieć jedną z następujących wartości: REG_OPTION_BACKUP_RESTORE, REG_OPTION_NON_VOLATILE lub REG_OPTION_VOLATILE.

*samDesired*<br/>
Maska, która określa prawa dostępu dla klucza.

*lpSecurityAttributes*<br/>
Wskaźnik do struktury SECURITY_ATTRIBUTES, która określa, czy zwracany uchwyt może być dziedziczony przez procesy podrzędne. Jeśli *lpSecurityAttributes* ma wartość null, uchwyt nie może być dziedziczony.

*phkResult*<br/>
Wskaźnik do zmiennej, która otrzymuje dojście do otwartego lub utworzonego klucza. Jeśli klucz nie jest jednym ze wstępnie zdefiniowanych kluczy rejestru, wywołaj `RegCloseKey` funkcję po zakończeniu korzystania z dojścia.

*lpdwDisposition*<br/>
Wskaźnik do zmiennej, która otrzymuje jedną z następujących wartości dyspozycji: REG_CREATED_NEW_KEY lub REG_OPENED_EXISTING_KEY.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest ERROR_SUCCESS. Jeśli funkcja się nie powiedzie, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w Winerror. h.

### <a name="remarks"></a>Uwagi

Ta otoka wywołuje `RegCreateKeyTransacted` funkcję.

## <a name="regdeletekey"></a><a name="regdeletekey"></a>RegDeleteKey

Usuwa podklucz i jego wartości z określonego, specyficznego dla platformy widoku rejestru jako operacji transakcyjnej.

```cpp
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*hKey*|Uchwyt do otwartego klucza rejestru.|
|*lpSubKey*|Nazwa klucza, który ma zostać usunięty.|

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest ERROR_SUCCESS. Jeśli funkcja się nie powiedzie, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w Winerror. h.

### <a name="remarks"></a>Uwagi

Ta otoka wywołuje `RegDeleteKeyTransacted` funkcję.

## <a name="regopenkeyex"></a><a name="regopenkeyex"></a>Działanie funkcji RegOpenKeyEx

Otwiera określony klucz rejestru i kojarzy go z transakcją.

```cpp
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```

### <a name="parameters"></a>Parametry

*hKey*<br/>
Uchwyt do otwartego klucza rejestru.

*lpSubKey*<br/>
Nazwa podklucza rejestru, który ma zostać otwarty.

*ulOptions*<br/>
Ten parametr jest zarezerwowany i musi mieć wartość zero.

*samDesired*<br/>
Maska, która określa prawa dostępu dla klucza.

*phkResult*<br/>
Wskaźnik do zmiennej, która otrzymuje dojście do otwartego lub utworzonego klucza. Jeśli klucz nie jest jednym ze wstępnie zdefiniowanych kluczy rejestru, wywołaj `RegCloseKey` funkcję po zakończeniu korzystania z dojścia.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, wartość zwracana jest ERROR_SUCCESS. Jeśli funkcja się nie powiedzie, wartość zwracana jest niezerowym kodem błędu zdefiniowanym w Winerror. h

### <a name="remarks"></a>Uwagi

Ta otoka wywołuje `RegOpenKeyTransacted` funkcję.

## <a name="rollback"></a><a name="rollback"></a>Wycofywania

Żąda wycofania transakcji.

```cpp
inline BOOL Rollback();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli powodzenie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta otoka wywołuje `RollbackTransaction` funkcję.

## <a name="setfileattributes"></a><a name="setfileattributes"></a>Setgetfileattributes

Ustawia atrybuty dla pliku lub katalogu jako operacji transakcyjnej.

```cpp
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```

### <a name="parameters"></a>Parametry

*lpFileName*<br/>
Nazwa pliku lub katalogu.

*dwAttributes*<br/>
Atrybuty pliku do ustawienia dla pliku. Aby uzyskać więcej informacji, zobacz [SetFileAttributesTransacted](/windows/win32/api/winbase/nf-winbase-setfileattributestransactedw).

### <a name="remarks"></a>Uwagi

Ta otoka wywołuje `SetFileAttributesTransacted` funkcję.

## <a name="see-also"></a>Zobacz także

[Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)
