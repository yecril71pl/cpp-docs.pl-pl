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
ms.openlocfilehash: 5c2814f963ea4814e0d7585e0e4d6dda26c1f04d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321325"
---
# <a name="catltransactionmanager-class"></a>Klasa CAtlTransactionManager

CAtlTransactionManager Klasa zapewnia otokę do funkcji Menedżera transakcji jądra (KTM).

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CAtlTransactionManager;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[~CAtlTransactionManager](#dtor)|CAtlTransactionManager destruktora.|
|[CAtlTransactionManager](#catltransactionmanager)|Konstruktor CAtlTransactionManager.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Zamknij](#close)|Zamyka jeden dojście transakcji.|
|[Zatwierdzenie](#commit)|Żąda, aby transakcja została zatwierdzona.|
|[Utwórz](#create)|Tworzy dojście transakcji.|
|[Createfile](#createfile)|Tworzy lub otwiera plik, strumień plików lub katalog jako operację transakcji.|
|[Deletefile](#deletefile)|Usuwa istniejący plik jako operację przekonowanej.|
|[Plik ZnajdźFirst](#findfirstfile)|Przeszukuje katalog w poszukiwaniu pliku lub podkatalogu jako operacji przekonowanej.|
|[Atrybuty GetFileAttributes](#getfileattributes)|Pobiera atrybuty systemu plików dla określonego pliku lub katalogu jako operację przekonanego.|
|[GetFileAttributesEx](#getfileattributesex)|Pobiera atrybuty systemu plików dla określonego pliku lub katalogu jako operację przekonanego.|
|[Uchwyt GetHandle](#gethandle)|Zwraca dojście transakcji.|
|[Powrót IsFallback](#isfallback)|Określa, czy wywołania rezerwowe są włączone.|
|[Movefile](#movefile)|Przenosi istniejący plik lub katalog, w tym jego łady podrzędne, jako operację przekonanego.|
|[RegCreateKeyEx (RecreateKeyEx)](#regcreatekeyex)|Tworzy określony klucz rejestru i kojarzy go z transakcją. Jeśli klucz już istnieje, funkcja go otwiera.|
|[Klawisz RegDelete](#regdeletekey)|Usuwa podklucz i jego wartości z określonego widoku specyficzne dla platformy rejestru jako operacji przekonowanej.|
|[RegopenKeyEx (ReopenKeyEx)](#regopenkeyex)|Otwiera określony klucz rejestru i kojarzy go z transakcją.|
|[Wycofywania](#rollback)|Żądania, aby transakcja została wycofana.|
|[Atrybuty SetFileAttributes](#setfileattributes)|Ustawia atrybuty pliku lub katalogu jako operację transakcji.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[m_bFallback](#m_bfallback)|PRAWDA, jeśli rezerwowy jest obsługiwany; FAŁSZ inaczej.|
|[m_hTransaction](#m_htransaction)|Dojście transakcji.|

## <a name="remarks"></a>Uwagi

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[ATL::CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltransactionmanager.h

## <a name="catltransactionmanager"></a><a name="dtor"></a>~CAtlTransactionManager

CAtlTransactionManager destruktora.

```
virtual ~CAtlTransactionManager();
```

### <a name="remarks"></a>Uwagi

W normalnym przetwarzaniu transakcja jest automatycznie zatwierdzana i zamykana. Jeśli destruktor jest wywoływany podczas odwijania wyjątku, transakcja jest przywracana i zamykana.

## <a name="catltransactionmanager"></a><a name="catltransactionmanager"></a>CAtlTransactionManager

Konstruktor CAtlTransactionManager.

```
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```

### <a name="parameters"></a>Parametry

*bWłach*<br/>
WARTOŚĆ TRUE wskazuje wsparcie rezerwowe. Jeśli funkcja transakcji nie powiedzie się, klasa automatycznie wywołuje funkcję "bez transakcji". FALSE wskazuje, że nie ma wywołań "rezerwowych".

*bAutoCreateTransakcja*<br/>
PRAWDA wskazuje, że program obsługi transakcji jest tworzony automatycznie w konstruktorze. FALSE wskazuje, że tak nie jest.

### <a name="remarks"></a>Uwagi

## <a name="close"></a><a name="close"></a>Zamknij

Zamyka dojście transakcji.

```
inline BOOL Close();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta otoka `CloseHandle` wywołuje funkcję. Metoda jest automatycznie wywoływana w destruktorze.

## <a name="commit"></a><a name="commit"></a>Zatwierdzanie

Żąda, aby transakcja została zatwierdzona.

```
inline BOOL Commit();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta otoka `CommitTransaction` wywołuje funkcję. Metoda jest automatycznie wywoływana w destruktorze.

## <a name="create"></a><a name="create"></a>Utworzyć

Tworzy dojście transakcji.

```
inline BOOL Create();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta otoka `CreateTransaction` wywołuje funkcję. Sprawdź to pod kątem

## <a name="createfile"></a><a name="createfile"></a>Createfile

Tworzy lub otwiera plik, strumień plików lub katalog jako operację transakcji.

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

*lpFileName*<br/>
Nazwa obiektu, który ma zostać utworzony lub otwarty.

*dwDesiredAccess*<br/>
Dostęp do obiektu, który można podsumować jako odczyt, zapis, oba lub żaden (zero). Najczęściej używane wartości to GENERIC_READ, GENERIC_WRITE lub oba: GENERIC_READ &#124; GENERIC_WRITE.

*dwShareMode (tryb współudziału)*<br/>
Tryb udostępniania obiektu, który może być odczytywany, zapisywany, zarówno, usuwany, wszystkie te lub żaden: 0, FILE_SHARE_DELETE, FILE_SHARE_READ, FILE_SHARE_WRITE.

*lpSecurityAttributes*<br/>
Wskaźnik do struktury SECURITY_ATTRIBUTES, który zawiera opcjonalny deskryptor zabezpieczeń, a także określa, czy zwrócony uchwyt może być dziedziczony przez procesy podrzędne. Parametr może mieć wartość NULL.

*dwCreationDisposition (Wykrywanie tworzenia)*<br/>
Akcja do podjęcia plików, które istnieją i nie istnieją. Ten parametr musi być jedną z następujących wartości, których nie można połączyć: CREATE_ALWAYS, CREATE_NEW, OPEN_ALWAYS, OPEN_EXISTING lub TRUNCATE_EXISTING.

*dwFlagsAndAttributes*<br/>
Atrybuty pliku i flagi. Ten parametr może zawierać dowolną kombinację dostępnych atrybutów plików (FILE_ATTRIBUTE_*). Wszystkie inne atrybuty plików zastępują FILE_ATTRIBUTE_NORMAL. Ten parametr może również zawierać kombinacje flag\*(FILE_FLAG_) do kontroli zachowania buforowania, trybów dostępu i innych flag specjalnego przeznaczenia. Łączą się one z\* dowolnymi wartościami FILE_ATTRIBUTE_.

*hTemplateFile*<br/>
Prawidłowy dojście do pliku szablonu z prawem dostępu GENERIC_READ. Plik szablonu dostarcza atrybuty plików i atrybuty rozszerzone dla tworzonego pliku. Ten parametr może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście, którego można użyć do uzyskania dostępu do obiektu.

### <a name="remarks"></a>Uwagi

Ta otoka `CreateFileTransacted` wywołuje funkcję.

## <a name="deletefile"></a><a name="deletefile"></a>Deletefile

Usuwa istniejący plik jako operację przekonowanej.

```
inline BOOL DeleteFile(LPCTSTR lpFileName);
```

### <a name="parameters"></a>Parametry

*lpFileName*<br/>
Nazwa pliku do usunięcia.

### <a name="remarks"></a>Uwagi

Ta otoka `DeleteFileTransacted` wywołuje funkcję.

## <a name="findfirstfile"></a><a name="findfirstfile"></a>Plik ZnajdźFirst

Przeszukuje katalog w poszukiwaniu pliku lub podkatalogu jako operacji przekonowanej.

```
inline HANDLE FindFirstFile(
    LPCTSTR lpFileName,
    WIN32_FIND_DATA* pNextInfo);
```

### <a name="parameters"></a>Parametry

*lpFileName*<br/>
Katalog lub ścieżka oraz nazwa pliku do wyszukania. Ten parametr może zawierać symbole wieloznaczne, takie jak gwiazdka (*) lub znak zapytania ().

*pNextInfo*<br/>
Wskaźnik do struktury WIN32_FIND_DATA, który odbiera informacje o znalezionym pliku lub podkatalogu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, zwracana wartość jest dojściem wyszukiwania używanym w kolejnym wywołaniu lub `FindNextFile` `FindClose`. Jeśli funkcja nie powiedzie się lub nie może zlokalizować plików z ciągu wyszukiwania w *parametrze lpFileName,* zwracana wartość jest INVALID_HANDLE_VALUE.

### <a name="remarks"></a>Uwagi

Ta otoka `FindFirstFileTransacted` wywołuje funkcję.

## <a name="getfileattributes"></a><a name="getfileattributes"></a>Atrybuty GetFileAttributes

Pobiera atrybuty systemu plików dla określonego pliku lub katalogu jako operację przekonanego.

```
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```

### <a name="parameters"></a>Parametry

*lpFileName*<br/>
Nazwa pliku lub katalogu.

### <a name="remarks"></a>Uwagi

Ta otoka `GetFileAttributesTransacted` wywołuje funkcję.

## <a name="getfileattributesex"></a><a name="getfileattributesex"></a>GetFileAttributesEx

Pobiera atrybuty systemu plików dla określonego pliku lub katalogu jako operację przekonanego.

```
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```

### <a name="parameters"></a>Parametry

*lpFileName*<br/>
Nazwa pliku lub katalogu.

*fInfoLevelId (Nieumieja)*<br/>
Poziom informacji o atrybutach do pobrania.

*lpFileInformacja*<br/>
Wskaźnik do buforu, który odbiera informacje o atrybucie. Typ informacji o atrybutach przechowywanych w tym buforze jest określany przez wartość *fInfoLevelId*. Jeśli *parametrem fInfoLevelId* jest GetFileExInfoStandard, parametr ten wskazuje strukturę WIN32_FILE_ATTRIBUTE_DATA.

### <a name="remarks"></a>Uwagi

Ta otoka `GetFileAttributesTransacted` wywołuje funkcję.

## <a name="gethandle"></a><a name="gethandle"></a>Uchwyt GetHandle

Zwraca dojście transakcji.

```
HANDLE GetHandle() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście transakcji dla klasy. Zwraca wartość `CAtlTransactionManager` NULL, jeśli nie jest dołączony do uchwytu.

### <a name="remarks"></a>Uwagi

## <a name="isfallback"></a><a name="isfallback"></a>Powrót IsFallback

Określa, czy wywołania rezerwowe są włączone.

```
BOOL IsFallback() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca PRAWDA jest klasa obsługuje wywołania rezerwowe. FAŁSZ inaczej.

### <a name="remarks"></a>Uwagi

## <a name="m_bfallback"></a><a name="m_bfallback"></a>m_bFallback

PRAWDA, jeśli rezerwowy jest obsługiwany; FAŁSZ inaczej.

```
BOOL m_bFallback;
```

### <a name="remarks"></a>Uwagi

## <a name="m_htransaction"></a><a name="m_htransaction"></a>m_hTransaction

Dojście transakcji.

```
HANDLE m_hTransaction;
```

### <a name="remarks"></a>Uwagi

## <a name="movefile"></a><a name="movefile"></a>Movefile

Przenosi istniejący plik lub katalog, w tym jego łady podrzędne, jako operację przekonanego.

```
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```

### <a name="parameters"></a>Parametry

*lpOldFileName*<br/>
Bieżąca nazwa istniejącego pliku lub katalogu na komputerze lokalnym.

*lpNewFileName*<br/>
Nowa nazwa pliku lub katalogu. Ta nazwa nie może już istnieć. Nowy plik może znajdować się w innym systemie plików lub na dysku. Nowy katalog musi znajdować się na tym samym dysku.

### <a name="remarks"></a>Uwagi

Ta otoka `MoveFileTransacted` wywołuje funkcję.

## <a name="regcreatekeyex"></a><a name="regcreatekeyex"></a>RegCreateKeyEx (RecreateKeyEx)

Tworzy określony klucz rejestru i kojarzy go z transakcją. Jeśli klucz już istnieje, funkcja go otwiera.

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

*klawiszy*<br/>
Dojście do otwartego klucza rejestru.

*lpSubKey*<br/>
Nazwa podklucza, który ta funkcja otwiera lub tworzy.

*dwReserved (niesłuszne)*<br/>
Ten parametr jest zarezerwowany i musi wynosić zero.

*lpClass (klasa lpclass)*<br/>
Klasa zdefiniowana przez użytkownika tego klucza. Ten parametr może być ignorowany. Ten parametr może mieć wartość NULL.

*Dwoptions*<br/>
Ten parametr może być jedną z następujących wartości: REG_OPTION_BACKUP_RESTORE, REG_OPTION_NON_VOLATILE lub REG_OPTION_VOLATILE.

*samDesired (polski)*<br/>
Maska określająca prawa dostępu dla klucza.

*lpSecurityAttributes*<br/>
Wskaźnik do struktury SECURITY_ATTRIBUTES, która określa, czy zwrócony uchwyt może być dziedziczony przez procesy podrzędne. Jeśli *lpSecurityAttributes* ma wartość NULL, uchwyt nie może być dziedziczony.

*phkResult (wynik)*<br/>
Wskaźnik do zmiennej, która odbiera dojście do klucza otwartego lub utworzonego. Jeśli klucz nie jest jednym ze wstępnie zdefiniowanych `RegCloseKey` kluczy rejestru, należy wywołać funkcję po zakończeniu korzystania z dojścia.

*lpdwDisposition*<br/>
Wskaźnik do zmiennej, która otrzymuje jedną z następujących wartości dyspozycji: REG_CREATED_NEW_KEY lub REG_OPENED_EXISTING_KEY.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli funkcja nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w Winerror.h.

### <a name="remarks"></a>Uwagi

Ta otoka `RegCreateKeyTransacted` wywołuje funkcję.

## <a name="regdeletekey"></a><a name="regdeletekey"></a>Klawisz RegDelete

Usuwa podklucz i jego wartości z określonego widoku specyficzne dla platformy rejestru jako operacji przekonowanej.

```
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*klawiszy*|Dojście do otwartego klucza rejestru.|
|*lpSubKey*|Nazwa klucza do usunięcia.|

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli funkcja nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w Winerror.h.

### <a name="remarks"></a>Uwagi

Ta otoka `RegDeleteKeyTransacted` wywołuje funkcję.

## <a name="regopenkeyex"></a><a name="regopenkeyex"></a>RegopenKeyEx (ReopenKeyEx)

Otwiera określony klucz rejestru i kojarzy go z transakcją.

```
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```

### <a name="parameters"></a>Parametry

*klawiszy*<br/>
Dojście do otwartego klucza rejestru.

*lpSubKey*<br/>
Nazwa podklucza rejestru, który ma zostać otwarty.

*UlOptions*<br/>
Ten parametr jest zarezerwowany i musi wynosić zero.

*samDesired (polski)*<br/>
Maska określająca prawa dostępu dla klucza.

*phkResult (wynik)*<br/>
Wskaźnik do zmiennej, która odbiera dojście do klucza otwartego lub utworzonego. Jeśli klucz nie jest jednym ze wstępnie zdefiniowanych `RegCloseKey` kluczy rejestru, należy wywołać funkcję po zakończeniu korzystania z dojścia.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się, zwracana wartość jest ERROR_SUCCESS. Jeśli funkcja nie powiedzie się, zwracana wartość jest kodem błędu niezerowego zdefiniowanym w Winerror.h

### <a name="remarks"></a>Uwagi

Ta otoka `RegOpenKeyTransacted` wywołuje funkcję.

## <a name="rollback"></a><a name="rollback"></a>Wycofywania

Żądania, aby transakcja została wycofana.

```
inline BOOL Rollback();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta otoka `RollbackTransaction` wywołuje funkcję.

## <a name="setfileattributes"></a><a name="setfileattributes"></a>Atrybuty SetFileAttributes

Ustawia atrybuty pliku lub katalogu jako operację transakcji.

```
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```

### <a name="parameters"></a>Parametry

*lpFileName*<br/>
Nazwa pliku lub katalogu.

*dwAttributes (przyw.*<br/>
Atrybuty pliku do skonfigurowania dla pliku. Aby uzyskać więcej informacji, zobacz [SetFileAttributesTransacted](/windows/win32/api/winbase/nf-winbase-setfileattributestransactedw).

### <a name="remarks"></a>Uwagi

Ta otoka `SetFileAttributesTransacted` wywołuje funkcję.

## <a name="see-also"></a>Zobacz też

[Składniki ATL COM pulpitu](../../atl/atl-com-desktop-components.md)
